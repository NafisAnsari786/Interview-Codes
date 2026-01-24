<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">

![image](https://github.com/user-attachments/assets/1435a674-a3dd-4eeb-8248-2f76e1d3b019)

**Table Schema**
CREATE TABLE SalesData (
    ProductID INT PRIMARY KEY,
    ProductName VARCHAR(50),
    SaleDate DATE,
    QuantitySold INT,
    Revenue DECIMAL(10,2)
);

INSERT INTO SalesData (ProductID, ProductName, SaleDate, QuantitySold, Revenue) VALUES
(1, 'Widget A', '2023-11-01', 150, 3000),
(2, 'Widget B', '2023-11-01', 200, 4000),
(3, 'Widget C', '2023-11-01', 180, 3600),
(4, 'Widget D', '2023-11-01', 250, 5000),
(5, 'Widget E', '2023-11-01', 100, 2000);
**SOLUTION**

```SQL
WITH TopProducts AS (
	SELECT 
		ProductID, QuantitySold,
		Revenue,
		DENSE_RANK() OVER (ORDER BY Revenue DESC) AS drnk
	FROM SalesData
)
SELECT	ProductID, QuantitySOld, Revenue
FROM TopProducts
WHERE drnk <= 3;
```

<img width="867" height="562" alt="image" src="https://github.com/user-attachments/assets/37b0f9e2-baf6-4bd0-bff2-709f42bd745d" />
