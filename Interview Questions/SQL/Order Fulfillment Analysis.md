<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">

![image](https://github.com/user-attachments/assets/6ef46c24-ad2e-4390-80ba-f57db199d1c7)

**Table and Schema**
CREATE TABLE OrderStats (
    OrderID INT PRIMARY KEY,
    CustomerID INT,
    OrderStatus VARCHAR(20)
);

INSERT INTO OrderStats (OrderID, CustomerID, OrderStatus) VALUES
(1, 101, 'Fulfilled'),
(2, 102, 'Pending'),
(3, 101, 'Fulfilled'),
(4, 103, 'Fulfilled'),
(5, 102, 'Fulfilled'),
(6, 101, 'Pending'),
(7, 103, 'Fulfilled'),
(8, 103, 'Cancelled');

**SOLUTION**
```sql
WITH OrderActivity AS (
	SELECT 
		CustomerID,
		COUNT(*) AS TotalOrders,
		SUM(CASE WHEN OrderStatus = 'Fulfilled' THEN 1 ELSE 0 END) AS FulfilledOrders
		FROM OrderStats
		GROUP BY CustomerID
)
SELECT 
	CustomerID,
	ROUND((FulfilledOrders * 100) / NULLIF(TotalOrders, 0), 2) AS FulfillmentPercentage
FROM OrderActivity
ORDER BY CustomerID;
```

**OUTPUT**

<img width="1237" height="597" alt="image" src="https://github.com/user-attachments/assets/2368a6e7-8d5c-482e-8394-b7b013792755" />

