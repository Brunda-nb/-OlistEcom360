# BUSINESS GOAL
Improve customer experience, increase revenue, and reduce operational inefficiencies.

├── 1. CONVERSION & FUNNEL PERFORMANCE
│   ├── 1.1 Funnel Volume Metrics
│   │   ├── Orders Placed
│   │   ├── Payments Approved
│   │   ├── Orders Shipped
│   │   ├── Orders Delivered
│   │   └── Orders Reviewed
│   │
│   ├── 1.2 Funnel Efficiency Metrics
│   │   ├── Conversion Rate (Placed → Delivered)
│   │   ├── Stage-wise Drop-off Rate
│   │   ├── % Cancellations
│   │   └── Time Taken per Stage (Order → Payment → Ship → Delivery)
│   │
│   └── 1.3 Category-wise Funnel Insights
│       ├── Category Conversion Rate
│       ├── Category Drop-off Rate
│       └── Category Funnel Bottlenecks

│
├── 2. LOGISTICS & DELIVERY PERFORMANCE
│     │
│     ├── 2.1 Delivery Speed
│     │     ├── Average Delivery Time
│     │     ├── Actual vs Estimated Delivery Time
│     │     └── Delivery Time by Region/City/Seller
│     │
│     ├── 2.2 Delay Metrics
│     │     ├── % Orders Delivered Late
│     │     ├── Delay by State/City
│     │     ├── Delay by Seller
│     │     └── Delay by Product Category
│     │
│     └── 2.3 Logistics Impact
│           ├── Delay → Review Score Impact
│           ├── Delay → Cancellation Risk
│           └── Estimated Financial Loss from Delays

│
├── 3. PAYMENT & REVENUE PERFORMANCE
│     │
│     ├── 3.1 Revenue Metrics
│     │     ├── Total Revenue
│     │     ├── GMV (Gross Merchandise Volume)
│     │     ├── Average Order Value (AOV)
│     │     └── Revenue by Category / Seller
│     │
│     ├── 3.2 Payment Behavior
│     │     ├── % Orders by Payment Method
│     │     ├── Avg Installments per Order
│     │     ├── Installment-based Conversion Rate
│     │     └── High Order Value → Installments Pattern
│     │
│     └── 3.3 Loss & Leakage
│           ├── Revenue Lost due to Cancellations
│           ├── Loss due to Late Deliveries
│           └── High-risk Sellers/Regions for Loss

│
├── 4. CUSTOMER EXPERIENCE & REVIEW ANALYSIS
│     │
│     ├── 4.1 Review Distribution
│     │     ├── Avg Review Score
│     │     ├── Score Distribution (1–5)
│     │     └── % Low-rated Orders (1–2 stars)
│     │
│     ├── 4.2 Root Causes of Low Reviews
│     │     ├── Delivery Delays
│     │     ├── Product Quality Issues
│     │     ├── Packaging/Damage Complaints
│     │     └── Incorrect Product
│     │
│     └── 4.3 Seller-level Customer Experience
│           ├── Avg Seller Rating
│           ├── Complaints per Seller
│           └── High Satisfaction Sellers

│
├── 5. PRODUCT CATEGORY & SALES PERFORMANCE
│     │
│     ├── 5.1 Category Demand
│     │     ├── Order Volume by Category
│     │     ├── Revenue by Category
│     │     └── Seasonal Trends
│     │
│     ├── 5.2 Category Risk
│     │     ├── Cancellation Rate by Category
│     │     ├── Refund/Return Rate by Category
│     │     └── High-risk Product Types
│     │
│     └── 5.3 Category Satisfaction
│           ├── Avg Review Score by Category
│           └── % Low-rated SKUs per Category

│
├── 6. SELLER PERFORMANCE
│     │
│     ├── 6.1 Seller Contribution
│     │     ├── Revenue per Seller
│     │     ├── Order Volume per Seller
│     │     └── Seller Market Share
│     │
│     ├── 6.2 Seller Operations
│     │     ├── On-time Shipping Rate
│     │     ├── Avg Handling Time
│     │     ├── Seller Delay Impact
│     │     └── Cancellation Rate per Seller
│     │
│     └── 6.3 Seller Quality
│           ├── Avg Review Score per Seller
│           ├── Complaints per Seller
│           └── High Risk Sellers (delays + low score)

│
└── 7. CUSTOMER SEGMENTATION & RETENTION
      │
      ├── 7.1 Customer Segments
      │     ├── Segments by Geography
      │     ├── Segments by Order Frequency
      │     └── Segments by Spending Patterns
      │
      ├── 7.2 Retention & Repeat Purchases
      │     ├── Repeat Purchase Rate
      │     ├── Time Between Purchases
      │     ├── Category-driven Repeat Behavior
      │     └── Region-wise Repeat Rate
      │
      └── 7.3 Customer Lifetime Value (LTV)
            ├── LTV by Segment
            ├── LTV by Category Preference
            └── Churn-prone Customer Groups

# 📊 Olist KPI Tree (Based on Full Business Questions)

A unified KPI Tree mapping each business question → KPI category → diagnostic metrics.  
Use this to structure SQL scripts, EDA sections, dashboard pages, and your final business insights.

