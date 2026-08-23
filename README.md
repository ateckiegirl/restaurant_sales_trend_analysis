# Restaurant Sales Trend Analysis

## Project Overview

This project analyzes daily restaurant sales data to understand sales performance, monthly trends, and changes in sales over time.

The project was developed as an end-to-end data analytics workflow, starting with manually recorded sales data in Excel, followed by an ETL process using SSIS to load the data into SQL Server, and finally importing the data into Power BI for analysis and visualization.

## Business Scenario

The restaurant records daily sales through two payment channels:

- Cash
- POS

The objective of this analysis was to transform the raw sales records into meaningful insights that could help the business understand its sales performance and identify periods of growth and decline.

## Objectives

The analysis focused on answering questions such as:

- What was the overall sales performance?
- Which month generated the highest sales?
- What was the highest sales recorded in a single day?
- How did sales change from month to month?
- Which periods experienced significant sales declines?
- What patterns could be observed in the restaurant's sales performance?

## Tools & Technologies

- Microsoft Excel
- SQL Server
- SSIS
- Power BI
- DAX

## Data Preparation & ETL

The raw sales records were initially documented manually in Excel using three columns:

- Sales Date
- Cash
- POS

The data was then processed through an SSIS ETL workflow.

The ETL process involved:

1. Extracting the Excel data.
2. Performing data conversion.
3. Loading the transformed data into SQL Server using an OLE DB Destination.
4. Validating the loaded data in SQL Server.
5. Importing the SQL Server data into Power BI.

During data validation, inconsistencies were identified in some of the recorded dates. The affected dates were corrected in the source Excel data, after which the ETL process was rerun and the SQL Server table was reloaded.

## Data Transformation in Power BI

After importing the data into Power BI, missing values in the Cash and POS columns were replaced with zero during the Power Query transformation process.

A calculated column was then created to calculate daily total sales by combining Cash and POS sales.

**Daily Total Sales = Cash + POS**

## Data Modelling

A dedicated Date table was created to support time-based analysis.

The Date table included:

- Date
- Year
- Month Number
- Month Name

The Date table was connected to the Sales table using a many-to-one relationship, with the Date table functioning as the dimension table and the Sales table functioning as the fact table.

## DAX Measures

Several DAX measures were created to support the analysis, including:

- Total Sales
- Average Daily Sales
- Highest Daily Sales
- Highest Sales Date
- Previous Month Sales
- Month-over-Month Sales Change %

The Month-over-Month Sales Change % measure was calculated using:
The Month-over-Month Sales Change % measure was calculated using:

```DAX
MOM SALES CHANGE % =
DIVIDE(
    [TOTAL SALES] - [PREVIOUS MONTH SALES],
    [PREVIOUS MONTH SALES]
)
```
## Dashboard

The final Power BI dashboard provides an overview of the restaurant's sales performance through:

- Total Sales
- Highest Daily Total
- Highest Sales Date
- Average Daily Sales
- Monthly Sales Trend
- Top 5 Months by Sales
- Month-over-Month Sales Change %

## Business Insights

### Overall Sales Performance

The restaurant recorded total sales of **₦34.43 million** during the analysis period.

### Highest Daily Sales

The highest daily sales recorded were **₦320,500**, occurring on **November 1, 2025**.

### Highest-Performing Month

**January 2026** recorded the highest monthly sales at approximately **₦5.65 million**.

### February Sales Decline

February 2026 recorded sales of approximately **₦3.22 million**, making it the lowest-performing complete month in the dataset.

Sales declined by **42.99%** compared with January.

Possible business factors that may have contributed to the decline include post-festive financial pressure, school-related expenses, reduced discretionary spending, and fasting periods.

### Month-over-Month Performance

| Month | MoM Sales Change |
|---|---:|
| November 2025 | +237.88% |
| December 2025 | +28.55% |
| January 2026 | +31.15% |
| February 2026 | -42.99% |
| March 2026 | +21.39% |
| April 2026 | +8.76% |
| May 2026 | +7.00% |
| June 2026 | -8.37% |

November recorded the highest month-over-month increase at **237.88%**. However, this result should be interpreted cautiously because October contained only partial-month sales records.

Following the significant decline in February, sales recovered in March and continued to grow through May, although the rate of growth slowed. Sales then declined again by **8.37% in June**.

## Key Takeaway

The analysis shows that restaurant sales performance varied significantly throughout the period. Sales reached their strongest level in January, experienced a substantial decline in February, recovered between March and May, and declined again in June.

The project also highlighted the importance of understanding the context and quality of the underlying data when interpreting business performance.
