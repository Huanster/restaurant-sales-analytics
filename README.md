# Restaurant Sales Analytics (MySQL · Data Cleaning · Power BI Dashboard)

This project analyzes messy restaurant transaction data to show how SQL, data cleaning, and visualization can be used to improve revenue, menu strategy, and staffing efficiency. The analysis is performed in MySQL, and insights are visualized in an interactive Power BI dashboard.

The work includes:

- importing a real, intentionally dirty restaurant dataset from Kaggle,

- building a reproducible MySQL cleaning pipeline,

- analyzing sales and menu performance using SQL,

- and creating a clean, insight-driven Power BI dashboard for decision-making.

## 1. Business Context

Restaurants collect thousands of data points every week through POS systems—orders, items sold, timestamps, payment methods, and more. In reality, this data is often inconsistent, messy, or incomplete.

This project simulates the role of a restaurant data analyst and answers:

“When do customers buy, what drives revenue, and how can we improve staffing and menu performance?”

This project demonstrates:

- SQL expertise: CTEs, joins, aggregates, string cleaning, date/time parsing

- Data cleaning: standardizing categories, fixing invalid data, removing duplicates

- Analytics: order-level metrics, menu performance, hourly demand patterns

- Power BI visualization: KPI cards, heatmaps, category analysis, ranked menu items

## 2. Dataset

-Source: Kaggle – Restaurant Sales – Dirty Data for Cleaning Training

-Rows: ~17,000 restaurant line items

-Grain: One row = one menu item sold in an order

Fields include:

-order date / time

-order type (dine-in, delivery, takeaway)

-item name & category

-quantity

-price

-branch

-payment method

This dataset is intentionally messy, allowing for real-world style cleaning in SQL.

## 3. Tools & Technologies

- MySQL — data cleaning, standardization, analysis

- Power BI — dashboard visualization

- GitHub — version control (github.com/Huanster)

- Optional: Python/pandas for exports or extra validation


## 4. Business Questions

### Sales & Demand

- What days and hours generate the most orders and revenue?

- How does performance differ by order type (dine-in vs delivery vs takeaway)?

### Menu Performance

- Which items and categories generate the highest revenue?

- Which items have high volume but low price (potentially underpriced)?

- How concentrated is revenue among the top items?

### Operational Efficiency

- When is the restaurant under-staffed or over-staffed?

- How should management adjust schedules based on hourly demand patterns?

## 5. Project Structure
restaurant-sales-analytics/
  ├─ README.md
  ├─ docs/
  │   ├─ 01_project_overview.md
  │   ├─ 02_data_understanding.md
  │   ├─ 03_data_cleaning.md
  │   ├─ 04_sql_analysis.md
  │   ├─ 05_visualization_and_insights.md
  │   └─ 06_conclusions_and_next_steps.md
  ├─ sql/
  │   ├─ create_tables.sql
  │   ├─ cleaning_views.sql
  │   └─ analysis_queries.sql
  ├─ data/
  │   └─ restaurant_sales_dirty.csv
  └─ dashboard/
      └─ restaurant_dashboard.pbix




## 6. Data Cleaning in MySQL

This project uses a three-step cleaning pipeline:

### 1. Staging Table

Raw CSV imported as text into restaurant_sales_raw.

### 2. Cleaning Views

- Parse dates/times using STR_TO_DATE

- Standardize categories with LOWER(), TRIM(), and CASE

- Fix typos and batch inconsistencies in order types, branches, and payment methods

- Convert quantity and price to numeric data types

- Remove invalid rows (negative quantity/price, invalid timestamps)

### 3. Final Clean Table

restaurant_sales_clean with:

-cleaned categories

-consistent order types

-valid dates/times

-numeric fields

- line_revenue = quantity * unit_price

This table becomes the foundation for all downstream analysis and Power BI visuals.


## 7. SQL Analysis

All analysis is performed in MySQL and includes:

#### Order-Level Aggregations

- Total orders

- Total revenue

- Average order value (AOV)

#### Time-Based Demand

- Revenue by day

- Orders by hour

- Weekday × hour heatmap output (later visualized in Power BI)

#### Menu Performance

- Top items by revenue

- Top items by quantity

- Category-level revenue

- Revenue concentration (Pareto-style analysis)

## Branch Insights

If the dataset has branches, branch-level KPIs are computed for comparison.

All SQL is documented in sql/analysis_queries.sql.

## 8. Power BI Dashboard

The dashboard consists of four main pages:

### Page 1 – Executive Summary

Total revenue

Total orders

Average order value

Revenue by order type

Daily revenue trend

### Page 2 – Demand & Staffing

Heatmap: orders by weekday × hour

Hourly order distribution

Staffing insights

### Page 3 – Menu Performance

Top 10 items by revenue

Top 10 items by quantity

Scatter: quantity vs price

### Page 4 – Category Mix

Revenue share by category

AOV by category

Live Dashboard (Power BI)

Once published to Power BI Public or embedded, add link here:

➡️ Power BI Dashboard: [Add link here]
➡️ dashboard/restaurant_dashboard.pbix included in repo

## 9. Key Insights (Replace with Your Actual Results)

Example placeholders you can replace with real values:

- Peak demand occurs on Fridays and Saturdays between 18:00–21:00, with demand nearly 2× above baseline.

- Top 10 items contribute 70–75% of revenue.

- Delivery orders show higher order volume but slightly lower AOV than dine-in.

- Some categories (e.g., beverages or desserts) show high volume but uneven pricing—good candidates for upsells or repricing.

## 10. Running the Project
### 1. Clone the repository
git clone https://github.com/Huanster/restaurant-sales-analytics.git
cd restaurant-sales-analytics
## 2. 2. Set up MySQL

- Create a database

- Run /sql/create_tables.sql

- Load the Kaggle CSV into restaurant_sales_raw
## 3. Apply cleaning logic
SOURCE sql/cleaning_views.sql;
## 4. Run analysis queries
SOURCE sql/analysis_queries.sql;

## 5. Open Power BI

- Load cleaned MySQL table or exported CSVs

- Build visuals from the SQL outputs

## 11. Project Highlights

- Built a clean, analysis-ready dataset from messy restaurant sales data

- Demonstrated SQL mastery: cleaning, transforming, aggregating

- Designed a Power BI dashboard to communicate insights

- Used analytics to answer real restaurant business questions

- End-to-end documentation of thought process and methodology








