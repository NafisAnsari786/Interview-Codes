<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">

![image](https://github.com/user-attachments/assets/5e8c2fb2-25d0-4112-ba95-f42c1d3f5054)

**1 SOLUTION with SELF JOIN**

```sql
WITH CustomerOrderMonths AS (
    SELECT DISTINCT 
        CustomerID,
        EXTRACT(Year FROM OrderDate) AS Year,
        EXTRACT(Month FROM OrderDate) AS Month
    FROM CustomerOrders
),
ConsecutiveOrders AS (
    SELECT c1.CustomerID
    FROM CustomerOrderMonths c1
    INNER JOIN CustomerOrderMonths c2
    ON c1.CustomerID = c2.CustomerID
    AND (
        (c1.Year = c2.Year AND c1.Month = c2.Month - 1) OR
        (c1.Year = c2.Year - 1 AND c1.Month = 12 AND c2.Month = 1)
    )
)
SELECT DISTINCT CustomerID
FROM ConsecutiveOrders;
```

**2 SOLUTION with LAG**

```sql
WITH MonthlyOrders AS (
    SELECT DISTINCT 
        CustomerID,
        DATE_TRUNC(OrderDate, MONTH) AS OrderMonth
    FROM CustomerOrders
),
MonthDiffs AS (
    SELECT 
        CustomerID,
        OrderMonth,
        LAG(OrderMonth) OVER (PARTITION BY CustomerID ORDER BY OrderMonth) AS PrevMonth
    FROM MonthlyOrders
)
SELECT DISTINCT CustomerID
FROM MonthDiffs
-- Checks if the previous order month was exactly 1 month ago
WHERE DATE_DIFF(OrderMonth, PrevMonth, MONTH) = 1;
```

**OUTPUT**

![image](https://github.com/user-attachments/assets/110474ee-7c2a-4381-a17d-ed2a229a0019)

