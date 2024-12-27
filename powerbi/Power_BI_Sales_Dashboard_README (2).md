
# Power BI Sales Dashboard

## Overview
This document details the measures, metrics, and features of a Power BI Sales Dashboard, leveraging SQL queries and visualizations to track **Sales**, **Profit**, and **Quantity**. The dashboard empowers users to gain actionable insights into regional and temporal performance.

---

## 🔢 Measures and Metrics

### 1. Foundational Measures
- **Total Sales**  
  ```sql
  SELECT SUM(Sales) AS Total_Sales
  FROM Sales_Data;
  ```
  - **Purpose**: Provides total sales as the baseline metric.

- **Total Profit**  
  ```sql
  SELECT SUM(Profit) AS Total_Profit
  FROM Sales_Data;
  ```
  - **Purpose**: Aggregates profit to evaluate overall business performance.

- **Total Quantity**  
  ```sql
  SELECT SUM(Quantity) AS Total_Quantity
  FROM Sales_Data;
  ```
  - **Purpose**: Calculates the total number of products sold.

---

### 2. Time Intelligence Metrics

#### Current Year Metrics
- **CY Sales**  
  ```sql
  SELECT SUM(Sales) AS CY_Sales
  FROM Sales_Data
  WHERE Year = EXTRACT(YEAR FROM CURRENT_DATE);
  ```
  - **Purpose**: Dynamically calculates total sales for the current year.

- **CY Profit** and **CY Quantity**  
  - Use similar logic as above for Profit and Quantity.

#### Previous Year Metrics
- **PY Sales**  
  ```sql
  SELECT SUM(Sales) AS PY_Sales
  FROM Sales_Data
  WHERE Year = EXTRACT(YEAR FROM CURRENT_DATE) - 1;
  ```
  - **Purpose**: Facilitates year-over-year comparisons.

- **PY Profit** and **PY Quantity**  
  - Use similar logic as above for Profit and Quantity.

---

### 3. Year-over-Year (YoY) Analysis

- **Year-over-Year Sales (YoY Sales)**  
  ```sql
  SELECT 
      (CY_Sales - PY_Sales) / NULLIF(PY_Sales, 0) AS YoY_Sales
  FROM (
      SELECT 
          SUM(CASE WHEN Year = EXTRACT(YEAR FROM CURRENT_DATE) THEN Sales ELSE 0 END) AS CY_Sales,
          SUM(CASE WHEN Year = EXTRACT(YEAR FROM CURRENT_DATE) - 1 THEN Sales ELSE 0 END) AS PY_Sales
      FROM Sales_Data
  ) AS YoY_Data;
  ```
  - **Purpose**: Quantifies the percentage change in sales year-over-year.

---

### 4. Dynamic Metrics and Titles

- **Dynamic Metric Query**  
  ```sql
  SELECT 
      CASE 
          WHEN Metric = 'Sales' THEN SUM(Sales)
          WHEN Metric = 'Profit' THEN SUM(Profit)
          WHEN Metric = 'Quantity' THEN SUM(Quantity)
      END AS Metric_Value
  FROM Sales_Data
  WHERE Year = EXTRACT(YEAR FROM CURRENT_DATE);
  ```
  - **Purpose**: Enables toggling between metrics for a customizable experience.

- **Dynamic Title Example**  
  ```sql
  SELECT 'Sales Dashboard - Viewing ' || Metric AS Dynamic_Title
  FROM Selected_Metric;
  ```
  - **Purpose**: Updates dashboard titles dynamically based on the selected metric.

---

## 📈 Visualizations and Their Strategic Role

- **Bubble Map**  
  - **Query**:
    ```sql
    SELECT State, SUM(Sales) AS Total_Sales
    FROM Sales_Data
    GROUP BY State;
    ```
  - **Purpose**: Displays state-wise sales distribution.  
  - **Benefit**: Identifies high- and low-performing regions for better resource allocation.

- **Bar Chart**  
  - **Query**:
    ```sql
    SELECT State, SUM(Sales) AS Total_Sales
    FROM Sales_Data
    GROUP BY State
    ORDER BY Total_Sales DESC;
    ```
  - **Purpose**: Ranks sales performance by state.  
  - **Benefit**: Highlights top and bottom performers for actionable insights.

- **Sparklines with Average Line**  
  - **Query**:
    ```sql
    SELECT Month, AVG(Sales) AS Avg_Sales, SUM(Sales) AS Total_Sales
    FROM Sales_Data
    GROUP BY Month;
    ```
  - **Purpose**: Visualizes monthly trends for Sales, Profit, and Quantity.  

- **Comparison Table**  
  - **Query**:
    ```sql
    SELECT 
        Year,
        SUM(Sales) AS Sales,
        SUM(Profit) AS Profit,
        SUM(Quantity) AS Quantity
    FROM Sales_Data
    GROUP BY Year;
    ```
  - **Purpose**: Summarizes key metrics for year-over-year comparisons.

---

## 🚀 Features Demonstrated

### **SQL Mastery**
- Constructed advanced queries for YoY analysis, dynamic filtering, and key metric calculations.
- Used date-based functions such as `EXTRACT(YEAR)` for precise temporal analysis.

### **Data Modeling Expertise**
- Built normalized data tables with relationships for efficient querying.
- Created robust temporal filtering for year, month, and quarter-based insights.

### **Visualization Excellence**
- Designed clear, relevant visuals that prioritize user understanding.
- Balanced aesthetics with functionality, ensuring a professional dashboard layout.

---

## **How to Use**
1. Export and connect your database to **Power BI Desktop**.
2. Copy the provided SQL queries into your data source to create necessary measures.
3. Visualize the output:
   - Use **Bubble Maps**, **Bar Charts**, and **Sparklines** to interpret trends.
   - Apply filters to focus on specific years, metrics, or regions.
4. Use the comparison table and YoY metrics to drive actionable insights.
