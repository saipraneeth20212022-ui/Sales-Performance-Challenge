# Sales-Performance-Challenge
A regional sales company operating across 3 regions (Central, North, South) needed a comprehensive business intelligence solution to replace their manual, spreadsheet-based reporting process. The Sales Manager required a clear, non-technical dashboard to present business performance during monthly leadership reviews.
Problem Statement
The company faced several challenges:

No clear view of Year-over-Year business performance
Unable to track Regional Manager performance against category targets
High product return rates with no visibility into root causes
Delivery delays affecting customer satisfaction with no monitoring system
Manual reporting scattered across multiple spreadsheets


Solution
Built a 5-page interactive Power BI dashboard that transforms raw sales data into actionable business insights.

Dataset
TableRowsDescriptionOrders (2015-2018)10,000Core transaction dataPeople3Regional Manager mappingReturns637Returned order recordsTarget15Category-wise annual targets

Data Preparation
Challenges Solved

Excel serial number date conversion using Power Query M formula
Word-based quantity values (one, two, six) replaced with numeric values in order_2016
Composite key Category_Year created to establish Target relationship
All 4 order files appended into single Orders table (10,000 rows)
Date Table created for time intelligence calculations

New Columns Added

Year — extracted from Order Date
Delivery Days — Ship Date minus Order Date
Category_Year — composite key for Target relationship
Month Number — for correct month sorting


Data Model
RelationshipTypeOrders → People (Region)Many to OneOrders → Target (Category_Year)Many to OneOrders → Date Table (Order Date)Many to OneOrders → ReturnsNo direct relationship — handled via DAX

DAX Measures Created (23 Measures)
Core Measures

Total Sales, Total Profit, Total Orders, Profit Margin %

Year-over-Year

Sales LY, Sales YoY %, Profit LY, Profit YoY %, Orders LY, Orders YoY %

Target Achievement

Total Target, Target Achievement %, Target Gap, Target Status

Returns

Returned Orders, Return Rate %, Return Rate LY, Return Rate YoY

Delivery

Avg Delivery Days, Delayed Orders, Delay Rate %, Delay Rate LY, Delay Rate YoY


Dashboard Pages
Page 1 — Business Overview
High level KPI cards showing Total Sales, Profit, Orders, Margin, Return Rate and Delivery Days with YoY comparison. Sales growth by year bar chart and Sales vs Target by category comparison.
Page 2 — Regional Performance
Sales and Profit by Region, Manager Performance Summary table, Sales by Region and Category breakdown, Regional YoY comparison.
Page 3 — Target Achievement
Manager × Category matrix with conditional formatting (Green = achieved, Red = missed), Sales vs Target by category, Target Achievement % by category, detailed target gap table.
Page 4 — Returns Analysis
Return rate KPIs with YoY, Return rate by Region, Category and Ship Mode with conditional formatting, Manager-wise returns summary table.
Page 5 — Delivery Delays
Delivery KPIs, Avg delivery days by Ship Mode, Delay rate by Region and Category, Manager-wise delay summary with conditional formatting.

Key Business Insights

Business grew 27.5% in sales and 24.6% in profit in 2018 vs 2017
All 3 categories exceeded targets in 2018 — Technology leading at 229.5%
Central region has highest return rate at 21.2% — requires attention
Return rate decreased 2.3% YoY — positive trend
Standard Class shipping has highest avg delivery days at 5 days
Emily Burns (Central) achieved highest sales at £597K in 2018


Technical Stack

Tool: Microsoft Power BI Desktop
Data Source: CSV files
Query Language: Power Query M
Calculation Language: DAX
Visuals Used: KPI Cards, Clustered Bar Charts, Matrix, Line Chart, Table, Slicer


Key Decisions Made

Returns handled via DAX instead of direct relationship due to duplicate Order IDs
Composite key approach used for Target table instead of separate relationships
Delivery delay threshold set at 5 days based on Standard Class average
Target measures filtered by MAX year to work correctly with slicer
DISTINCTCOUNT used for Returned Orders to avoid duplicate counting
AVERAGEX with SUMMARIZE used for Avg Delivery Days to avoid duplicate order counting
