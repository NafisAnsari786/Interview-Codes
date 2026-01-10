<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">

![image](https://github.com/user-attachments/assets/71c23611-e6a8-4f46-8728-091c1ec030e9)

**SOLUTION**
```SQL
WITH CustomerTotals AS (
    -- Step 1: Sum the purchases for each customer per region
    SELECT 
        Region, 
        CustomerID, 
        SUM(PurchaseAmount) AS Total_PurchaseAmount
    FROM CustomerPurchases
    GROUP BY Region, CustomerID
),
RankedCustomers AS (
    -- Step 2: Rank customers based on their total spend
    SELECT 
        Region, 
        CustomerID, 
        Total_PurchaseAmount,
        ROW_NUMBER() OVER (PARTITION BY Region ORDER BY Total_PurchaseAmount DESC) AS rownum
    FROM CustomerTotals
)
-- Step 3: Select the top 3 per region
SELECT 
    Region, 
    CustomerID, 
    Total_PurchaseAmount
FROM RankedCustomers
WHERE rownum <= 3
ORDER BY Region, Total_PurchaseAmount DESC;
```
**OUTPUT**

![image](https://github.com/user-attachments/assets/c604b273-1458-46bc-aa76-671c6afaf0b8)

