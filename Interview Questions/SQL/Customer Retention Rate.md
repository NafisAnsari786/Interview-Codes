<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

![image](https://github.com/user-attachments/assets/ad68bf25-137d-4830-9a51-d0cdbe6e1c73)

CREATE TABLE CustomerActivity (
    CustomerID INT,
    Year INT,
    PurchaseAmount INT
);
INSERT INTO CustomerActivity (CustomerID, Year, PurchaseAmount) VALUES
(101, 2022, 1000),
(101, 2023, 1200),
(101, 2024, 1500),
(102, 2022, 600),
(102, 2023, 800),
(103, 2023, 400),
(104, 2023, 900),
(104, 2024, 1100),
(105, 2022, 700),
(105, 2024, 950),
(106, 2022, 500),
(106, 2023, 650),
(106, 2024, 900);

**1 SOLUTION with SELF JOIN**

```SQL
WITH YearlyActivity AS (
	SELECT c1.CustomerID,
	c1.Year AS CurrentYear,
	c2.Year AS NextYear
	FROM CustomerActivity c1
	LEFT JOIN CustomerActivity c2
	ON c1.CustomerID = c2.CustomerID
	AND c2.Year = c1.Year+1
),
RetentionData AS (
	SELECT CurrentYear AS Year,
	COUNT(DISTINCT CustomerID) AS Customers,
	COUNT(DISTINCT CASE WHEN NextYear IS NOT NULL THEN CustomerID END) AS RetainedCustomers
	FROM YearlyActivity
	GROUP BY CurrentYear
)
SELECT Customers, Year, RetainedCustomers,
ROUND((CAST(RetainedCustomers AS FlOAT) / Customers)*100,2) AS CustomerRetentionRate
FROM RetentionData
ORDER BY Year;
```

**2 SOLUTION with LEAD**

```sql
WITH YearlyActivity AS (
    SELECT 
        CustomerID, 
        Year,
        LEAD(Year) OVER (PARTITION BY CustomerID ORDER BY Year) AS Next_Year
    FROM CustomerActivity
)
SELECT 
    Year,
    COUNT(CustomerID) AS Total_Customers,
    COUNT(CASE WHEN Next_Year = Year + 1 THEN 1 END) AS Retained_Customers,
    ROUND(COUNT(CASE WHEN Next_Year = Year + 1 THEN 1 END) * 100.0 / COUNT(CustomerID), 2) AS Retention_Rate
FROM YearlyActivity
GROUP BY Year
ORDER BY Year;
```

**OUTPUT**
<img width="1227" height="740" alt="image" src="https://github.com/user-attachments/assets/5d9d6478-c923-4d7d-8f10-c11236584bf3" />


