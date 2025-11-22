# 📊 Olist E‑Commerce Funnel Analysis — Business Questions

Below is the complete set of industry-relevant, funnel‑focused, analytics‑ready business questions for the Olist Brazilian E‑commerce dataset. These questions will guide my SQL, EDA, visualizations, and final insights.

🛒**Conversion Funnel Analysis**

- What is the overall conversion rate from order placement → payment → delivery?
- At which stage of the funnel do customers drop off the most? (payment pending, cancellations, delays)
- How long does each stage of the order journey take on average?
- Which product categories have the highest and lowest conversion rates?

📦 **Logistics & Delivery Performance**

- What percentage of orders are delivered on time vs delayed?
- Which states/cities experience the highest delivery delays?
- Which sellers or product categories contribute most to delivery delays?
- How do delivery delays affect customer satisfaction (review scores)?
- What is the average actual vs estimated delivery time?

💸 **Payment Behavior & Revenue Insights**

- Which payment methods are most popular?
- Do higher-value orders tend to use more installments?
- What is the distribution of payment installments across customers?
- Which product categories generate the highest total revenue?
- What is the average order value by product category?
- How much revenue is lost due to canceled orders?

🌟 **Customer Experience & Review Analysis**

- What factors contribute most to low review scores (1–2 stars)?
- How do review scores vary by product category?
- Is there a correlation between delivery time and review score?
- What is the distribution of review scores across the platform?
- Which sellers consistently achieve high customer satisfaction?

👥 **Customer Segmentation & Retention**

- Which customer segments have the highest repeat purchase rates?
- What demographic or geographic patterns exist among returning customers?
- Which categories drive repeat orders the most?
- What is the average time between purchases for returning customers?

🔍 **Product Category & Sales Performance**

- Which categories have the highest order volume?
- Which categories show seasonal trends?
- What is the cancellation rate by product category?
- Which products have the highest refund/return risk?

📉 **Loss, Risk & Operational Inefficiencies**

- Estimated financial loss due to late deliveries.
- Estimated financial loss due to canceled orders.
- Are there sellers or regions with unusually high cancellation rates?
- Identify operational bottlenecks in the logistics chain.

📈 **Value‑Add Questions**

- What is the ideal delivery time threshold that maximizes customer satisfaction?
- Which variables best predict a customer giving a 5‑star rating?
- Does offering more installment options improve conversion?
- Which customer segments are most sensitive to delivery delays?

# 🎯 Olist KPI Design Board 

Below are the Core Metrics, Diagnostic Metrics, and Actionable KPIs i have defined.

## ✅ 1. Business Goal (Top-Level)

- Improve customer experience, increase revenue, and reduce operational inefficiencies.

## 🛒 2. Funnel KPIs (Customer Journey)

These KPIs directly answer your conversion-focused questions.
**Core KPIs**
- Orders Placed
- Payments Approved
- Orders Shipped
- Orders Delivered
- Orders Reviewed

**Derived KPIs**
- Conversion Rate (Placed → Delivered)
- Drop-off Rate by Stage
- On-time Delivery Rate
- % Orders with Reviews

## 🚚 3. Logistics & Delivery KPIs
**Core KPIs**
- Average Delivery Time
- Average Delay (Actual – Estimated)
- % Orders Delivered Late
- Avg Shipping Distance (Geo data)

**Derived KPIs**
- Delay by Seller
- Delay by Carrier
- Delay by Region (State/City)
- Delay impact on Review Score

## 💳 4. Payment & Revenue KPIs
**Core KPIs**
- Total Revenue
- Average Order Value (AOV)
- GMV (Gross Merchandise Volume)
- Freight Cost per Order

**Payment-Specific**
- % Orders by Payment Type
- Avg Installments per Order
- Installment-based Revenue Contribution

## 📦 5. Product & Category KPIs
**Core KPIs**
- Revenue by Category
- Order Volume by Category
- Cancellation Rate by Category
- Return/Refund Rate

**Quality**
- Average Review Score by Category
- % Low-rated Products (<=2 stars)

## 👩‍💼 6. Seller Performance KPIs
**Core KPIs**
- Revenue per Seller
- Order Volume per Seller
- Seller On-time Shipping Rate
- Avg Review Score per Seller

**Risk & Compliance**
- % Complaints per Seller
- Return Rate per Seller

## ⭐ 7. Customer Experience KPIs
**Core KPIs**
- Avg Review Score
- Review Distribution (1 to 5 stars)

**Diagnostic**
- Low Review Root Causes (Delay, Price, Damage)
- NPS-like Score (5-star vs 1-star ratio)
- Delivery Delay → Complaints correlation

## 🧭 8. Growth & Repeat Purchase KPIs
- Unique Customers per Month
- Repeat Customer Rate
- Customer Lifetime Value (LTV)

# 📌 KPI Dashboard Sections

The dashboard is be divided into 5 easy pages:
## 1.Executive Summary
- Revenue
- AOV
- On-time delivery %
- Avg review score
- Total orders
## 2.Logistics Dashboard
- Delay heatmap
- Distance vs delay correlation
- Late delivery % by city
## 3.Product Category Dashboard
- Top revenue categories
- Category-level ratings
- High-return products
## 4.Seller Performance Dashboard
- Seller ranking
- On-time shipping rate
- Complaints %
## 5.Customer Experience Dashboard
- Rating distributions
- Root cause of low ratings
- Delay → rating impact
