# SSIS ETL Process

SQL Server Integration Services (SSIS) was used to extract, transform, and load the restaurant sales data from Excel into SQL Server.

## ETL Workflow

The ETL process followed these steps:

**Excel Source → Data Conversion → OLE DB Destination (SQL Server)**

### 1. Extract

The manually recorded daily restaurant sales data was first entered into Microsoft Excel.

The dataset contained:

- Sales Date
- POS
- Cash

The Excel file was used as the source for the SSIS package.

### 2. Transform

A Data Conversion transformation was used to convert the source fields into appropriate data types before loading the data into SQL Server.

### 3. Load

The transformed data was loaded into SQL Server using an OLE DB Destination.

The destination table was created in the `TRENDS` database and used as the source for subsequent analysis in Power BI.

## SSIS Package

The SSIS package used for this project is included in this folder.

The package demonstrates the ETL workflow used to move the sales data from Excel into SQL Server.