---

# 🎯 TOP-LEVEL GOAL  
## **Increase Total Revenue & Customer Satisfaction**  
Supported by: Conversion, Delivery Efficiency, Payment Behavior, Customer Retention, Product Performance.

---

# 🌿 FULL KPI TREE

---

# 1️⃣ Conversion Funnel KPIs  
Track the customer journey from order → payment → delivery.

### **Primary KPIs**
- **Overall Conversion Rate**
- **Stage-wise Conversion**  
  - Order → Payment  
  - Payment → Shipment  
  - Shipment → Delivery

### **Diagnostic Metrics**
- Funnel drop-off rate (payment pending, failed, cancellations)
- Avg time spent at each funnel stage  
  - Order to Payment  
  - Payment to Shipment  
  - Shipment to Delivery
- Conversion rate by product category
- Conversion rate by region
- Cart abandonment indicators (inferred)

---

# 2️⃣ Logistics & Delivery KPIs  
Measure delivery performance, regional issues, and supply chain efficiency.

### **Primary KPIs**
- **On-Time Delivery %**
- **Average Actual vs Estimated Delivery Time**
- **Delivery Delay Rate**
- **Order Delivery SLA Compliance**

### **Diagnostic Metrics**
- Delay rate by:
  - State / City
  - Seller
  - Product category
  - Carrier (if inferred)
- Delivery delay impact on:
  - Review Scores  
  - Cancellations  
  - Refunds
- Hub/warehouse processing time (based on timestamps)

---

# 3️⃣ Payment Behavior & Revenue KPIs  
Focus on payment patterns, profitability and revenue impact.

### **Primary KPIs**
- **Popular Payment Methods Share**
- **Installment Usage %**
- **Average Installment Count**
- **Total Revenue**
- **Net Revenue (after cancellations/returns)**

### **Diagnostic Metrics**
- Installments vs AOV correlation  
- Payment method preferences by state  
- Installment behavior by order value  
- Category-wise revenue  
- Revenue loss due to:
  - Canceled orders  
  - Returned/refunded orders  
- High-value vs low-value customer segments

---

# 4️⃣ Customer Experience & Review KPIs  
Understand quality perception and customer sentiment.

### **Primary KPIs**
- **Average Review Score**
- **5-Star Rating %**
- **1–2 Star Rate**
- **Delivery Time → Review Score Correlation**

### **Diagnostic Metrics**
- Low-score root causes:
  - Delivery delays  
  - Product quality issues (category-level)  
  - Seller behavior  
- Review distribution across:
  - Product categories  
  - Sellers  
  - Regions  
- Seller satisfaction leaderboard

---

# 5️⃣ Customer Segmentation & Retention KPIs  
Track user lifecycle, loyalty, and repeat behavior.

### **Primary KPIs**
- **Repeat Purchase Rate**
- **Customer Retention Rate**
- **Average Time Between Purchases**
- **Customer Lifetime Orders**

### **Diagnostic Metrics**
- Segments by:
  - Geography  
  - Category preference  
  - Payment behavior  
  - Order value tiers  
- Categories driving the most repeat orders  
- High-value vs low-value customer cohorts  
- New vs returning customer ratio

---

# 6️⃣ Product Category & Sales KPIs  
Analyze category-level performance and profitability.

### **Primary KPIs**
- **Order Volume by Category**
- **Revenue by Category**
- **Category Conversion Rate**
- **Category Cancellation Rate**

### **Diagnostic Metrics**
- Seasonal order trends (month/quarter)
- High refund/return categories
- Top sellers and underperforming sellers for each category
- Stock/out-of-stock inference (via lead times)

---

# 7️⃣ Loss, Risk & Operational Inefficiency KPIs  
Identify hidden financial impact and operational failures.

### **Primary KPIs**
- **Loss Due to Late Deliveries (estimated)**
- **Loss Due to Cancellations**
- **Loss Due to Returns/Refunds**
- **Operational Risk Score (composite)**

### **Diagnostic Metrics**
- Sellers with unusually high cancellation rates  
- Regions with consistent delivery bottlenecks  
- Time-to-ship delays  
- Payment failure & pending statuses  
- SLA breach patterns over time

---

# 8️⃣ Value-Added Predictive/Advanced KPIs  
For machine-learning or advanced analytics layers.

### **Primary KPIs**
- **Optimal Delivery Time Threshold** (maximizes 5-star reviews)
- **5-Star Rating Predictive Variables**
- **Installments → Conversion Impact**
- **Segments Most Sensitive to Delivery Delays**

### **Diagnostic Metrics**
- Feature importance for review predictions  
- Delivery sensitivity scores by customer cohort  
- Installment elasticity (conversion uplift from more options)  
- Churn/retention prediction signals

---

# 🧭 How to Use This Tree
- Map each KPI to SQL queries in your EDA notebook.
- Build dashboard tabs for:
  - Funnel  
  - Delivery  
  - Payments  
  - Revenue  
  - Reviews  
  - Categories  
  - Customers  
- Use the tree to structure the **Insights & Recommendations** section 

---
