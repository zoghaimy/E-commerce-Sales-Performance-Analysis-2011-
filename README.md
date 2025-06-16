# E-commerce Sales Performance Analysis (2011)

## Project Overview

This project involved a comprehensive analysis of a transactional dataset from an online retail company in 2011. The primary goal was to transform raw sales data into actionable business intelligence, providing insights into sales trends, customer behavior, and product performance to inform strategic decision-making.

## Problem Statement

The objective was to derive meaningful insights from raw e-commerce transaction data to answer critical business questions, such as:
- What are the key sales trends over time (monthly, daily, hourly)?
- Which geographical regions are driving sales?
- What are the characteristics of high-value products and customers?
- Are there any anomalies or patterns in customer shopping behavior that can be leveraged?

## Dataset

The analysis utilizes the `Online Retail.xlsx` dataset, containing transactional data for a UK-based online retail store from 01/12/2010 to 09/12/2011. The dataset includes information on invoices, stock codes, product descriptions, quantities, unit prices, customer IDs, and countries.

## Tools and Technologies

* **Database Management:** Microsoft SQL Server (SSMS)
* **Data Analysis & Visualization:** Microsoft Power BI Desktop
* **Documentation:** Microsoft Excel, PDF

## Key Actions and Steps Taken (Methodology)

This project followed a robust data analysis pipeline, from raw data to actionable insights:

1.  **Data Acquisition & Ingestion:**
    * The raw `Online Retail.xlsx` data was meticulously imported into a dedicated SQL Server database.

2.  **Data Cleansing & Transformation (SQL First Approach):**
    * **Identified and resolved critical data type mismatches:** Addressed persistent errors during import related to `Quantity` (from `smallint` overflow to `INT`) and `UnitPrice` (from `float` to `DECIMAL(18,4)`) to ensure data integrity.
    * **Handled missing values:** Replaced `NULL` `CustomerID` entries with `0` to categorize anonymous transactions, preventing data loss for valuable sales data.
    * **Filtered invalid records:** Removed transactions with non-positive `Quantity` or `UnitPrice` (e.g., returns, erroneous entries) to focus on genuine sales.
    * **Created calculated measures:** Derived `SalesAmount` (`Quantity * UnitPrice`) directly in SQL for robust calculations.

3.  **Feature Engineering (SQL Server):**
    * Enriched the dataset by extracting and creating new analytical features from existing columns, including:
        * `InvoiceMonth`: Month of transaction for seasonal analysis.
        * `HourOfDay`: Hour of transaction for hourly traffic patterns.
        * `InvoiceDayOfWeek`: Day of the week for daily shopping habits.
        * `DayType`: Categorized days as 'Weekday' or 'Weekend'.

4.  **Data Modeling & Dashboard Design (Power BI):**
    * Connected Power BI Desktop to the cleaned and transformed SQL Server database.
    * Designed an intuitive and interactive dashboard to visualize key performance indicators and trends.

5.  **Advanced Analysis & Insights (Power BI - DAX):**
    * Developed sophisticated DAX measures, such as `Average Order Value` and `Total Unique Customers`, to gain deeper insights into customer spending.
    * Performed preliminary customer segmentation to identify top-value customers.

## Key Findings and Business Insights

The analysis yielded several critical insights for the e-commerce business:

* **Strong Seasonal Peaks:** Sales exhibited significant seasonality, with the **highest revenue generated in November**, followed closely by September and October, indicating a strong influence of Q4 and holiday shopping periods.
* **UK Market Dominance:** The **United Kingdom accounted for approximately 84% of total sales**, establishing it as the primary market and revenue driver.
* **Consistent Weekday Shopping Patterns:** The majority of sales occurred on **weekdays**, with peak shopping activity consistently observed between **09:00 AM and 03:00 PM**.
* **Curious Weekend Anomaly:** A notable observation was the **complete absence of sales on Saturdays**, with all weekend sales occurring on Sundays. This warrants further investigation into operational procedures or data collection methods.
* **High-Value Products Identified:** Beyond standard products, "DotCom Postage" (shipping charges) was a significant revenue contributor. Furthermore, specific product StockCodes (e.g., 'B', 'AMAZONFEE', 'DOT') were identified as **high-value items** due to their high average unit prices, generating substantial revenue despite potentially lower quantities sold.
* **Customer Engagement Gaps:** While the business had `4,239` unique customers overall, only `2,561` (~60%) were active in the last three months of the analysis period, indicating an opportunity for customer re-engagement.
* **Top-Tier Customers:** Specific customer IDs (`17846`, `16742`, `15802`, and `15098`) were identified as the highest-value customers, consistently contributing the most revenue.

## Recommendations

Based on the analysis, the following recommendations are proposed to optimize business strategies:

* **Optimize for Peak Seasons:** Align marketing campaigns, inventory management, and operational resources to capitalize on the strong Q4 sales period.
* **Focus on Core Market:** Continue to refine strategies for the dominant UK market while evaluating opportunities for targeted, data-driven expansion into other promising regions.
* **Enhance Operational Efficiency:** Align customer support and fulfillment staffing with identified peak shopping hours (09:00-15:00).
* **Investigate Saturday Sales Anomaly:** Conduct a root cause analysis to understand the absence of Saturday sales. This could uncover valuable insights into operational models or data capture issues.
* **Strategic Product Management:** Analyze the profitability of "DotCom Postage" and develop strategies to promote and potentially upsell high-value, high-unit-price products to suitable customer segments.
* **Implement Customer Lifecycle Management:** Develop targeted re-engagement campaigns for inactive customers and establish loyalty programs or personalized outreach for top-tier customers to foster continued retention.

## Dashboard Snapshot

Below is a snapshot of the Power BI dashboard created for this project:

![Online Retail Dashboard](PowerBI_Report/Online_Retail_Dashboard.png)

## Full Project Report

For a more detailed breakdown of the analysis, methodology, and findings, please refer to the full project report:

[Project Report](Documentation/Project_Report.pdf)

---
