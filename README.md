# Superstore Sales & Business Analytics Dashboard

An end-to-end Data Analytics project using **SQL Server, Power BI, Power Query, and DAX** to analyze sales performance, profitability, product performance, customer behavior, and regional trends.

The project transforms raw Superstore sales data into meaningful business insights through SQL analysis and a three-page interactive Power BI dashboard.

---

## 📊 Dashboard Preview

### 1. Executive Overview

This page provides a high-level overview of the business's sales and profitability.

![Executive Overview Dashboard](screenshots/executive_overview.png)

**Key metrics and visualizations:**
- Total Sales
- Total Profit
- Profit Margin
- Total Orders
- Total Customers
- Average Order Value
- Sales and Profit Trends Over Time
- Sales by Category
- Sales by Region

### 2. Product & Sales Performance

This page analyzes product-level performance and identifies products that generate high revenue but have negative profit.

![Product and Sales Performance Dashboard](screenshots/product_sales_performance.png)

**Key analyses:**
- Top 10 Products by Sales
- Top 10 Products by Profit
- High-Sales Products with Negative Profit
- Profit by Category
- Discount vs. Profit

### 3. Customer & Regional Analysis

This page explores customer value and compares business performance across geographic regions.

![Customer and Regional Analysis Dashboard](screenshots/customer_regional_analysis.png)

**Key analyses:**
- Top 10 Customers by Sales
- Top 10 Customers by Profit
- One-Time vs. Returning Customers
- Sales by Region
- Profit by Region

---

## 🎯 Business Questions

This project answers the following business questions:

1. What are the total sales, total profit, and overall profit margin?
2. How do sales and profit change over time?
3. Which products generate the highest sales and profit?
4. Which products have high sales but negative profit?
5. Which categories and sub-categories are the most profitable?
6. How do sales and profit vary across regions?
7. Who are the most valuable customers by sales and profit?
8. How many customers are classified as one-time versus returning?
9. How are different discount levels associated with profitability?

---

## 🛠️ Tools & Technologies

- **SQL Server / SSMS:** Business analysis, aggregations, filtering, grouping, and customer and product analysis.
- **Power BI:** Interactive dashboards and business data visualization.
- **Power Query:** Data cleaning, transformation, and preparation.
- **DAX:** Calculated measures and key performance indicators.
- **Excel:** Supporting data preparation and validation.

---

## 🧹 Data Preparation

The dataset was prepared before the analysis to improve data quality and consistency.

Key preparation steps included:

- Removed the unnecessary `Row ID` field.
- Validated and corrected `Order Date` and `Ship Date` data types.
- Reviewed numeric data types for Sales, Profit, Quantity, and Discount.
- Prepared the data using Power Query.
- Imported the cleaned dataset into SQL Server.
- Validated key business metrics against SQL query results.

**Dataset:** [Superstore Sales — Kaggle](https://www.kaggle.com/datasets/josephguria/superstore-sales)

---

## 📈 Key Findings

### Overall Business Performance

- **Total Sales:** $2,297,201.07
- **Total Profit:** $286,397.79
- **Profit Margin:** 12.47%
- **Total Orders:** 5,009
- **Total Customers:** 793
- **Average Order Value:** $458.61
- **Total Quantity Sold:** 37,873

### Sales Trends

Annual sales increased from approximately **$484.25K in 2011** to **$733.95K in 2014**.

Annual profit also increased over the same period, from approximately **$49.54K** to **$93.51K**.

### Category Profitability

- **Technology** generated approximately $145.46K in profit.
- **Office Supplies** generated approximately $122.49K in profit.
- **Furniture** generated approximately $18.45K in profit.

Furniture had a profit margin of approximately **2.49%**, substantially lower than Technology and Office Supplies.

### Regional Performance

The **West** region generated the highest total sales, at approximately **$725.46K**, and the highest total profit, at approximately **$108.42K**.

The Central region had a lower overall profit margin than the other regions, highlighting an opportunity for more detailed regional and category-level analysis.

### Product Performance

Some products generated substantial sales while recording negative total profit. Revenue alone is therefore not sufficient to evaluate product performance.

### Discounts and Profitability

Several higher discount levels were associated with negative profit. This relationship highlights the importance of monitoring discount policies and profitability together. It does not, by itself, prove that discounts caused the losses.

### Customer Behavior

Based on distinct order counts in the dataset:

- **Returning Customers:** 781 (98.49%)
- **One-Time Customers:** 12 (1.51%)

These classifications are derived from the available order history and are not original dataset fields.

---

## 💰 Key Metrics

| Metric | Value |
|---|---:|
| Total Sales | $2,297,201.07 |
| Total Profit | $286,397.79 |
| Profit Margin | 12.47% |
| Total Orders | 5,009 |
| Total Customers | 793 |
| Average Order Value | $458.61 |
| Total Quantity | 37,873 |

---

## 🧮 SQL Analysis

SQL Server was used to perform business-focused analysis, including:

- Overall sales and profitability.
- Sales and profit trends by year and month.
- Top products by sales and profit.
- Products with high sales but negative profit.
- Category and sub-category profitability.
- Regional performance.
- Customer sales and profit analysis.
- Discount-level profitability.
- One-time and returning customer classification using Common Table Expressions (CTEs).

### Example SQL Query: High Sales but Negative Profit

```sql
SELECT TOP 10
    Product_Name,
    SUM(Sales) AS Total_Sales,
    SUM(Profit) AS Total_Profit
FROM Superstore_Cleaned
GROUP BY Product_Name
HAVING
    SUM(Sales) > 10000
    AND SUM(Profit) < 0
ORDER BY Total_Profit ASC;
```

**What this query does:**

1. `SELECT TOP 10` returns up to ten products.
2. `SUM(Sales)` calculates the total sales for each product.
3. `SUM(Profit)` calculates the total profit for each product.
4. `GROUP BY Product_Name` aggregates records by product.
5. `HAVING` keeps products with more than $10,000 in sales and negative total profit.
6. `ORDER BY Total_Profit ASC` places the products with the largest losses first.

This analysis helps identify products that generate revenue but may require pricing, discount, or cost review.

---

## 📂 Repository Structure

```text
superstore-sales-business-analytics/
│
├── README.md
│
├── data/
│   └── README.md
│
├── sql/
│   └── superstore_analysis.sql
│
├── powerbi/
│   └── Superstore_Dashboard.pbix
│
└── screenshots/
    ├── executive_overview.png
    ├── product_sales_performance.png
    └── customer_regional_analysis.png
```

*This is the suggested repository structure. Include the files and folders that actually exist in your GitHub repository.*

---

## ⚠️ Important Notes & Limitations

- The One-Time vs. Returning classification is derived from the number of distinct orders per customer.
- The customer-type donut chart uses a separate summary table with fixed counts. It does not automatically respond to filters applied to the original sales table.
- Observed relationships between discounts and profit do not establish causation.
- The findings describe the available dataset and its historical period; they should be interpreted within that context.

---

## 🚀 Skills Demonstrated

- Data cleaning and preparation
- SQL querying and business analysis
- Aggregation and grouping with `GROUP BY`
- Filtering with `WHERE` and `HAVING`
- Customer analysis using `COUNT(DISTINCT)`
- Conditional logic using `CASE`
- Common Table Expressions (CTEs)
- KPI development using DAX
- Power BI dashboard design
- Product and category profitability analysis
- Customer and regional analysis
- Business insights and data storytelling

---

## 👨‍💻 Author

**Abdelrhman Taha**

Data Analytics | SQL | Power BI | Business Intelligence

