<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">

![image](https://github.com/user-attachments/assets/6ef46c24-ad2e-4390-80ba-f57db199d1c7)

**SOLUTION**
```sql
WITH OrderStats AS (
    SELECT 
        CustomerID,
        COUNT(*) AS TotalOrders,
        SUM(CASE WHEN OrderStatus = 'Fulfilled' THEN 1 ELSE 0 END) AS FulfilledOrders
    FROM Orders
    GROUP BY CustomerID
)
SELECT 
    CustomerID,
    ROUND((FulfilledOrders * 100.0) / TotalOrders, 2) AS FulfillmentPercentage
FROM OrderStats
ORDER BY CustomerID;

```

**OUTPUT**

![image](https://github.com/user-attachments/assets/7468dc30-a4a1-4b5c-8913-6aefaf536045)
