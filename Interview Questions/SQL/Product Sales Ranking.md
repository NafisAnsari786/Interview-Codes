<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

![image](https://github.com/user-attachments/assets/15c82ead-de44-4add-bf76-6a9057a63a19)
**Create Table and Schema**
CREATE TABLE ProductSales2 (
    ProductID INT PRIMARY KEY,
    Category VARCHAR(50),
    Sales INT
);

INSERT INTO ProductSales2 (ProductID, Category, Sales) VALUES
-- Electronics
(201, 'Electronics', 5000),
(202, 'Electronics', 7000),
(203, 'Electronics', 7000),
(204, 'Electronics', 3000),
-- Furniture
(205, 'Furniture', 6000),
(206, 'Furniture', 4500),
(207, 'Furniture', 6000),
(208, 'Furniture', 2000),
-- Clothing
(209, 'Clothing', 2500),
(210, 'Clothing', 4000),
(211, 'Clothing', 4000),
(212, 'Clothing', 1500);


**SOLUTION**
```sql
WITH TopProducts AS (
	SELECT ProductID,
		Category,
		Sales,
		DENSE_RANK() OVER (PARTITION BY Category ORDER BY Sales DESC) AS drnk
	FROM ProductSales2
		
)
SELECT ProductID, Category, Sales
FROM TopProducts
WHERE drnk <= 3;
```

**OUTPUT**

<img width="1002" height="628" alt="image" src="https://github.com/user-attachments/assets/615cdaa3-e0de-4803-9885-3f3f73c97306" />

