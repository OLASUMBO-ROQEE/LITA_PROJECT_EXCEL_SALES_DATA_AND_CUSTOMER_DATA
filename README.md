# LITA_PROJECT_EXCEL_SALES_DATA
This is where I documented my first project while learning data analysis with the incubator hub. This contain of data analysis of sales and customer data using excel
### Project Title: Sales Data.

[Project Overview](project-overview)

Data Sources

Tools used

Data cleaning and preparation

### Project Overview
---
This Data Analysis Project aims to generate insight into the sales performance of the sales data project over the years. By analysing the various parameters in the data received, we seek to gather enough insight to make reasonable decisions which will enable us to tell compeling stories around our data from the insight gotten and to know the best performance from our data.

### Data Sources
---
The primary source of data used here is sales data from The Incubator Hub Lita Project.

### Tools Used
---
- Microsoft Excel [Download here](https://www.microsoft.com)
  1. Data cleaning
  2.  Analysis
  3.  For Data Visualization.
-SQL
- PowerBi
  
     
- Github for portfolio building.

### Data cleaning and preparations
---
In the initial phase of the data cleaning and preparations, we performed the following action
1. Data Loading and Inspection.
2. Handling missing variables.
3. Data cleaning and formatting.

### Exploratory Data Analysis
---
EDA involves the exploring of the data to answer some questions about the data such as :
- What is the average sales per product?
- What is the total sales per product,region and month?
- What is the total revenue by region?

### Data Analysis
---
This is where we include some basic class of codes or the DAX expressions used during your analysis.
```SQL
SELECT 
    Product, 
    SUM(Quantity * UnitPrice) AS TotalSales
FROM 
    [dbo].[LITA capstone dataset]
GROUP BY 
    Product
SELECT 
    Region, 
    COUNT(OrderID) AS TransactionCount
FROM 
    [dbo].[LITA capstone dataset]
GROUP BY 
    Region
SELECT TOP 1 
    Product, 
    SUM(Quantity * UnitPrice) AS TotalSales
FROM 
    [dbo].[LITA capstone dataset]
GROUP BY 
    Product
ORDER BY 
    TotalSales DESC
SELECT 
    Product, 
    SUM(Quantity * UnitPrice) AS TotalRevenue
FROM 
    [dbo].[LITA capstone dataset]
GROUP BY 
    Product
SELECT 
    YEAR(OrderDate) AS Year, 
    MONTH(OrderDate) AS Month, 
    SUM(Quantity * UnitPrice) AS MonthlySales
FROM 
    [dbo].[LITA capstone dataset]
WHERE 
    YEAR(OrderDate) = YEAR(GETDATE())
GROUP BY 
    YEAR(OrderDate), MONTH(OrderDate)
ORDER BY 
    Month
SELECT TOP 5 
    CustomerID, 
    SUM(Quantity * UnitPrice) AS TotalPurchase
FROM 
    [dbo].[LITA capstone dataset]
GROUP BY 
    CustomerID
ORDER BY 
    TotalPurchase DESC
WITH RegionSales AS (
    SELECT 
        Region, 
        SUM(Quantity * UnitPrice) AS TotalSales
    FROM 
        [dbo].[LITA capstone dataset]
    GROUP BY 
        Region
), TotalSales AS (
    SELECT SUM(TotalSales) AS GrandTotal FROM RegionSales
)
SELECT 
    RS.Region, 
    RS.TotalSales, 
    (RS.TotalSales * 100.0 / TS.GrandTotal) AS SalesPercentage
FROM 
    RegionSales RS, TotalSales TS
SELECT 
    DISTINCT Product
FROM 
    [dbo].[LITA capstone data]
WHERE 
    Product NOT IN (
        SELECT Product
        FROM [dbo].[LITA capstone data]
        WHERE OrderDate >= DATEADD(QUARTER, -1, GETDATE())
    )
```






### Data Visualisation
---

![Screenshot 2024-11-03 225244](https://github.com/user-attachments/assets/2497a767-d6ae-445d-a4a6-817c5c005166)


![Screenshot 2024-11-03 223534](https://github.com/user-attachments/assets/dc04f4ae-a7ec-4809-9839-dd718dc29df7)

![Screenshot 2024-11-04 212541](https://github.com/user-attachments/assets/0f26007b-4bbf-4d7d-9312-a59501b3609b)
