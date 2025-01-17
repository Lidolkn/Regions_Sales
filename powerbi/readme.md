# Power BI Sales Dashboard

## Overview
This document details the measures, metrics, and features of a Power BI Sales Dashboard, leveraging advanced DAX formulas and visualizations to track **Sales**, **Profit**, and **Quantity**. The dashboard empowers users to gain actionable insights into regional and temporal performance.

---

## 🔢 Measures and Metrics

### 1. Foundational Measures
- **Total Sales**  
  ```DAX
  Total Sales = SUM('Sales Data'[Sales])
  ```
  - **Purpose**: Provides total sales as the baseline metric.

- **Total Profit**  
  ```DAX
  Total Profit = SUM('Sales Data'[Profit])
  ```
  - **Purpose**: Aggregates profit to evaluate overall business performance.

- **Total QTY**  
  ```DAX
  Total QTY = SUM('Sales Data'[Quantity])
  ```
  - **Purpose**: Calculates the total number of products sold.

These measures underpin the entire dashboard and serve as the foundation for advanced calculations.

---

### 2. Time Intelligence Metrics

#### Current Year Metrics
- **CY Sales**  
  ```DAX
  CY Sales = CALCULATE([Total Sales], 'Calendar Table'[Year] = SELECTEDVALUE('Calendar Table'[Year]))
  ```
  - **Purpose**: Dynamically calculates total sales for the selected year.

- **CY Profit** and **CY QTY**  
  - Follow similar logic for profit and quantity calculations.

#### Previous Year Metrics
- **PY Sales**  
  ```DAX
  PY Sales = CALCULATE([Total Sales], 'Calendar Table'[Year] = SELECTEDVALUE('Calendar Table'[Year]) - 1)
  ```
  - **Purpose**: Facilitates year-over-year comparisons.

- **PY Profit** and **PY QTY**  
  - Used to track trends in profit and quantity compared to the previous year.

---

### 3. Year-over-Year (YoY) Analysis

- **YoY Sales**  
  ```DAX
  YoY Sales = DIVIDE([CY Sales] - [PY Sales], [PY Sales], 0)
  ```
  - **Purpose**: Quantifies the percentage change in sales YoY.

- **YoY Sales Indicator**  
  ```DAX
  YoY Sales Indicator = IF([YoY Sales] > 0, UNICHAR(9650) & FORMAT([YoY Sales], "0%"), UNICHAR(9660) & FORMAT([YoY Sales], "0%"))
  ```
  - **Purpose**: Adds intuitive visual cues (up/down arrows) for growth or decline.

---

### 4. Dynamic Metrics and Titles

- **Dynamic Metric**  
  ```DAX
  Dynamic Metric = SWITCH(
      SELECTEDVALUE('Select Metric'[Metric]),
      "Sales", [CY Sales],
      "Profit", [CY Profit],
      "Quantity", [CY QTY]
  )
  ```
  - **Purpose**: Enables seamless toggling between metrics for a customizable experience.

- **Dynamic Title**  
  ```DAX
  Dynamic Title = "Sales Dashboard - Viewing " & SELECTEDVALUE('Select Metric'[Metric])
  ```
  - **Purpose**: Updates visual titles dynamically based on the selected metric.

---

## 📈 Visualizations and Their Strategic Role

- **Bubble Map**  
  - **Purpose**: Displays state-wise sales distribution.  
  - **Why Used**: Helps quickly identify high- and low-performing regions, guiding resource allocation.

- **Bar Chart**  
  - **Purpose**: Provides a ranked comparison of sales by state.  
  - **Why Used**: Highlights top and bottom performers for actionable insights.

- **Sparklines with Average Line**  
  - **Purpose**: Visualizes monthly trends for Sales, Profit, and Quantity.  
  - **Why Used**: Highlights seasonal variations and deviations for proactive strategy adjustments.

- **Comparison Table**  
  - **Purpose**: Summarizes key metrics (CY vs. PY) for Sales, Profit, and Quantity.  
  - **Why Used**: Offers a comprehensive view of year-over-year performance in one format.

---

## 🚀 Features Demonstrated

### DAX Mastery
- Constructed advanced measures for YoY analysis, dynamic filtering, and KPI calculations.
- Used time intelligence functions such as `SAMEPERIODLASTYEAR` and `TOTALYTD` for precise date-based analytics.

### Data Modeling Expertise
- Established efficient table relationships for seamless data connectivity.
- Created a robust Calendar Table for granular year, month, and quarter-based analysis.

### Visualization Excellence
- Designed visuals with clarity and relevance in mind.
- Balanced aesthetics and functionality, ensuring a professional and user-friendly dashboard.

---

## How to Use
1. Download and open the `.pbix` file in **Power BI Desktop**.
2. Interact with the dashboard:
   - Apply filters to view data by year or selected metrics.
   - Explore regional insights using visualizations like the **Bubble Map**, **Bar Chart**, and **Sparklines**.
3. Use the comparison table to analyze performance trends and strategic opportunities.
