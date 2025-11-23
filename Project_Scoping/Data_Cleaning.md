# 📌 Olist E-Commerce Project — Data Cleaning Plan

This document outlines the complete cleaning approach for all tables in the Olist Brazilian E-commerce dataset.
It ensures consistent, reliable, analysis-ready data for funnel analytics, logistics KPIs, revenue insights, and customer experience modeling.

## 🔷 1. Data Loading & Structure Validation
✔ Load all CSVs into SQLite database

Validate row & column counts
Verify UTF-8 encoding
Store with consistent naming (snake_case)
Enforce primary key constraints

✔ Confirm schema correctness

Run:
`PRAGMA table_info(table_name);`

Check:
No corrupted types
No missing PK fields
No inconsistent NULL constraints

Tables included:
customers
orders
order_items
order_payments
order_reviews
sellers
geolocation
products
category_translation

## 🔷 2. Primary Key Validation

**Customers**
customer_id → unique
customer_unique_id → NOT unique (expected)
**Orders**
order_id → unique
**Order Items**
Composite key:
(order_id, order_item_id) → unique
**Products**
product_id → unique
**Sellers**
seller_id → unique

Check using:
`SELECT order_id, COUNT(*)
FROM orders
GROUP BY order_id
HAVING COUNT(*) > 1;`

## 🔷 3. Foreign Key Integrity Checks
Expected relationships:
|Child	                    | Parent	                   |  Key        |
|---------------------------|----------------------------|-------------|
| `orders                   | `	customers	               | customer_id | 
| `order_items	            | ` orders	                 | order_id    | 
| `order_items              | `	sellers	                 |  seller_id  | 
| `order_items	            | `products	                 | product_id  | 
| `order_payments	          | `orders	                   | order_id    | 
| `order_reviews	          | `orders	                   | order_id    | 

Detect missing parent rows:

 `SELECT child.order_id
FROM order_items child
LEFT JOIN orders parent ON parent.order_id = child.order_id
WHERE parent.order_id IS NULL; `

## 🔷 4. Timestamp Standardization

Convert the following to DATETIME:

| Column	                      | Table                                |
|-------------------------------|--------------------------------------|
| `order_purchase_timestamp`	     | orders | 
| `order_approved_at`	             | orders | 
| `order_delivered_carrier_date`	 | orders | 
| `order_delivered_customer_date`  | orders | 
| `order_estimated_delivery_date`  | orders | 
| `review_answer_timestamp`	       | reviews | 
| `review_creation_date`	         | reviews | 

Fix timezone inconsistencies (all are UTC-like format).

## 🔷 5. Handling Missing Values

 🟦 Orders Table

| Column                         | Issue                               | Action                     |
|-------------------------------|--------------------------------------|----------------------------|
| `order_approved_at`           | Missing = payment pending            | Keep `NULL`, mark as pending |
| `order_delivered_carrier_date` | Missing = never shipped              | Label as `"not_shipped"`     |
| `order_delivered_customer_date` | Missing = not delivered/cancelled    | Keep `NULL`                 |
| `order_estimated_delivery_date` | Never missing                        | OK                         |

 🟦 Reviews Table

- `review_comment_title`, `review_comment_message` → **NULL allowed**
- **No imputation needed**

 🟦 Products Table

 Missing dimensions:
- `product_height_cm`
- `product_length_cm`
- `product_width_cm`
- `product_weight_g`

 Approach:
- Compute **category-level median**
- Impute missing using SQL:

`sql
UPDATE products 
SET product_weight_g = (SELECT median_weight_by_category);`


## 🔷 6. Outlier Treatment

**Payment Installments**
- Installments range 1–24
- Keep all (Brazilian market norms)

**Freight Values**
Flag extreme values:
`sql 
freight_value > (Q3 + 1.5 * IQR) `
Keep but mark as outliers.

**Delivery Time Outliers**
Customers receiving items before they were shipped:
-Negative delivery times
Fix:
`IF delivered_date < shipped_date → set delivered_date = shipped_date`

## 🔷 7. Derived Fields to Create
🟧 Delivery Delay
- `delivery_delay_days = julianday(order_delivered_customer_date) - julianday(order_estimated_delivery_date)`

🟧 Shipping Time
- `shipping_time_days = julianday(order_delivered_carrier_date) - julianday(order_approved_at)`

🟧 Delivery Time
- `delivery_time_days = julianday(order_delivered_customer_date) - julianday(order_delivered_carrier_date)`

🟧 Actual Order Lifecycle
- `total_order_time = julianday(order_delivered_customer_date) - julianday(order_purchase_timestamp)`

🟧 Cancellation Flag
- `CASE WHEN order_status = 'canceled' THEN 1 ELSE 0 END AS is_canceled`

## 🔷 8. Review Quality & Sentiment Flags

Even if text is missing, keep it — no imputation.
Create flags:
**Low rating**
- `CASE WHEN review_score IN (1,2) THEN 1 END AS is_low_rating`
**High rating**
- `CASE WHEN review_score = 5 THEN 1 END AS is_high_rating`

## 🔷 9. Category Standardization

Table: `product_category_name`

Problem:
Some categories do not match translation file
Many Brazilian categories do not have English translations
Fix:
- Merge using LEFT JOIN
- NULL translation? Keep original
- For analysis: use translated value when available

## 🔷 10. Duplicate Handling

- `customer_id` duplicates should not exist → drop if found
- `customer_unique_id` duplicates → valid; do not remove
- `geolocation` duplicates → keep
- `orders` duplicates → should be zero

## 🔷 11. Data Quality Rules Summary
- ✔ No conversion of numeric → string
- ✔ No arbitrary imputation except product dimensions
- ✔ Missing dates preserved (carry business meaning)
- ✔ Delivery delay computed only when both dates exist
- ✔ Do not remove outliers without tagging
- ✔ Keep raw versions untouched for reproducibility

## 🔷 12. Final Cleaned Output Tables

You will produce:

**1. fact_orders**
- delivery times
- delays
- cancellation flag
- review score merged

**2. fact_order_items**
- item-level revenue
- item-level freight
  
**3. dim_customers**

**4. dim_sellers**

**5. dim_products**

**6. dim_geolocation**

**7. fact_payments**

  ---

# 🎯 This Cleaning Plan Supports Your KPI Tree

- Conversion KPIs → require lifecycle timestamps
- Logistics KPIs → depend on delivery delay calculations
- Revenue KPIs → payment + item tables required
- Customer Experience KPIs → review + delivery delay relationship
- Seller KPIs → merged item + shipping data
