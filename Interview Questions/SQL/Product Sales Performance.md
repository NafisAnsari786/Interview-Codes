<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">


![image](https://github.com/user-attachments/assets/4539db3d-1001-4baf-809a-6004dc3974d0)

**Create Table & Schema**
CREATE TABLE ProductSales (
    ProductID INT PRIMARY KEY,
    Category VARCHAR(50),
    Revenue DECIMAL(10,2)
);

INSERT INTO ProductSales (ProductID, Category, Revenue) VALUES
-- Electronics
(201, 'Electronics', 5000),
(202, 'Electronics', 4000),
(205, 'Electronics', 6000),
(206, 'Electronics', 4500),
(207, 'Electronics', 5200),
(208, 'Electronics', 3000),
-- Furniture
(203, 'Furniture', 3500),
(204, 'Furniture', 2500),
(209, 'Furniture', 4200),
(210, 'Furniture', 3800),
(211, 'Furniture', 1800),
-- Clothing
(212, 'Clothing', 2200),
(213, 'Clothing', 3100),
(214, 'Clothing', 2800),
(215, 'Clothing', 1500),
-- Appliances
(216, 'Appliances', 7000),
(217, 'Appliances', 6200),
(218, 'Appliances', 5400),
(219, 'Appliances', 4800);
**SOLUTION**

```sql
WITH ProductStats AS (
	SELECT ProductID,
		Category,
		Revenue,
		DENSE_RANK() OVER (PARTITION BY Category ORDER BY Revenue DESC) AS drnk
	FROM ProductSales
)
SELECT ProductID, Category, Revenue
FROM ProductStats
WHERE drnk <= 3;
```
**OUTPUT**
![image](https://github.com/user-attachments/assets/e6f0a55a-975d-4fa6-a3b5-128d028da1e9)
