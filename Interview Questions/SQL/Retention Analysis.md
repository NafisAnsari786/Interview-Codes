<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">

![image](https://github.com/user-attachments/assets/4b7d7546-4a75-4cb5-b43b-a5c1b69de63b)

**SOLUTION Postgresql**

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
