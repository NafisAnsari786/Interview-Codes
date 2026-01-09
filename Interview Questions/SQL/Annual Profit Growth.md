<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

![image](https://github.com/user-attachments/assets/8e96c929-acc2-40da-8d83-c5a3a3f3330e)

**SOLUTION**
```sql
WITH LaggedSales AS (
    SELECT
        Month,
        Year,
        TotalSales,
        LAG(TotalSales) OVER (
            ORDER BY
                Year,
                CASE Month
                    WHEN 'January' THEN 1
                    WHEN 'February' THEN 2
                    WHEN 'March' THEN 3
                    WHEN 'April' THEN 4
                    WHEN 'May' THEN 5
                    WHEN 'June' THEN 6
                    WHEN 'July' THEN 7
                    WHEN 'August' THEN 8
                    WHEN 'September' THEN 9
                    WHEN 'October' THEN 10
                    WHEN 'November' THEN 11
                    WHEN 'December' THEN 12
                END
        ) AS PreviousTotalSales
    FROM MonthlySales
)
SELECT
    Month,
    Year,
    TotalSales,
    PreviousTotalSales,
    ROUND(
        ((TotalSales - PreviousTotalSales) / NULLIF(PreviousTotalSales, 0)) * 100,
        2
    ) AS GrowthRate
FROM LaggedSales
WHERE PreviousTotalSales IS NOT NULL;

```

**OUTPUT**

![image](https://github.com/user-attachments/assets/1c7d671c-1919-41de-9556-7ca1a07c3a74)

