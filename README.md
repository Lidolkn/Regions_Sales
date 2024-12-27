# Power BI Sales Dashboard - Regional Performance Analysis

## Objective
The aim of this project is to create a dynamic Power BI dashboard that tracks key metrics—**Sales, Profit, and Quantity**—across four regions: **Central, East, South, and West**. This dashboard provides strategic insights into regional performance, enabling data-driven decisions.

---

## Data Source
**Kaggle** - Superstore Data Analysis  
Accessible at [Kaggle.com](https://www.kaggle.com).

---

## Tool Used
- **Power BI**: Utilized to visualize and analyze sales data effectively across different regions.

---

## Business Requirements

### General Requirements
- Design a dynamic Power BI dashboard to track **Sales, Profit, and Quantity** across four regions: Central, East, South, and West.
- Allow users to filter by **year** and dynamically switch between the three metrics (**Sales, Profit, Quantity**).
- Include a comparison with the **previous year's (PY)** sales for the selected year.

### Specific Region Requirements
#### Central Region
- Display **Sales, Profit, and Quantity** based on the selected year.
- Allow dynamic selection between **Sales, Profit, and Quantity**.
- Show **previous year's Sales** for the selected year.
- Create a **bar sparkline** for monthly data, with an average line for trend analysis.

#### East Region
- Same requirements as Central Region.

#### South Region
- Same requirements as Central Region.

#### West Region
- Same requirements as Central Region.

---

## Additional Requirements
### Metrics Table/Grid
- Include a detailed table/grid for current and previous year metrics:
  - **CY Sales**: Current Year Sales  
  - **PY Sales**: Previous Year Sales  
  - **YoY Sales**: Year-over-Year Sales growth/decline  
  - **CY Profit**: Current Year Profit  
  - **PY Profit**: Previous Year Profit  
  - **YoY Profit**: Year-over-Year Profit growth/decline  
  - **CY Qty**: Current Year Quantity  
  - **PY Qty**: Previous Year Quantity  
  - **YoY Qty**: Year-over-Year Quantity growth/decline  

### Sales by State
1. **Bubble Map**: Visualize sales distribution across states, with bubble size corresponding to sales volume.
2. **Bar Chart**: Detailed breakdown of sales by state, with sorting options for easy comparison.

---

## Key Visualizations
- **Bubble Map**: Highlights sales distribution by state, with bubble size representing sales volume.
- **Bar Chart**: Provides a detailed view of sales by state, emphasizing top and bottom performers.
- **Sparklines with Average Line**: Displays monthly trends and fluctuations for better seasonal analysis.

---

## Performance Overview and Recommendations

### Central Region
- **Performance**: Stable YoY sales growth of 5%; slight 2% decline in quantity sold.  
- **Insight**: Strong demand, but a drop in quantity sold suggests pricing or supply chain issues.  
- **Recommendation**: Explore inventory strategies to address the quantity decrease.

### East Region
- **Performance**: Strongest profit growth of 10% YoY, 8% increase in sales, and 6% increase in quantity sold.  
- **Insight**: Effective sales strategies and high market demand, especially in Q3.  
- **Recommendation**: Focus marketing efforts in Q3 to sustain growth.

### South Region
- **Performance**: Steady growth—4% increase in sales, 3% in profit, stable quantity.  
- **Insight**: Consistent demand and reliable customer retention.  
- **Recommendation**: Use cross-selling and upselling strategies for moderate growth.

### West Region
- **Performance**: 5% decline in quantity sold; stable sales value, slight profit decrease.  
- **Insight**: Pricing or cost challenges are impacting profitability.  
- **Recommendation**: Reassess pricing strategies and implement cost controls to stabilize margins.

---

## Summary of Insights
- **Growth Opportunities**: Focus on high-growth regions (e.g., East) to leverage strong demand.  
- **Inventory Adjustments**: Address declining quantity trends in Central and West regions.  
- **Cost Controls**: Prioritize cost strategy refinements in the West to safeguard profitability.  

---

## How to Use
1. Open the provided `.pbix` file in **Power BI Desktop**.
2. Interact with the dashboard:
   - Apply filters for **year** and **KPI**.
   - Explore regional insights using the visualizations.
   - Analyze performance metrics and trends for informed decision-making.

