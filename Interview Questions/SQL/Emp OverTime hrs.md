<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">

![image](https://github.com/user-attachments/assets/2e1a0715-0f12-40ce-9e52-6c54f6585efc)

CREATE TABLE EmployeeHours (
    EmployeeID INT,
    Department VARCHAR(50),
    WorkHours INT,
    OvertimeHours INT
);

INSERT INTO EmployeeHours (EmployeeID, Department, WorkHours, OvertimeHours) VALUES
(101, 'Sales', 40, 5),
(102, 'HR', 40, 2),
(103, 'IT', 40, 8),
(104, 'Sales', 40, 4),
(105, 'IT', 40, 10),
(106, 'Sales', 40, 6),
(107, 'Sales', 40, 7),
(108, 'IT', 40, 9),
(109, 'IT', 40, 6),
(110, 'HR', 40, 3),
(111, 'Sales', 40, 5),
(112, 'Sales', 40, 8);

**SOLUTION**
```sql
WITH DepartmentStats AS (
	SELECT 
		Department, 
		COUNT(DISTINCT EmployeeID) AS NumberofEmployee,
		ROUND(AVG(CAST(OvertimeHours AS FLOAT)),2) AS AvgOverTime
		FROM EmployeeHours
		GROUP BY Department
)
SELECT Department, AvgOvertime
FROM DepartmentStats
WHERE NumberofEmployee > 5;
```
<img width="892" height="442" alt="image" src="https://github.com/user-attachments/assets/d9757e0b-c4c0-4318-8ce2-467a0d17a64d" />

