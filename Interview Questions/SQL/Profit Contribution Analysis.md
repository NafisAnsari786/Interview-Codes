<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

![image](https://github.com/user-attachments/assets/3982ed5a-083b-43d4-9900-7517365963c8)

**Table & Schema**
CREATE TABLE CategoryProfit (
    Category VARCHAR(50),
    Revenue INT,
    Cost INT
);

INSERT INTO CategoryProfit (Category, Revenue, Cost) VALUES
-- Electronics
('Electronics', 50000, 30000),
('Electronics', 42000, 25000),
('Electronics', 38000, 22000),
-- Furniture
('Furniture', 30000, 15000),
('Furniture', 28000, 14000),
('Furniture', 26000, 13000),
-- Clothing
('Clothing', 20000, 5000),
('Clothing', 18000, 6000),
('Clothing', 16000, 4000);

**SOLUTION**
```sql
WITH ProfitData AS (
	SELECT Category,
		SUM(Revenue - Cost) AS TotalProfit
	FROM CategoryProfit
	GROUP BY Category
)
SELECT 
	Category,
	TotalProfit,
	CAST(ROUND(TotalProfit * 100.0 / NULLIF(SUM(TotalProfit) OVER (), 0), 2)AS FLOAT) AS ProfitContributionPercentage
FROM ProfitData
ORDER BY ProfitContributionPercentage DESC;
```

**OUTPUT**

<img width="1468" height="492" alt="image" src="https://github.com/user-attachments/assets/2a225a8c-4708-40ab-945c-e68d896784a4" />

