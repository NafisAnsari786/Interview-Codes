<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">

![image](https://github.com/user-attachments/assets/220817e4-1674-4e90-84e9-b7e45325d8f9)

**SOLUTION**

```sql
WITH SalesWithMonthNum AS (
    SELECT 
        ProductID,
        Month,
        Revenue,
        CASE Month
            WHEN 'Jan' THEN 1
            WHEN 'Feb' THEN 2
            WHEN 'Mar' THEN 3
        END AS MonthNum
    FROM MonthlySales
),
LaggedSales AS (
    SELECT 
        ProductID, 
        Month, 
        Revenue AS CurrentRevenue,
        LAG(Revenue) OVER (
            PARTITION BY ProductID 
            ORDER BY MonthNum
        ) AS PreviousRevenue
    FROM SalesWithMonthNum
),
GrowthRate AS (
    SELECT 
        ProductID,
        Month,
        CurrentRevenue, 
        PreviousRevenue,
        ROUND(
            ((CurrentRevenue - PreviousRevenue) / NULLIF(PreviousRevenue, 0)) * 100, 
            2
        ) AS GrowthPercentage
    FROM LaggedSales
    WHERE PreviousRevenue IS NOT NULL
)
SELECT 
    ProductID,
    Month,
    CurrentRevenue,
    PreviousRevenue,
    GrowthPercentage
FROM GrowthRate
ORDER BY ProductID, Month;

```

**OUTPUT**

![image](https://github.com/user-attachments/assets/7a7d76d3-f32d-4a85-bd86-bf8b052200c7)
