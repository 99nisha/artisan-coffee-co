# Coffee Business KPI Formulas & Calculations

## 1. Customer Metrics

### Customer Lifetime Value (CLV)
```
CLV = total_lifetime_spend (from customers table)
```
**Example from dataset:**
- David Park: $2,145.80
- Sarah Chen: $1,234.50

### Average Customer Lifetime Value
```
Avg CLV = SUM(total_lifetime_spend) / COUNT(customers)
```
**Calculation:** $7,055.50 / 8 customers = $879.89

### Customer Acquisition Cost (CAC)
```
CAC = SUM(marketing_campaigns.budget) / COUNT(new customers acquired)
```
**From dataset:** $1,075 marketing budget / estimated new customers

### Customer Retention Rate
```
Retention Rate = (Customers who made repeat purchases / Total customers) × 100
```
**Calculation:** (7 repeat customers / 8 total customers) × 100 = 87.5%

### Average Order Value (AOV)
```
AOV = SUM(orders.total_amount) / COUNT(orders)
```
**Calculation:** $112.40 / 8 orders = $14.05 per order

### Purchase Frequency
```
Purchase Frequency = COUNT(orders) / COUNT(unique customers) in time period
```
**From dataset:** 8 orders / 6 unique customers = 1.33 orders per customer per day

### Net Promoter Score (NPS) - Survey Based
```
NPS = % Promoters (9-10) - % Detractors (0-6)
```
*Note: Requires customer survey data not in current dataset*

## 2. Product & Inventory Metrics

### Profit Margin by Product
```
Profit Margin = ((selling_price - unit_cost) / selling_price) × 100
```
**Examples:**
- Ethiopian Coffee: ((18.99 - 7.25) / 18.99) × 100 = 61.9%
- Espresso Blend: ((15.99 - 5.10) / 15.99) × 100 = 68.1%

### Gross Profit Margin
```
Gross Profit Margin = (Revenue - COGS) / Revenue × 100
```
**Where COGS = SUM(order_items.quantity × products.unit_cost)**

### Inventory Turnover Rate
```
Inventory Turnover = COGS / Average Inventory Value
```
**Where Average Inventory Value = (Beginning Inventory + Ending Inventory) / 2**

### Inventory Days on Hand
```
Days on Hand = (Average Inventory Value / COGS) × 365
```

### Waste Percentage
```
Waste % = (waste_amount / total_product_used) × 100
```
**From daily_operations:** 0.5 lbs waste / estimated 50 lbs used = 1%

### Product Mix Analysis
```
Product Mix % = (Product Category Revenue / Total Revenue) × 100
```

## 3. Financial Metrics

### Daily Revenue
```
Daily Revenue = SUM(orders.total_amount) WHERE order_date = specific_date
```
**June 20 example:** $112.40 (from 8 orders)

### Monthly Revenue
```
Monthly Revenue = SUM(orders.total_amount) WHERE MONTH(order_date) = target_month
```

### Revenue per Customer
```
Revenue per Customer = Total Revenue / COUNT(unique customers)
```

### Cost of Goods Sold (COGS)
```
COGS = SUM(order_items.quantity × products.unit_cost)
```
**For each order:**
- Order O001: (1×1.85) + (1×1.20) + (1×1.50) = $4.55
- Order total: $11.99, COGS: $4.55, Gross Profit: $7.44

### Break-Even Point (Units)
```
Break-Even Units = Fixed Costs / (Selling Price per Unit - Variable Cost per Unit)
```

### Break-Even Point (Revenue)
```
Break-Even Revenue = Fixed Costs / Gross Margin %
```

### Cash Flow
```
Cash Flow = Revenue - Total Expenses
```
**Where Total Expenses = SUM(expenses.amount) + Labor Costs**

### Return on Investment (ROI)
```
ROI = (Gain from Investment - Cost of Investment) / Cost of Investment × 100
```

### Marketing ROI
```
Marketing ROI = (Revenue from Campaign - Campaign Cost) / Campaign Cost
```
**From dataset:** Summer Single Origins campaign = 1.8 ROI

## 4. Operational Metrics

### Revenue per Employee
```
Revenue per Employee = Daily Revenue / staff_count
```
**June 20:** $112.40 / 3 staff = $37.47 per employee

### Labor Cost Percentage
```
Labor Cost % = (Total Labor Costs / Total Revenue) × 100
```
**Where Labor Costs = SUM(employee hours × hourly_wage)**

