

![image](https://github.com/user-attachments/assets/5e8c2fb2-25d0-4112-ba95-f42c1d3f5054)

CREATE TABLE CustomerOrders (
    CustomerID INT,
    OrderDate DATE,
    Amount INT
);

INSERT INTO CustomerOrders (CustomerID, OrderDate, Amount) VALUES
(101, '2024-01-05', 300),
(101, '2024-02-07', 500),
(101, '2024-03-01', 700),

(102, '2024-01-10', 150),
(102, '2024-03-12', 400),

(103, '2024-01-25', 200),
(103, '2024-02-20', 350),

(104, '2024-02-05', 250),
(104, '2024-03-15', 450),

(105, '2024-01-18', 180);
**1 SOLUTION with SELF JOIN**

```sql
WITH CustStats AS (
	SELECT
		DISTINCT CustomerID,
		YEAR(OrderDate) AS Year,
		MONTH(OrderDate) AS Month
	FROM CustomerOrders
),
ConsecutiveMonths AS (
	SELECT
		c1.CustomerID
	FROM CustStats c1
	INNER JOIN CustStats c2
	ON c1.CustomerID = c2.CustomerID
	AND ( 
		(c1.Year = c2.Year AND c1.Month = c2.Month - 1) OR
		(c1.Year = c2.Year - 1 AND c1.Month = 12 AND c2.Month = 1)
	)
)
SELECT DISTINCT CustomerID
FROM ConsecutiveMonths;
```

**2 SOLUTION with LAG**

```sql
WITH MonthlyOrders AS (
    SELECT DISTINCT
        CustomerID,
        YEAR(OrderDate) AS OrderYear,
        MONTH(OrderDate) AS OrderMonth
    FROM CustomerOrders
),
MonthLag AS (
    SELECT 
        CustomerID,
        OrderYear,
        OrderMonth,
        LAG(OrderYear) OVER (PARTITION BY CustomerID ORDER BY OrderYear, OrderMonth) AS PrevYear,
        LAG(OrderMonth) OVER (PARTITION BY CustomerID ORDER BY OrderYear, OrderMonth) AS PrevMonth
    FROM MonthlyOrders
)
SELECT DISTINCT CustomerID
FROM MonthLag
WHERE 
    (OrderYear = PrevYear AND OrderMonth = PrevMonth + 1)
 OR (OrderYear = PrevYear + 1 AND PrevMonth = 12 AND OrderMonth = 1);

```

**OUTPUT**

<img width="945" height="703" alt="image" src="https://github.com/user-attachments/assets/4197fea3-08d4-4567-8bb2-bc8606eb7d54" />


