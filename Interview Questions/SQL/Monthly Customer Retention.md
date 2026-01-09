<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">
 
![image](https://github.com/user-attachments/assets/5d768851-c7fd-4115-8d05-cc8c2c2a18cd)

**SOLUTION 1**
```sql
WITH CustomerLag AS (
    SELECT
        CustomerID,
        Month,
        PurchaseCount,
        LAG(PurchaseCount) OVER (PARTITION BY CustomerID ORDER BY FIELD(Month, 'Jan', 'Feb', 'Mar')) AS PreviousPurchaseCount,
        LAG(Month) OVER (PARTITION BY CustomerID ORDER BY FIELD(Month, 'Jan', 'Feb', 'Mar')) AS PreviousMonth
    FROM
        CustomerPurchases
)
SELECT
    CustomerID,
    Month AS CurrentMonth,
    PreviousMonth
FROM
    CustomerLag
WHERE
    PurchaseCount > 0 AND PreviousPurchaseCount > 0;
```

**SOLUTION 2**

```sql
WITH CustStats AS (
    SELECT 
        CustomerID, 
        Month, 
        PurchaseCount AS CurrentMonthPurchase,
        LAG(PurchaseCount) OVER (
            PARTITION BY CustomerID 
            ORDER BY 
                CASE UPPER(Month)
                    WHEN 'JAN' THEN 1 WHEN 'FEB' THEN 2 WHEN 'MAR' THEN 3
                    WHEN 'APR' THEN 4 WHEN 'MAY' THEN 5 WHEN 'JUN' THEN 6
                    WHEN 'JUL' THEN 7 WHEN 'AUG' THEN 8 WHEN 'SEP' THEN 9 
                    WHEN 'OCT' THEN 10 WHEN 'NOV' THEN 11 WHEN 'DEC' THEN 12
                END
        ) AS PreviousMonthPurchase
    FROM CustomerPurchases
)
SELECT DISTINCT CustomerID
FROM CustStats
WHERE CurrentMonthPurchase > 0 
  AND PreviousMonthPurchase > 0; -- Added AND and fixed typo
```

**OUTPUT**

![image](https://github.com/user-attachments/assets/320529d2-0280-4b22-9bc7-beb0f05315fd)