### Average Transaction Value
```
Average Transaction = SUM(orders.total_amount) / COUNT(orders)
```

### Transactions per Hour
```
Transactions per Hour = COUNT(orders) / operating_hours
```
**June 20:** 8 orders / 11 hours = 0.73 transactions per hour

### Customer Service Time
```
Avg Service Time = Total Service Time / COUNT(orders)
```
*Note: Requires order preparation time tracking*

### Equipment Utilization Rate
```
Utilization Rate = (Actual Usage Time / Available Time) × 100
```

### Order Fulfillment Time
```
Avg Fulfillment Time = AVG(completed_time - order_time)
```

## 5. Quality & Production Metrics

### Roasting Yield
```
Roasting Yield = (roasted_bean_weight_out / green_bean_weight_in) × 100
```
**From dataset:**
- Batch RB001: (4.2 / 5.0) × 100 = 84%
- Batch RB002: (8.3 / 10.0) × 100 = 83%

### Quality Score Average
```
Avg Quality Score = SUM(roast_quality_score) / COUNT(batches)
```
**From dataset:** (8.5 + 8.7 + 8.2 + 8.4 + 9.1) / 5 = 8.58

### Cupping Score Impact on Sales
```
Sales Correlation = CORR(cupping_score, sales_volume)
```

### Production Efficiency
```
Production Efficiency = Actual Output / Planned Output × 100
```

## 6. Marketing & Growth Metrics

### Customer Acquisition Rate
```
Acquisition Rate = New Customers / Total Customers × 100
```

### Campaign Conversion Rate
```
Conversion Rate = (Conversions / Total Reach) × 100
```
**From dataset:** New Customer Welcome = (156 × 0.125) / 156 = 12.5%

### Social Media Engagement Rate
```
Engagement Rate = (Likes + Comments + Shares) / Reach × 100
```

### Email Marketing Metrics
```
Open Rate = Opens / Emails Sent × 100
Click Rate = Clicks / Emails Sent × 100
```

### Event Success Rate
```
Event Success = Attendees / Capacity × 100
```

## 7. Seasonal & Trend Analysis

### Year-over-Year Growth
```
YoY Growth = ((Current Period - Previous Period) / Previous Period) × 100
```

### Seasonal Index
```
Seasonal Index = (Period Average / Overall Average) × 100
```

### Weather Impact Analysis
```
Weather Correlation = CORR(weather_condition, daily_revenue)
```

## 8. Advanced Analytics

### Customer Segmentation (RFM Analysis)
```
Recency Score = Days since last purchase (scaled 1-5)
Frequency Score = Number of purchases (scaled 1-5)  
Monetary Score = Total spend (scaled 1-5)
```

### Cohort Analysis
```
Cohort Retention = (Customers active in month X / Customers in initial cohort) × 100
```

### Predictive Analytics
```
Forecasted Revenue = Historical Average × Seasonal Adjustment × Growth Factor
```

## 9. Composite KPIs

### Business Health Score
```
Health Score = (Revenue Growth × 0.3) + (Customer Retention × 0.3) + 
               (Profit Margin × 0.2) + (Operational Efficiency × 0.2)
```

### Customer Satisfaction Index
```
Satisfaction Index = (Repeat Purchase Rate × 0.4) + (Average Order Value Growth × 0.3) + 
                    (Complaint Resolution Rate × 0.3)
```

## 10. Real-Time Dashboard Metrics

### Hourly Sales Velocity
```
Sales Velocity = Revenue in Current Hour / Average Revenue per Hour
```

### Live Inventory Alert
```
Stock Alert = IF(available_quantity < minimum_stock_level, "REORDER", "OK")
```

### Daily Target Progress
```
Target Progress = (Current Revenue / Daily Target) × 100
```

## Data Sources by KPI Category

### From `orders` and `order_items` tables:
- Revenue metrics, AOV, transaction counts

### From `customers` table:
- CLV, retention rates, customer segmentation

### From `products` and `inventory` tables:
- Profit margins, inventory turnover, COGS

### From `roasting_batches` table:
- Quality scores, yield rates, production efficiency

### From `expenses` table:
- Cost ratios, profitability metrics

### From `daily_operations` table:
- Operational efficiency, weather correlations

### From `marketing_campaigns` table:
- Marketing ROI, conversion rates

These formulas provide a comprehensive framework for measuring and optimizing the coffee business performance across all key areas.