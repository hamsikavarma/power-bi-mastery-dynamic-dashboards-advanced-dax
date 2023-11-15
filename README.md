# Power-BI-Mastery-Dynamic-Dashboards-Advanced-DAX

### Project Overview
This project showcases an Advanced Power BI Sales Dashboard, incorporating dynamic bookmarks, complex DAX calculations, and interactive storytelling techniques to analyze business sales performance. Designed to track key financial metrics, the dashboard provides insights for both executive-level decision-making and operational-level performance analysis.

---

## Dashboard Preview
[Click to view dashboard via Power BI web Link](https://app.powerbi.com/view?r=eyJrIjoiNTQ0YTllMGItMjUxNi00ZDdiLThmZmUtMGQxNWI4ODdkMGExIiwidCI6IjY3NmQ5MDg1LTQzMjMtNDc2NS1iZTVjLWNjMDdlMTEyMTA5MiJ9) 

<div style="display: flex; flex-direction: row;">
  <img src="Icons & Screenshots/Dashboard.gif" alt="Dashboard" width="400" style="margin-right: 20px;">
</div>

---

### Industry Use Case
Sales performance analysis is critical for organizations looking to optimize revenue, monitor trends, and enhance strategic decision-making. This project applies best practices in business intelligence (BI) and data visualization to provide actionable insights into YoY growth, customer satisfaction, and profitability.

---

## Key Features and Functionalities

### Executive-Level Insights
- YoY Growth Analysis: High-level growth trends using REMOVEFILTERS() to ensure business-wide visibility.
- Gross Sales and Profit KPIs: Key financial indicators with comparisons to historical performance.
- Customer Satisfaction Score: Aggregated customer feedback displayed dynamically.

### Operational-Level Insights
- Monthly and Yearly Trend Analysis: Performance tracking over time, responding to slicer selections.
- Dynamic Bookmarking: Interactive navigation for seamless storytelling.
- DAX-Based Performance Metrics: Implementing calculated measures for in-depth analysis of sales trends.

### Advanced DAX Calculations
- Dynamic YoY Growth:
   - Executive View: Business-wide perspective ignoring slicer filters.
   - Operational View: YoY growth influenced by user-selected filters.
- Customer Satisfaction Score: Aggregating satisfaction ratings dynamically.

---

## Technologies and Tools Used
| Technology | Purpose |
|---------------|------------|
| Power BI | Data visualization and dashboard development |
| DAX (Data Analysis Expressions) | Advanced calculations and KPIs |
| Power Query | Data transformation and cleansing |
| SQL | Data extraction and preprocessing |
| Excel | Initial dataset review and structuring |

---

## Project Structure
```bash
Sales-Performance-Analysis
|-- Data          # Contains raw and cleaned data files
|-- PowerBI       # Power BI .pbix file with reports
|-- DAX           # Custom DAX scripts and calculations
|-- Screenshots   # Dashboard previews and insights
|-- README.md     # Documentation (this file)
```

## DAX Code Snippets

### YoY Growth - Executive Level
```DAX
Executive YoY% Dynamic = 
VAR _LatestYear = 
    CALCULATE( MAX( CalendarTable[Year] ), ALL( CalendarTable ) )

VAR _PreviousYear = _LatestYear - 1

VAR _Current12MonthSales = 
    CALCULATE(
        Measures_Sales[Total Sales], 
        CalendarTable[Year] = _LatestYear,
        REMOVEFILTERS( CalendarTable )
    )

VAR _Previous12MonthSales = 
    CALCULATE(
        Measures_Sales[Total Sales], 
        CalendarTable[Year] = _PreviousYear,
        REMOVEFILTERS( CalendarTable )
    )

VAR _Result =
    IF(
        NOT(ISBLANK(_Previous12MonthSales)), 
        (_Current12MonthSales - _Previous12MonthSales) / _Previous12MonthSales, 
        BLANK()
    )

RETURN _Result
```
---

## How to Use This Project
1. Clone the Repository
```bash
git clone https://github.com/hamsikachintakuntla/Sales-Performance-Analysis.git
```
2. Open Power BI and Load the .pbix File
3. Explore the Dashboard and Interact with Slicers
4. Review DAX Scripts for Advanced Insights

---

## Key Learnings and Takeaways
- Understanding YoY Analysis at both executive and operational levels
- Building Interactive Power BI Dashboards with bookmarks and storytelling
- Writing Optimized DAX Measures for business performance analysis
- Using REMOVEFILTERS vs ALL in DAX for strategic reporting

---

## Target Audience
- Data Analysts and BI Professionals - Learn how to implement advanced Power BI techniques
- Recruiters and Hiring Managers - Evaluate Power BI skills with a practical case study
- Businesses and Clients - Gain insights into sales trends and data-driven decision-making

---

## Connect With Me
- LinkedIn: [Hamsika Chintakuntla](https://www.linkedin.com/in/hamsikachintakuntla/)
- Email: chintakuntlahamsika@gmail.com

If you find this project useful, please star the repository!

---

### Final Thoughts
This project bridges the gap between executive-level and operational analytics, offering insights into how advanced Power BI dashboards can drive business decisions with data.

Looking forward to your feedback and contributions!

---

### About the Maintainer
Hamsika Chintakuntla is a Data Analyst with over 4 years of experience delivering data-driven solutions across financial services and healthcare technology. She specializes in SQL, Python, and Power BI for ETL/ELT pipelines, dashboard development, and KPI reporting. Her expertise lies in transforming complex datasets into actionable business insights through automated reporting and advanced analytics. This repository is maintained to demonstrate advanced business intelligence techniques and practical DAX applications.