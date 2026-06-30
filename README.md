# 💰 Automated Financial Reporting Dashboard

A Power BI dashboard project analyzing financial sales performance with custom DAX measures, drill-through navigation, and time-intelligence calculations.

---

## 📊 Dashboard Preview

### Page 1 — Executive Summary
<img width="1121" height="625" alt="executivesummary" src="https://github.com/user-attachments/assets/71c9b71e-b63f-4259-a0bb-632f7bb3a0c4" />


### Page 2 — Detail Report
<img width="1116" height="611" alt="detailreport" src="https://github.com/user-attachments/assets/f94fd741-193e-4105-836d-71842f8eb3c8" />


---

## 🛠️ Tools & Technologies
| Tool | Purpose |
|---|---|
| Power BI Desktop | Dashboard development and visualization |
| DAX | Time-intelligence measures (MoM Growth, YTD Sales) |
| Power Query | Data modeling and date table creation |

---

## 📁 Dataset
- **Source:** Microsoft Financial Sample Dataset
- **Columns:** Segment, Country, Product, Units Sold, Manufacturing Price, Sale Price, Gross Sales, Discounts, Sales, COGS, Profit, Date

---

## 📈 Dashboard Pages

### 1. Executive Summary
- KPI cards: Total Sales, Total Profit, Profit Margin %, Total Units Sold
- Monthly sales trend with YTD comparison
- Sales by product (bar chart)
- Sales by segment (donut chart)
- Year filter (slicer)

### 2. Detail Report
- KPI cards: Total Sales, Total Profit, MoM Growth
- Detailed transaction table (Date, Country, Segment, Product, Units Sold, Sales, Profit)
- Sales by country (bar chart)
- Segment vs Product matrix
- **Drill-through enabled** from Product bar chart on Executive Summary page

---

## 💡 Key Insights
- **Total Sales:** 118.73M
- **Total Profit:** 16.89M
- **Top Product:** Velo (highest revenue contributor)
- **Top Segment:** Government (by total sales)
- **Time-Intelligence:** Custom MoM Growth and YTD Sales measures built with DAX DATEADD and TOTALYTD functions

---

## ⚙️ DAX Measures Used
```
Total Sales = SUM(financials[Sales])
Total Profit = SUM(financials[Profit])
Profit Margin % = DIVIDE([Total Profit], [Total Sales]) * 100
Total Units Sold = SUM(financials[Units Sold])
YTD Sales = TOTALYTD([Total Sales], DateTable[Date])

MoM Growth = 
VAR CurrentMonth = [Total Sales]
VAR PrevMonth = CALCULATE([Total Sales], DATEADD(DateTable[Date], -1, MONTH))
RETURN DIVIDE(CurrentMonth - PrevMonth, PrevMonth) * 100
```

## 🗂️ Data Modeling
- Built a dedicated **Date Table** using `CALENDAR()` function to support accurate time-intelligence calculations
- Established a one-to-many relationship between `financials[Date]` and `DateTable[Date]`
- Marked `DateTable` as the official Date Table for DAX time functions

---
