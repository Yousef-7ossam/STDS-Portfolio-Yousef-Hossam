# Task Description: Furniture Sales Dashboard

## Project Overview
The **Furniture Sales Dashboard** is an interactive Excel-based analytical tool designed to visualize sales performance. It enables stakeholders to analyze trends across different regions, categories, and timeframes to make data-driven business decisions.

## Objectives
* **Performance Tracking:** Monitor Key Performance Indicators (KPIs) such as total revenue, profit, and sales volume.
* **Trend Analysis:** Identify sales and profit patterns over time.
* **Regional Insights:** Compare performance across different geographical regions.

## 1. Data Cleaning & Transformation (Power Query)
To ensure data integrity, the following steps were performed in Power Query:
* **Format Standardization:** Changed 'Order Date' and 'Ship Date' to proper Date formats.
* **Locale Adjustment:** Resolved regional errors by switching system locale to English (United States).
* **Feature Engineering:** Added a **Duration** column and a **Month** column for better time-series analysis.

**Power Query Transformation Process:**
![Power Query Steps](image%20Dashboard/Power%20Query.png)

## 2. Data Analysis (Pivot Tables)
Using Excel Pivot Tables, the data was summarized to uncover insights regarding:
* Total Sales and Profit by Category.
* Monthly performance trends.
* Geographic distribution of sales.



**Data Analysis & Pivot Tables:**
![Pivot Tables](image%20Dashboard/pivot%20tables.png)




## 3. Final Interactive Dashboard
The final dashboard provides a professional layout for easy navigation and decision-making, featuring dynamic filters and KPI cards.

**Final Dashboard Layout:**
![Dashboard Overview](image%20Dashboard/Dashboard.png)

## Key Features
* **Interactive Visualizations:** Dynamic charts for sales and profit trends.
* **Dynamic Slicers:** Filters for date, product category, and region.
* **Automated Workflow:** Data processing powered by Power Query.
