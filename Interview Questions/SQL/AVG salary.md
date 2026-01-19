<img src="https://img.shields.io/badge/EASY-green" alt="EASY" width="70">

![image](https://github.com/user-attachments/assets/f9ed2d30-cf67-4e06-91c9-f99a00c21052)

**Table schema** 
CREATE TABLE Employees (
    EmpID INT PRIMARY KEY,
    Department VARCHAR(50),
    Salary INT,
    DateOfJoining DATE,
    PerformanceScore INT
);

INSERT INTO Employees (EmpID, Department, Salary, DateOfJoining, PerformanceScore) VALUES
(1, 'Sales',  65000, '2024-03-15', 4),
(2, 'IT',     90000, '2023-07-01', 5),
(3, 'HR',     55000, '2022-06-12', 3),
(4, 'Sales',  72000, '2025-01-10', 4),
(5, 'IT',     88000, '2021-05-20', 5),
(6, 'Finance',75000, '2024-09-18', 4),
(7, 'HR',     60000, '2023-11-05', 3),
(8, 'IT',     95000, '2025-02-14', 5),
(9, 'Sales',  70000, '2022-08-22', 4),
(10,'Finance',80000, '2023-04-30', 5);

**SOLUTION MySQL**

```sql
SELECT Department, AVG(Salary) AS avg_salary
FROM Employees
GROUP BY Department
ORDER BY avg_salary DESC
LIMIT 1;
```

**SOLUTION SQL server**

```sql
SELECT TOP 1 Department, AVG(Salary) AS avg_salary
FROM Employees
GROUP BY Department
ORDER BY avg_salary DESC;
```

<img width="756" height="262" alt="image" src="https://github.com/user-attachments/assets/1335f902-8195-4c82-82c2-bfe6e1eb012c" />

