# Task Description: Furniture Sales Dashboard

## Project Overview
[cite_start]The **Furniture Sales Dashboard** is an interactive Excel-based analytical tool designed to visualize sales performance[cite: 26]. It enables stakeholders to analyze trends across different regions, categories, and timeframes to make data-driven business decisions.

## Objectives
* **Performance Tracking:** Monitor Key Performance Indicators (KPIs) such as total revenue, profit, and sales volume.
* **Trend Analysis:** Identify sales and profit patterns over time.
* **Regional Insights:** Compare performance across different geographical regions and product categories.
* **Operational Efficiency:** Analyze shipping durations to optimize logistics.

## Key Features
* **Interactive Visualizations:** Dynamic charts for sales and profit trends.
* **Filter Capabilities:** Slicers for date, product category, and region to allow deep-dive analysis.
* **KPI Cards:** Real-time summary of essential business metrics.
* **Automated Workflow:** Data processing powered by Power Query for consistency and accuracy.

## Data Cleaning & Transformation (Power Query)
To ensure data integrity, the following steps were performed in Power Query:
1. **Format Standardization:** Changed 'Order Date' and 'Ship Date' to proper Date formats.
2. **Locale Adjustment:** Resolved regional errors by switching system locale to English (United States).
3. **Data Reduction:** Removed irrelevant columns to focus on analytical value.
4. **Feature Engineering:** - Added a **Duration** column (Ship Date - Order Date) to calculate shipping time.
   - Created a **Month** column using three-letter suffixes (e.g., Jan, Feb).
5. **Financial Accuracy:** Converted the **Profit** column to Currency format.

## Visual Documentation
* **Data Transformation Process:** [Power Query Screenshot](https://github.com/Yousef-7ossam/Furniture-Sales-Dashboard/blob/main/Power%20Query.png)
* **Final Dashboard Layout:** [Dashboard Screenshot](https://github.com/Yousef-7ossam/Furniture-Sales-Dashboard/blob/main/Dashboard.png)
