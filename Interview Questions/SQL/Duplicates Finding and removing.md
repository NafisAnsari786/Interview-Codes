**A. Finding Duplicates**

To see which records are repeated, you group by the columns that should be unique and look for a count greater than 1.

```sql
SELECT emp_id, COUNT(*)
FROM Employees
GROUP BY emp_id
HAVING COUNT(*) > 1;
```

**B. Removing Duplicates**

The "Clean" CTE Method for Removing Duplicates
In this example, we assume "duplicates" are rows where the EmpID is the same, and we want to keep the one with the lowest unique id (or the first one entered).

**Pro-Tip: The "Safety Check"
The best part about using a CTE is that you can test it before you delete data. Just change the last part to a SELECT to see exactly what is about to be deleted:**

```sql
WITH DuplicateFinder AS (
SELECT id, emp_id, 
ROW_NUMBER() OVER (PARTITION BY emp_id ORDER BY id ASC) AS row_num
FROM Employees
)
SELECT * FROM DuplicateFinder
WHERE row_num > 1;
```






