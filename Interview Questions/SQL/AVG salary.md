<img src="https://img.shields.io/badge/EASY-green" alt="EASY" width="70">


 
![image](https://github.com/user-attachments/assets/f9ed2d30-cf67-4e06-91c9-f99a00c21052)

**SOLUTION 1**

```sql
SELECT Department, AVG(Salary) AS avg_salary
FROM Employees
GROUP BY Department
ORDER BY avg_salary DESC
LIMIT 1;
```

**SOLUTION 2 Using CTE & Window Function**

```sql
WITH AvgSalary AS (
SELECT Department, AVG(Salary) AS avg_salary
FROM Employees
),
WITH RankedAverages AS (
SELECT Department, avg_salary,
DENSE_RANK() OVER (ORDER BY avg_salary DESC) AS drnk
)
SELECT Department, avg_salary
FROM RankedAverages
WHERE drnk = 1;
```
