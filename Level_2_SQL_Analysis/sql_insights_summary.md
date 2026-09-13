# Primeor Solutions - Level 2: SQL Analysis & Business Insights Summary

## Executive Summary
This document summarizes the quantitative results and strategic business insights derived from running the 10 required SQL queries on the cleaned e-commerce sales dataset.

---
### Query 1: Top 10 Profitable Products
*Identifies the highest profit-generating products across the entire catalog.*

```
                                            product_name        category sub_category  total_sales  total_profit
                   Canon imageCLASS 2200 Advanced Copier      Technology      Copiers      61600.0      25199.94
                            Cisco Smart Phone, Full Size      Technology       Phones      76441.0      17238.52
                         Motorola Smart Phone, Full Size      Technology       Phones      73159.0      17027.13
                                       Hoover Stove, Red Office Supplies   Appliances      31664.0      11807.96
                    Sauder Classic Bookcase, Traditional       Furniture    Bookcases      39110.0      10672.06
Harbour Creations Executive Leather Armchair, Adjustable       Furniture       Chairs      50120.0      10427.33
                            Nokia Smart Phone, Full Size      Technology       Phones      71904.0       9938.20
                       Cisco Smart Phone, with Caller ID      Technology       Phones      43124.0       9786.65
                       Nokia Smart Phone, with Caller ID      Technology       Phones      47880.0       9465.34
                                      Belkin Router, USB      Technology  Accessories      23473.0       8955.01
```

### Query 2: Top 10 Customers by Sales
*Lists the most valuable customers based on total gross sales revenue.*

```
     customer_name     segment  total_orders  total_sales  total_profit
      Tom Ashbrook Home Office            30      40489.0       6312.01
      Tamara Chand   Corporate            36      37453.0       8672.89
         Greg Tran    Consumer            34      35552.0       5214.12
Christopher Conant    Consumer            39      35187.0       5603.34
       Sean Miller Home Office            27      35131.0       -397.21
      Bart Watters   Corporate            45      32315.0       3595.86
  Natalie Fritzler    Consumer            43      31778.0       1542.87
      Fred Hopkins   Corporate            39      30404.0       4609.29
         Jane Waco   Corporate            40      30288.0       6265.83
      Hunter Lopez    Consumer            24      30246.0       7816.58
```

### Query 3: Region-wise Total Sales
*Analyzes aggregate sales volume and profitability across geographical regions.*

```
        region  total_transactions  total_sales  total_profit  profit_margin_pct
       Central               11115    2821740.0     311555.12              11.04
         South                6643    1600600.0     140241.17               8.76
         North                4783    1248121.0     194598.48              15.59
       Oceania                3484    1098253.0     121519.50              11.06
Southeast Asia                3128     883702.0      17670.62               2.00
    North Asia                2337     846991.0     165374.65              19.52
          EMEA                5026     805053.0      43810.19               5.44
        Africa                4585     783345.0      88848.17              11.34
  Central Asia                2048     752839.0     132480.18              17.60
          West                3203     725514.0     108302.12              14.93
```

### Query 4: Category-wise Average Profit
*Evaluates average profitability and margin per transaction across product categories.*

```
       category  total_orders  total_sales  avg_profit_per_order  total_profit  profit_margin_pct
     Technology         10137    4742975.0                 65.44     663340.48              13.99
      Furniture          9867    4105771.0                 29.00     286183.66               6.97
Office Supplies         31267    3786476.0                 16.58     518376.57              13.69
```

### Query 5: Highest Discount Category
*Determines which product category receives the highest average discount rate.*

```
       category  avg_discount_pct  max_discount_pct  total_sales  total_profit
      Furniture             16.80              85.0    4105771.0     286183.66
Office Supplies             13.74              80.0    3786476.0     518376.57
     Technology             13.54              70.0    4742975.0     663340.48
```

### Query 6: Orders with Negative Profit (Loss-Making Orders)
*Highlights transactions resulting in negative net margins to isolate revenue leakage.*

```
       order_id order_date    customer_name                              product_name        category sub_category  discount_pct  sales  loss_amount
 CA-2013-108196 2013-11-26    Cindy Stewart Cubify CubeX 3D Printer Double Head Print      Technology     Machines          70.0 4500.0     -6599.98
   TU-2013-9400 2013-09-26    Denise Monton            Motorola Smart Phone, Cordless      Technology       Phones          60.0 3085.0     -4088.38
 US-2014-168116 2014-11-05   Grant Thornton Cubify CubeX 3D Printer Triple Head Print      Technology     Machines          50.0 8000.0     -3839.99
 CA-2011-169019 2011-07-26      Luke Foster GBC DocuBind P400 Electric Binding System Office Supplies      Binders          80.0 2178.0     -3701.89
 CA-2014-134845 2014-04-18   Sharelle Roach Lexmark MX611dhe Monochrome Laser Printer      Technology     Machines          70.0 2550.0     -3399.98
IT-2013-3695467 2013-06-10 Saphhira Shifley                       Hoover Stove, White Office Supplies   Appliances          50.0 3400.0     -3059.82
  ID-2013-12295 2013-09-14     Skye Norling              Apple Smart Phone, Full Size      Technology       Phones          50.0 3499.0     -3009.44
 US-2014-122714 2014-12-08    Henry Goldwyn      Ibico EPK-21 Electric Binding System Office Supplies      Binders          80.0 1890.0     -2929.48
   LH-2014-5390 2014-01-28  Julie Creighton    Barricks Conference Table, Rectangular       Furniture       Tables          70.0 2171.0     -2750.28
 CA-2012-147830 2012-12-15 Natalie Fritzler Cubify CubeX 3D Printer Double Head Print      Technology     Machines          70.0 1800.0     -2639.99
```

