<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

![image](https://github.com/user-attachments/assets/8e96c929-acc2-40da-8d83-c5a3a3f3330e)

**Table Schema**
CREATE TABLE AnnualProfits (
    [Year] INT PRIMARY KEY,
    Revenue INT,
    Expenses INT
);

INSERT INTO AnnualProfits ([Year], Revenue, Expenses) VALUES
(2017, 120000, 80000),
(2018, 135000, 90000),
(2019, 150000, 100000),
(2020, 140000, 95000),     -- slight dip (COVID-like scenario)
(2021, 160000, 105000),
(2022, 175000, 115000),
(2023, 180000, 110000),
(2024, 220000, 135000),
(2025, 270000, 160000),
(2026, 310000, 185000);

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

<img width="1382" height="727" alt="image" src="https://github.com/user-attachments/assets/3e30b3fb-7a8f-429f-b1d1-c3f32bd25777" />


