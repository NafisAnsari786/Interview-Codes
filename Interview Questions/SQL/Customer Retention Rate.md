<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

![image](https://github.com/user-attachments/assets/ad68bf25-137d-4830-9a51-d0cdbe6e1c73)

**1 SOLUTION with SELF JOIN**

```SQL
WITH CustomerRetention AS (
    SELECT c1.CustomerID,
    c1.Year AS Current_Year,
    c2.Year AS Next_Year
    FROM CustomerActivity c1
    LEFT JOIN CustomerActivity c2
    ON c1.CustomerID = c2.CustomerID
    AND c2.Year = c1.Year + 1
),
RetentionRate AS (
    SELECT Current_Year AS Year,
    COUNT(DISTINCT CustomerID) AS Customers,
    COUNT(DISTINCT CASE WHEN Next_Year IS NOT NULL THEN CustomerID END) AS RetainedCustomers
    FROM CustomerRetention
    GROUP BY Year
)
SELECT Year, Customers, RetainedCustomers,
ROUND((RetainedCustomers / Customers) * 100, 2) AS Customer_Retention_Rate
FROM RetentionRate
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
![image](https://github.com/user-attachments/assets/6481b72e-d431-456c-abb9-4ef748f9a440)