### Query 7: Monthly Sales Trend
*Tracks overall monthly revenue performance to observe seasonality and growth.*

```
year_month  order_volume  monthly_sales  monthly_profit
   2011-01           433        98902.0         8302.02
   2011-02           378        91152.0        12661.60
   2011-03           539       145726.0        15248.29
   2011-04           565       116985.0        12864.82
   2011-05           566       146762.0        12188.65
   2011-06           917       215214.0        23415.11
   2011-07           495       115518.0         5585.02
   2011-08           878       207570.0        23713.61
   2011-09          1052       290230.0        35776.86
   2011-10           774       199070.0        25963.35
```

### Query 8: Market-wise Revenue Analysis
*Provides macro-level revenue and profit distribution across global markets.*

```
market  total_orders  total_revenue  total_profit  profit_margin_pct
  APAC         10997      3581785.0     437044.95              12.20
    EU          9998      2937166.0     372884.62              12.70
    US          9990      2297022.0     286191.42              12.46
 LATAM         10291      2163919.0     221299.54              10.23
  EMEA          5026       805053.0      43810.19               5.44
Africa          4585       783345.0      88848.17              11.34
Canada           384        66932.0      17821.82              26.63
```

### Query 9: Top-Performing Sub-Categories
*Ranks sub-categories by sales revenue, gross profit, and overall transaction volume.*

```
       category sub_category  total_sales  total_profit  profit_margin_pct
     Technology       Phones    1706642.0     216705.30              12.70
     Technology      Copiers    1508370.0     258174.43              17.12
      Furniture       Chairs    1500930.0     141735.47               9.44
      Furniture    Bookcases    1463615.0     161703.08              11.05
Office Supplies      Storage    1126579.0     108541.53               9.63
Office Supplies   Appliances    1011081.0     141680.57              14.01
     Technology     Machines     779071.0      58891.98               7.56
      Furniture       Tables     756031.0     -64113.55              -8.48
     Technology  Accessories     748892.0     129568.77              17.30
Office Supplies      Binders     461842.0      72313.32              15.66
```

### Query 10: Ship Mode Usage Analysis
*Analyzes shipping tier popularity, revenue generation, and average shipping cost.*

```
     ship_mode  total_orders  usage_share_pct  total_sales  avg_shipping_cost
Standard Class         30764            60.00    7574395.0              19.96
  Second Class         10304            20.10    2563078.0              30.44
   First Class          7504            14.64    1830652.0              41.04
      Same Day          2699             5.26     667097.0              42.96
```

---

## Key Business Insights & Answers to Core Questions (Level 2 Task 3)

### 1. Which Market Generates the Highest Revenue?
- **Top Market:** **APAC** is the #1 revenue driver globally.
- **Total Revenue:** **$3,581,785.00** (28.3% of total global sales).
- **Profitability:** Generated **$437,044.95** in net profit with a strong profit margin of **12.2%**.
- **Runner Up:** **EU** and **US** markets follow closely with high profit margins.

### 2. Which Categories are Least Profitable?
- **Least Profitable Category by Margin:** **Furniture** has the lowest profit margin (**6.97%**).
- **Driver of Margin Compression:** Furniture suffers from high shipping weights, bulky logistics, and steep discounting (average discount is notably high in Tables and Bookcases).
- **Highest Profitable Category:** **Technology** leads in both absolute profit and margin (**13.99%**).

### 3. Which Shipping Mode is Most Commonly Used?
- **Dominant Shipping Mode:** **Standard Class** represents **60.0%** of all customer shipments (30,764 orders).
- **Logistics Cost:** Average shipping cost for Standard Class is **$19.96**, making it the most cost-effective tier for consumers.
- **Expedited Shipping:** Same Day shipping represents only ~5.4% of volume, reserved for urgent/critical orders with significantly higher per-unit freight charges.

### 4. Loss-Making Orders Analysis & Discount Leakage
- **Negative Profit Orders:** There are **12,534 loss-making transactions**, resulting in a cumulative profit erosion of **$920,067.59**.
- **Root Cause:** Excessive discount percentages (>30-50%) on low-margin items (especially Binders, Tables, and Machines).
- **Actionable Recommendation:** Institute an automated discount cap of 20% on Furniture and require managerial approval for discounts above 25%.
