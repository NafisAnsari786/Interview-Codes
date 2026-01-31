<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">

![image](https://github.com/user-attachments/assets/cdc1b35f-ec1b-4c8c-8596-0cbd1486ac33)


**SOLUTION**
```sql
WITH LaggedSales AS (
	SELECT 
		SalesMonth, 
		TotalSales,
		LAG(TotalSales) OVER (ORDER BY SalesMonth) AS PreviousMonthSales
	FROM MonthlySales
)
SELECT 
	SalesMonth, 
	TotalSales,
	PreviousMonthSales,
	ROUND(CAST(
		(TotalSales - PreviousMonthSales) * 100.0 / NULLIF(PreviousMonthSales, 0) 
		AS FLOAT),2) AS MoMGrowthPercentage
FROM LaggedSales;
```

**OUTPUT**

<img width="1088" height="706" alt="image" src="https://github.com/user-attachments/assets/e25791f6-86b6-4e44-a837-96d456212d5d" />


