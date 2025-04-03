
# Customer & Product Sales Insights – Advanced SQL Case Study

## 📊 Project Overview

This project demonstrates how to analyze e-commerce order data using advanced SQL techniques. The goal is to extract actionable insights about customer behavior, product performance, and revenue trends to support data-driven decision-making.

---

## 🎯 Objective

To solve key business questions using SQL by leveraging:
- JOINs across multiple tables
- Aggregations and filters
- Window functions (`RANK`, `LAG`)
- Common Table Expressions (CTEs)
- Real-world analytical logic

---

## 🧾 Dataset Description

The dataset simulates an e-commerce environment with 3 main tables:
- **Customers**: Customer ID, Name, and Region
- **Products**: Product ID, Name, Category, and Price
- **Orders**: Order ID, Customer and Product references, Date, Quantity, and Total Amount

---

## ❓ Key Business Questions Answered

1. **Top 5 customers by total revenue**
2. **Products with the highest average order value**
3. **Regions with the highest revenue per order**
4. **Monthly revenue trend with month-over-month change**
5. **Who are the repeat customers (more than one order)?**
6. **Top 3 customers in each region by total spending**

---

## 🧠 Key SQL Concepts Used

- `JOIN`, `GROUP BY`, `HAVING`
- `RANK`, `ROW_NUMBER`, `LAG`
- `CTEs` for step-by-step logic
- Aggregates: `SUM()`, `AVG()`, `COUNT()`
- `PARTITION BY` for regional ranking

---

## 🔍 Sample Query – Top 3 Customers by Region

```sql
WITH Customer_Spending AS (
    SELECT 
        c.Region,
        c.Customer_Name,
        SUM(o.Total_Amount) AS Total_Revenue
    FROM Orders o
    JOIN Customers c ON o.Customer_ID = c.Customer_ID
    GROUP BY c.Region, c.Customer_Name
)
SELECT *
FROM (
    SELECT *,
           RANK() OVER (PARTITION BY Region ORDER BY Total_Revenue DESC) AS Rank_In_Region
    FROM Customer_Spending
) ranked
WHERE Rank_In_Region <= 3;
```

---

## ✅ Insights & Recommendations

- North and South regions lead in revenue per order
- Repeat customers drive the bulk of sales—potential for loyalty programs
- Laptops and Smartphones generate the highest average order value
- Monthly revenue peaks in Q1 and shows positive growth trends

---

## 📁 Project Files

- `advanced_sql_practice_dataset.xlsx` – simulated relational database
- SQL scripts – `sql_case_study_queries.sql`
- Power BI layout – [provided separately]
- PowerPoint report – [provided separately]
- `README.md` – this file

---

## 📌 License

This project is for learning and portfolio use. Feel free to fork and adapt.
