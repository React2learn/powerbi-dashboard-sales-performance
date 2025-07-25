# 📊 Power BI Sales Dashboard Report
## 📝 Overview

This Power BI dashboard provides a visual analysis of sales data across regions, products, and time. It includes key performance indicators (KPIs), trends, and categorical breakdowns.

## 📁 Dataset
- Source: Sheet1 (Imported Excel or CSV)
- Fields Used

| Date & Category Info | Metrics              |
|----------------------|----------------------|
| `OrderDate`          | `Revenue`            |
| `Product`            | `UnitsSold`          |
| `Region`             | `UnitPrice`          |
| `Salesperson`        | `OrderID`            |


## 📌 KPIs (Displayed as Cards)

| **Metric**           | **Description**                    |
|----------------------|------------------------------------|
| **Total Revenue**    | Sum of all sales revenue           |
| **Total Orders**     | Count of orders placed             |
| **Avg Selling Price**| Revenue ÷ Units Sold               |
| **Top Product**      | Product with highest revenue       |

---

## 📈 Visualizations

### ✅ Units Sold by Product (%)
- Pie chart showing sales share by product  
- 🏆 **Most sold**: `Monitor`

### ✅ Sales by Region (₹)
- Horizontal bar chart by region  
- 🌍 **Top regions**: East and West

### ✅ Revenue Over Time (Daily)
- Line chart displaying revenue trend by day  
- 📈 Spikes observed in **March (Q1)**

### ✅ Detailed Sales Records Table
- Raw table showing: `Date`, `Region`, `Product`, `Revenue`  
- Scrollable for complete detail view

### ✅ Salesperson Filter
- Slicer to filter all visuals by selected salesperson

---

## 🧠 DAX Measures Used

```DAX
Total Revenue = SUM(Sheet1[Revenue])

Total Orders = DISTINCTCOUNT(Sheet1[OrderID])

Avg Selling Price = DIVIDE(SUM(Sheet1[Revenue]), SUM(Sheet1[UnitsSold]))

Top Product = 
CALCULATE(
    MAX(Sheet1[Product]),
    TOPN(1, SUMMARIZE(Sheet1, Sheet1[Product], "Rev", SUM(Sheet1[Revenue])), [Rev], DESC)
)

Revenue Last Year = 
CALCULATE([Total Revenue], SAMEPERIODLASTYEAR(DateTable[Date]))

YoY Revenue Growth % = 
DIVIDE([Total Revenue] - [Revenue Last Year], [Revenue Last Year])
```

## 💡 Insights & Observations

- 🏆 Monitor is the top-selling product  
- 🌍 East is the highest revenue-generating region  
- 📅 Revenue peaks in Q1, especially March  
- ✅ Clean card layout allows fast performance tracking  

---

## 📁 Files in This Repository

- `SalesDashboard.pbix` — Power BI report file  
- `dashboard_preview.png` — Dashboard screenshot  
- `README.md` — Project overview and summary  
