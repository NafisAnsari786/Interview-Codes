<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">

![image](https://github.com/user-attachments/assets/220817e4-1674-4e90-84e9-b7e45325d8f9)

**SOLUTION PostgreSQL**

```sql
WITH SalesWithMonthNum AS (
    SELECT ProductID, Month, Revenue,
        CASE Month 
            WHEN 'Jan' THEN 1 
            WHEN 'Feb' THEN 2 
            WHEN 'Mar' THEN 3 
        END AS MonthNum
    FROM MonthlySales
),
LaggedSales AS (
    SELECT 
        ProductID, Month, 
        Revenue AS CurrentRevenue,
        LAG(Revenue) OVER (PARTITION BY ProductID ORDER BY MonthNum) AS PreviousRevenue
    FROM SalesWithMonthNum
)
-- Combine GrowthRate and Final Select here
SELECT *,
    ROUND(((CurrentRevenue - PreviousRevenue) / NULLIF(PreviousRevenue, 0)) * 100, 2) AS GrowthPercentage
FROM LaggedSales
WHERE PreviousRevenue IS NOT NULL
ORDER BY ProductID, MonthNum;
```

**SOLUTION SQL Server**

```sql
WITH LaggedSales AS (
	SELECT ProductID,
		SalesMonth,
		Revenue AS CurrentRevenue,
		LAG(Revenue) OVER (PARTITION BY ProductID ORDER BY SalesMonth) AS PreviousRevenue
	FROM MonthlySales
),
GrowthRate AS(
	SELECT 
		ProductID,
		SalesMonth,
		CurrentRevenue,
		PreviousRevenue,
		CAST(ROUND((CurrentRevenue - PreviousRevenue) * 100.0 / NULLIF(PreviousRevenue, 0), 2) AS FLOAT) AS SalesGrowthPercentage
	FROM LaggedSales
)
SELECT 
	ProductID,
	SalesMonth,
	CurrentRevenue,
	PreviousRevenue,
	SalesGrowthPercentage
FROM GrowthRate
WHERE PreviousRevenue IS NOT NULL
ORDER BY ProductID, SalesMonth;
```

**OUTPUT**

<img width="1222" height="770" alt="image" src="https://github.com/user-attachments/assets/57a00f5d-4e62-4086-babc-a641ba77cfc2" />
