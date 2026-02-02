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
WITH TotalPurchases AS (
	SELECT 
		CustomerID,
		Region,
		SUM(PurchaseAmount) AS TotalPurchaseAmount
	FROM CustomerPurchases_2
	GROUP BY CustomerID, Region
),
RankedCustomers AS (
	SELECT CustomerID,
		Region,
		TotalPurchaseAmount,
		DENSE_RANK() OVER (PARTITION BY Region ORDER BY TotalPurchaseAmount DESC) AS drn
	FROM TotalPurchases
)
SELECT 
	CustomerID, Region, TotalPurchaseAmount
FROM RankedCustomers
WHERE drn <= 3
ORDER BY Region, TotalPurchaseAmount DESC;
```
**OUTPUT**

<img width="1227" height="743" alt="image" src="https://github.com/user-attachments/assets/d7ba4411-2043-4980-a2da-529423c89e77" />


