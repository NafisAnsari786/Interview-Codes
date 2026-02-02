<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">

![image](https://github.com/user-attachments/assets/71c23611-e6a8-4f46-8728-091c1ec030e9)

**Create Table & Schema**

CREATE TABLE CustomerPurchases_2 (
    CustomerID VARCHAR(10),
    Region VARCHAR(20),
    PurchaseAmount INT
);

INSERT INTO CustomerPurchases_2 (CustomerID, Region, PurchaseAmount) VALUES
('C001', 'North', 500),
('C001', 'North', 400),
('C002', 'South', 700),
('C002', 'South', 300),
('C003', 'North', 300),
('C003', 'North', 200),
('C004', 'East', 800),
('C004', 'East', 150),
('C005', 'South', 600),
('C005', 'South', 250),
('C006', 'East', 900),
('C007', 'North', 650);

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

<img width="1227" height="743" alt="image" src="https://github.com/user-attachments/assets/d7ba4411-2043-4980-a2da-529423c89e77" />


