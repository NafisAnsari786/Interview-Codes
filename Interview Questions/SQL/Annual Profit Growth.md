<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

![image](https://github.com/user-attachments/assets/8e96c929-acc2-40da-8d83-c5a3a3f3330e)

**SOLUTION**
```sql
WITH ProfitData AS (
	SELECT 
		Year,
		(Revenue - Expenses) AS Profit
		FROM AnnualProfits
),
GrowthData AS (
	SELECT 
	Year, Profit,
	LAG(Profit) OVER (ORDER BY Year) AS PreviousYearProfit
	FROM ProfitData
)
SELECT 
	Year, Profit, PreviousYearProfit,
	ROUND((Profit - PreviousYearProfit) * 100/ NULLIF(PreviousYearProfit, 0),2) AS YoYProfitGrowthPercentage
	FROM GrowthData;
```

**OUTPUT**

![image](https://github.com/user-attachments/assets/1c7d671c-1919-41de-9556-7ca1a07c3a74)

