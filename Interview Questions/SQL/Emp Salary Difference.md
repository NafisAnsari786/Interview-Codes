<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">

![image](https://github.com/user-attachments/assets/af9ea6ed-5f43-4dbf-adc0-dd46e50a1b19)

CREATE TABLE EmployeeSalaries (
    EmployeeID INT,
    Department VARCHAR(50),
    Salary INT
);

INSERT INTO EmployeeSalaries (EmployeeID, Department, Salary) VALUES
(101, 'HR', 50000),
(102, 'IT', 75000),
(103, 'HR', 45000),
(104, 'IT', 80000),
(105, 'Sales', 60000),
(106, 'Sales', 65000),
(107, 'HR', 55000),
(108, 'IT', 72000),
(109, 'Sales', 58000),
(110, 'HR', 48000);
**SOLUTION**

```sql
WITH SalaryCal AS (
	SELECT 
		Department, 
		MAX(Salary) MaxSal,
		MIN(Salary) MinSal
	FROM EmployeeSalaries
	GROUP BY Department
)
SELECT Department, (MaxSal - MinSal) SalaryDifference
FROM SalaryCal;
```

**OUTPUT**

<img width="888" height="521" alt="image" src="https://github.com/user-attachments/assets/572df9b4-bcc6-4105-8639-19173d4234a1" />

