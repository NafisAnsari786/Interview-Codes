**A. Finding Duplicates**
To see which records are repeated, you group by the columns that should be unique and look for a count greater than 1.

```sql
SELECT emp_id, COUNT(*)
FROM Employees
GROUP BY emp_id
WHERE COUNT(*) > 1;
```
