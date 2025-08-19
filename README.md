# Retail Sales Insights using SQL & Power BI (AtliQ Hardware)

## 📌 Project Overview

This project analyzes **AtliQ Hardware's retail sales data** using **SQL** and **Power BI** to uncover key business insights. The goal is to understand sales trends, identify high-value customers, and provide actionable insights that can improve decision-making and boost revenue.

---

## 🎯 Objectives

* Analyze sales performance across regions, products, and time periods.
* Identify top customers and markets contributing to revenue.
* Normalize revenue across different currencies (USD, INR).
* Build an interactive Power BI dashboard to monitor KPIs.

---

## 🗄️ Dataset

The project uses a **MySQL database** (`db_dump.sql`) with the following key tables:

* **customers** – customer details with type (Brick & Mortar / E-Commerce).
* **date** – calendar table with year, month, and date attributes.
* **transactions** – sales transactions including market, currency, and sales amount.

---

## 🛠️ Tools & Technologies

* **SQL (MySQL):** Data extraction and transformation.
* **Power BI:** Dashboard creation and data visualization.
* **Excel:** Additional data cleaning (if required).

---

## 📊 SQL Analysis

Some key SQL queries performed:

* Show all customer records:

  ```sql
  SELECT * FROM customers;
  ```
* Show total number of customers:

  ```sql
  SELECT COUNT(*) FROM customers;
  ```
* Show transactions for Chennai market:

  ```sql
  SELECT * FROM transactions WHERE market_code='Mark001';
  ```
* Calculate total revenue in 2020:

  ```sql
  SELECT SUM(t.sales_amount)
  FROM transactions t
  INNER JOIN date d ON t.order_date = d.date
  WHERE d.year = 2020 AND (t.currency='INR' OR t.currency='USD');
  ```

---

## 📈 Power BI Dashboard

* Created a **normalized sales amount (norm\_amount)** column:

  ```powerquery
  = Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] = "USD#(cr)" then [sales_amount]*75 else [sales_amount], type any)
  ```
* Designed interactive dashboards showing:

  * Revenue trends by year and month.
  * Top-performing markets and customers.
  * Product sales distribution.
  * Region-wise comparisons.

### 🔎 Dashboard Screenshots

**Key Insights Dashboard**
![Key Insights](https://github.com/NagullaSivaNandini/Retail-Sales-Insights/blob/main/key_insights.png)

**Profit Analysis Dashboard**
![Profit Analysis](profit_analysis.png.png)

**Performance Insights Dashboard**
![Performance Insights](https://github.com/NagullaSivaNandini/Retail-Sales-Insights/blob/main/performance_insights.png)

---

## 🚀 Outcomes

* Delivered a **clear view of sales trends and KPIs**.
* Helped stakeholders make **data-driven decisions**.
* Projected to increase quarterly revenue by **\~7%** through improved targeting and stock optimization.

---

## 📂 Repository Structure

* `db_dump.sql` → MySQL database dump.
* `si_youtube_updated_after_feedback.pbix` → Power BI dashboard file.
* `README.md` → Project documentation.
* Dashboard screenshots (`key_insights.png`, `profit_analysis.png`, `performance_insights.png`).

---

## 📝 Conclusion

This project demonstrates how combining **SQL for data extraction** and **Power BI for visualization** can create powerful business insights. The final dashboard enables AtliQ Hardware to monitor performance, identify opportunities, and drive revenue growth.

