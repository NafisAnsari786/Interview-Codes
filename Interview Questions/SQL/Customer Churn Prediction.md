<img  src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

![image](https://github.com/user-attachments/assets/0b3c68cf-95d1-4eb1-90dc-545d80a30b41)

**SOLUTION**

**SOLUTION 1 FOR Months based Churn**
```sql
WITH MonthParsed AS (
	SELECT CustomerID,
	PurchaseCount,
	CAST(RIGHT(Month, 4)AS INT) AS year_num,
	CASE LEFT(Month, 3)
		WHEN 'Jan' THEN 1
		WHEN 'Feb' THEN 2
		WHEN 'Mar' THEN 3
		WHEN 'Apr' THEN 4
		WHEN 'May' THEN 5
		WHEN 'Jun' THEN 6
		WHEN 'Jul' THEN 7
		WHEN 'Aug' THEN 8
		WHEN 'Sep' THEN 9
		WHEN 'Oct' THEN 10
		WHEN 'Nov' THEN 11
		WHEN 'Dec' THEN 12
	END AS month_num
FROM CustomerPurchases
),
RankedMonths AS (
	SELECT 
		CustomerID,
		PurchaseCount,
		ROW_NUMBER() OVER (
		PARTITION BY CustomerID 
		ORDER BY year_num DESC, month_num DESC) as rn
	FROM MonthParsed
)
SELECT CustomerID
FROM RankedMonths
GROUP BY CustomerID
HAVING
	MAX(CASE WHEN rn = 1 THEN PurchaseCount END) = 0
AND MAX(CASE WHEN rn = 2 THEN PurchaseCount END) = 0
AND MAX(CASE WHEN rn >= 3 THEN PurchaseCount END) > 0;
```

**SOLUTION 2 Date based Churn If dates are given**

```sql
WITH Ranked AS (
    SELECT
        CustomerID,
        PurchaseCount,
        ROW_NUMBER() OVER (
            PARTITION BY CustomerID
            ORDER BY Date DESC
        ) AS rn
    FROM CustomerPurchases
)
SELECT CustomerID
FROM Ranked
GROUP BY CustomerID
HAVING
    MAX(CASE WHEN rn = 1 THEN PurchaseCount END) = 0
AND MAX(CASE WHEN rn = 2 THEN PurchaseCount END) = 0
AND MAX(CASE WHEN rn > 2 THEN PurchaseCount END) > 0;
```

**OUTPUT**

![image](https://github.com/user-attachments/assets/75a03816-7d6a-4489-929c-d13a144ec890)
