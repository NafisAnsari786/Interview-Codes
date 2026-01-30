<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">

![image](https://github.com/user-attachments/assets/4b7d7546-4a75-4cb5-b43b-a5c1b69de63b)

**Create Table & Schema**
CREATE TABLE EmployeeRecords (
    EmpID INT PRIMARY KEY,
    Department VARCHAR(50),
    HireDate DATE,
    TerminationDate DATE NULL,
    Salary DECIMAL(10,2)
);

INSERT INTO EmployeeRecords (EmpID, Department, HireDate, TerminationDate, Salary) VALUES
-- Sales
(1, 'Sales', '2020-01-15', '2023-11-01', 50000),
(4, 'Sales', '2022-02-01', NULL,        60000),
(6, 'Sales', '2018-06-10', '2021-08-31', 55000),
-- IT
(2, 'IT',    '2019-05-10', NULL,        70000),
(5, 'IT',    '2020-08-15', NULL,        65000),
(7, 'IT',    '2021-09-01', '2024-01-15', 72000),
-- HR
(3, 'HR',    '2021-03-25', '2022-12-31', 45000),
(8, 'HR',    '2017-11-20', NULL,        52000),
-- Finance
(9, 'Finance','2019-02-01', NULL,        80000),
(10,'Finance','2021-07-15', '2023-06-30', 75000);
**SOLUTION SQL Server**
```sql
WITH TenureCal AS (
	SELECT Department,
		CASE
			WHEN TerminationDate IS NULL THEN DATEDIFF(DAY, HireDate, GETDATE()) / 365.0
			ELSE DATEDIFF(DAY, HireDate, TerminationDate) / 365.0
		END AS Tenure
	FROM EmployeeRecords
)
SELECT Department,
AVG(Tenure) AS AvgTenure
FROM TenureCal
GROUP BY Department;
```

**OUTPUT**

![image](https://github.com/user-attachments/assets/f8510dd4-aaf5-49a0-b040-709ef2e19615)
