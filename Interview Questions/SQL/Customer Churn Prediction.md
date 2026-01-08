<img  src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

![image](https://github.com/user-attachments/assets/0b3c68cf-95d1-4eb1-90dc-545d80a30b41)

**SOLUTION**

**SOLUTION 1 FOR Months based Churn**
```sql
WITH MonthOrdered AS (
    SELECT
        CustomerID,
        Month,
        PurchaseCount,
        CASE UPPER(Month)
            WHEN 'JAN' THEN 1
            WHEN 'FEB' THEN 2
            WHEN 'MAR' THEN 3
            WHEN 'APR' THEN 4
            WHEN 'MAY' THEN 5
            WHEN 'JUN' THEN 6
            WHEN 'JUL' THEN 7
            WHEN 'AUG' THEN 8
            WHEN 'SEP' THEN 9
            WHEN 'OCT' THEN 10
            WHEN 'NOV' THEN 11
            WHEN 'DEC' THEN 12
        END AS month_num
    FROM CustomerPurchases
),
RankedMonths AS (
    SELECT
        CustomerID,
        PurchaseCount,
        ROW_NUMBER() OVER (
            PARTITION BY CustomerID
            ORDER BY month_num DESC
        ) AS rn
    FROM MonthOrdered
)
SELECT CustomerID
FROM RankedMonths
GROUP BY CustomerID
HAVING
    MAX(CASE WHEN rn = 1 THEN PurchaseCount END) = 0
AND MAX(CASE WHEN rn = 2 THEN PurchaseCount END) = 0
AND MAX(CASE WHEN rn >= 3 THEN PurchaseCount END) > 0;
```

**SOLUTION 2 Date based Churn**

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
