# 📀 Olist E-Commerce Project — Gold Layer Design

The Gold Layer transforms the cleaned and standardized Silver Layer tables into analytics-ready fact and dimension tables. These tables power business dashboards, KPIs, funnel analysis, customer experience insights, and final visualizations.

---

## ⭐ Gold Layer Overview

The Gold Layer contains 7 final analytical tables:

1. **fact_orders**
2. **fact_order_items**
3. **fact_payments**
4. **dim_customers**
5. **dim_sellers**
6. **dim_products**
7. **dim_geolocation**

These tables are created by enriching, merging, and deriving fields from the Silver Layer.

---

## 🟦 1. fact_orders

**Source Tables**
- `silver_orders`
- `silver_reviews`

**Includes**
### Base Order Fields
- order_id  
- customer_id  
- order_status  
- order_purchase_timestamp  
- order_approved_at  
- order_delivered_carrier_date  
- order_delivered_customer_date  
- order_estimated_delivery_date  

### Derived Metrics
- shipping_time_days  
- delivery_time_days  
- total_order_time  
- delivery_delay_days  
- estimated_late_delivery_flag  
- is_canceled  
- is_delivered_without_delivery_date  
- is_shipped_without_carrier_date  

### Review Join
- review_score  
- is_low_rating  
- is_high_rating  

**Purpose**
- Core table for logistics KPIs, SLA insights, CX analysis, funnel metrics.

---

## 🟦 2. fact_order_items

**Source Tables**
- `silver_order_items`
- `silver_products`
- `silver_sellers`

**Includes**
### Base Item Fields
- order_id  
- order_item_id  
- product_id  
- seller_id  
- price  
- freight_value  
- shipping_limit_date  

### Product Enrichment
- product_category_name  
- product_category_name_english  
- product_weight_g  
- product_volume_cm3  

### Seller Enrichment
- seller_city  
- seller_state  

### Derived Fields
- item_revenue = price  
- item_freight_cost = freight_value  

**Purpose**
- Revenue analysis, seller performance, category insights.

---

## 🟦 3. fact_payments

**Source Table**
- `silver_order_payments`

**Includes**
- order_id  
- payment_type  
- payment_installments  
- payment_value  

**Purpose**
- Payment behavior, installment trends, revenue modeling.

---

## 🟦 4. dim_customers

**Source Tables**
- `silver_customers`
- `silver_geolocation`

**Includes**
- customer_id  
- customer_unique_id  
- customer_zip_code_prefix  
- customer_city  
- customer_state  
- geolocation join keys  

**Purpose**
- Customer segmentation, regional revenue analysis.

---

## 🟦 5. dim_sellers

**Source Tables**
- `silver_sellers`
- `silver_geolocation`

**Includes**
- seller_id  
- seller_zip_code_prefix  
- seller_city  
- seller_state  

**Purpose**
- Seller distribution, SLA performance, regional logistics analysis.

---

## 🟦 6. dim_products

**Source Tables**
- `silver_products`
- `silver_category_translation`

**Includes**
- product_id  
- product_category_name  
- product_category_name_english  
- product_weight_g  
- product_length_cm  
- product_height_cm  
- product_width_cm  
- product_volume_cm3  

### Flags
- missing_dimensions_flag  
- imputed_dimensions_flag  

**Purpose**
- Category behavior analysis, weight/volume insights, product mix.

---

## 🟦 7. dim_geolocation

**Source Table**
- `silver_geolocation`

**Includes**
- zip_code_prefix  
- latitude  
- longitude  
- city  
- state  

**Purpose**
- Distance analysis, clustering, regional segmentation.

---

## 🎯 What This Gold Layer Enables

- **Conversion funnel analytics** (from purchase → delivery)
- **Logistics KPIs** (delivery delay, shipping times)
- **Revenue and unit economics**
- **Customer experience modeling**
- **Seller performance benchmarking**
- **Category-level insights**
- **Geo-level segmentation & heatmaps**

---


