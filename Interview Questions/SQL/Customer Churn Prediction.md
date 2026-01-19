<img  src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

![image](https://github.com/user-attachments/assets/0b3c68cf-95d1-4eb1-90dc-545d80a30b41)

CREATE TABLE CustomerPurchases (
    CustomerID INT,
    [Month] VARCHAR(20),
    PurchaseCount INT
);

INSERT INTO CustomerPurchases (CustomerID, [Month], PurchaseCount) VALUES
(401, 'Nov-2025', 4),
(401, 'Dec-2025', 3),
(401, 'Jan-2026', 2),
(401, 'Feb-2026', 0),
(401, 'Mar-2026', 0),

(402, 'Nov-2025', 2),
(402, 'Dec-2025', 1),
(402, 'Jan-2026', 0),
(402, 'Feb-2026', 0),
(402, 'Mar-2026', 0),

(403, 'Nov-2025', 5),
(403, 'Dec-2025', 4),
(403, 'Jan-2026', 3),
(403, 'Feb-2026', 2),
(403, 'Mar-2026', 1),

(404, 'Nov-2025', 1),
(404, 'Dec-2025', 0),
(404, 'Jan-2026', 0),
(404, 'Feb-2026', 0),
(404, 'Mar-2026', 0);
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

<img width="1230" height="763" alt="image" src="https://github.com/user-attachments/assets/a6687486-7110-4900-bc45-f85ea5f04a87" />

