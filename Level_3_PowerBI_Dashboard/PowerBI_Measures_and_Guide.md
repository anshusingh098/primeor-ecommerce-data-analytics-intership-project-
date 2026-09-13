# Primeor Solutions - Level 3: Power BI Dashboard Architecture & DAX Measures Guide

## 1. Data Model Setup
- **Fact Table:** `sales_data` (imported from `Cleaned_Dataset.csv` or `Cleaned_Dataset.xlsx`)
- **Relationships:**
  - Date table linked on `order_date`
  - Customer table linked on `customer_name`
  - Product table linked on `product_id`

---

## 2. Core DAX Measures

### Metric 1: Total Sales
```dax
Total Sales = SUM(sales_data[sales])
```

### Metric 2: Total Profit
```dax
Total Profit = SUM(sales_data[profit])
```

### Metric 3: Total Orders
```dax
Total Orders = DISTINCTCOUNT(sales_data[order_id])
```

### Metric 4: Total Quantity Sold
```dax
Total Quantity = SUM(sales_data[quantity])
```

### Metric 5: Average Discount
```dax
Average Discount = AVERAGE(sales_data[discount])
```

### Metric 6: Profit Margin %
```dax
Profit Margin % = 
DIVIDE([Total Profit], [Total Sales], 0)
```

### Metric 7: Average Order Value (AOV)
```dax
Average Order Value = 
DIVIDE([Total Sales], [Total Orders], 0)
```

### Metric 8: Total Shipping Cost
```dax
Total Shipping Cost = SUM(sales_data[shipping_cost])
```

### Metric 9: Year-over-Year (YoY) Sales Growth
```dax
YoY Sales Growth = 
VAR PreviousYearSales = CALCULATE([Total Sales], SAMEPERIODLASTYEAR('Calendar'[Date]))
RETURN
DIVIDE([Total Sales] - PreviousYearSales, PreviousYearSales, 0)
```

### Metric 10: Loss-Making Orders Count
```dax
Loss Orders Count = 
CALCULATE([Total Orders], sales_data[profit] < 0)
```

---

## 3. Dashboard Structure & Design System

### Theme Colors:
- **Primary Navy:** `#1B365D` (Headers, Primary Bars)
- **Secondary Teal:** `#00A896` (Profit, Highlights)
- **Accent Gold:** `#F5A623` (Discounts, Segment Accent)
- **Warning Red:** `#D9534F` (Loss-making items)
- **Background:** `#F4F6F9`
- **Card Background:** `#FFFFFF` with drop shadow

### Page Layouts:
1. **Page 1: Executive Overview**
   - Slicers: Year, Market, Segment
   - KPI Cards: Total Sales ($12.64M), Total Profit ($1.47M), Total Orders (25,035), Average Discount (14.3%)
   - Visuals: Category Performance Clustered Column Chart, Market Revenue Share Donut Chart
2. **Page 2: Sales Analysis**
   - Slicers: Market, Region, Ship Mode
   - Visuals: Top Regions Bar Chart, Global Market Bar Chart, 48-Month Revenue Trend Area Chart, Profit Margin % by Category
3. **Page 3: Product & Customer Insights**
   - Slicers: Category, Sub-Category, Region
   - Visuals: Top 5 Profitable Products Bar Chart, Top 5 Customers by Revenue, Sub-Category Net Margin Tornado Chart (highlighting Tables loss), Segment Clustered Column Chart
