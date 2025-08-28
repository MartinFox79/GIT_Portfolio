# Bike Store Sales Dashboard

This interactive Power BI dashboard provides a comprehensive analysis of sales, products, and customer behavior in a fictional bike store. The report is structured into four main pages and allows users to explore key business metrics through intuitive, visually-rich insights.

## Project Files

- `BikeStore_Dashboard.pbix` – Power BI report file
- `Sales.csv` / `Sales.xlsx` – raw data source files

## Report Pages Overview
[Click here to view the full Power BI project](https://app.powerbi.com/view?r=eyJrIjoiN2I3N2ZjNTktNGNjYy00OGQ2LTlkODQtYzEzMmRiODRjZTQ1IiwidCI6IjNkZmU5YWI2LTgxYmYtNDkxYy1iNjcwLTAxYzgyNGEwOWUxOSJ9&embedImagePlaceholder=true&pageName=ReportSectiondce9cebadc024080661c)


### 1. Landing Page
A simple navigation interface where users can choose between the main analytical sections:
- Sales
- Products
- Customers

### 2. Sales Overview
Analyzes overall sales performance.

**Visuals**:
- Total Revenue
- Sales Growth Rate
- Average Order Value
- Revenue Over Time
- Revenue by Age Group
- Sales by Product Category
- Top 5 Best Selling Products

### 3. Product Overview
Focuses on selected product performance over time and across customer segments.

**Visuals**:
- Product Revenue Trend
- Revenue by Age Group
- Product Subcategory Performance

### 4. Customers Overview
Highlights customer demographics and distribution by region.

**Visuals**:
- Revenue by Country
- Profit per Customer
- Revenue Over Time
- Gender Distribution
- Age Group Distribution
- Customers by Country

## Data Model

### Tables Used

| Table Name        | Description                                                                 |
|-------------------|-----------------------------------------------------------------------------|
| `Sales`           | Main fact table containing transaction-level sales data                     |
| `Products`        | Dimension table with product details (category, subcategory, name, size)    |
| `Customers`       | Customer demographic data (age, gender, country)                            |
| `Date`            | Calendar table with full date hierarchy used for time-based analysis        |
| `Countries`       | Lookup table for standardizing country names and mapping regional data      |

### Relationships

- `Sales[Product ID]` → `Products[Product ID]` (Many-to-One)
- `Sales[Customer ID]` → `Customers[Customer ID]` (Many-to-One)
- `Sales[Order Date]` → `Date[Date]` (Many-to-One)
- `Customers[Country]` → `Countries[Country]` (Many-to-One)

All relationships are single-directional and enforced.

## Key DAX Measures

| Measure Name               | DAX Formula                                                                                  | Description                                      |
|----------------------------|-----------------------------------------------------------------------------------------------|--------------------------------------------------|
| Total Sales Revenue        | `SUM(Sales[Revenue])`                                                                         | Total revenue from all transactions              |
| Sales Growth Rate          | `( [Total Sales Revenue] - [Previous Period Revenue] ) / [Previous Period Revenue]`          | Growth vs previous time period                   |
| Average Order Value        | `AVERAGE(Sales[Revenue])`                                                                    | Average value of a single order                  |
| Profit per Customer        | `[Total Sales Revenue] / DISTINCTCOUNT(Sales[Customer ID])`                                 | Average profit per unique customer               |
| Previous Period Revenue    | `CALCULATE([Total Sales Revenue], DATEADD('Date'[Date], -1, YEAR))`                         | Revenue in the previous year                     |

> Note: All measures use properly defined relationships and the date table to ensure correct time intelligence.

## Data Transformation

Data was loaded and cleaned in Power Query before entering the data model. Key steps included:
- Removing null and duplicate records
- Changing data types for consistency
- Creating calculated columns (e.g., age groups)
- Filtering out irrelevant product categories or incomplete transactions

## Technologies Used

- Power BI Desktop (data modeling and report building)
- Power Query (ETL and data shaping)
- DAX (metrics and KPIs)
- Excel/CSV as data source

## Interactivity

The report includes the following interactive features:
- Date slicer with range selection
- Product and category filters
- Country-based segmentation
- Dynamic visuals reacting to user selections

## Business Applications

This dashboard can support:
- Sales trend analysis
- Target customer group identification
- Product performance tracking
- Regional strategy development

## Summary

The Bike Store Sales Dashboard demonstrates how structured data and visual storytelling can drive better business decisions. It integrates multiple data sources into a cohesive reporting solution that is easy to explore and adapt to specific business questions.
