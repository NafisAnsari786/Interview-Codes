<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">

![image](https://github.com/user-attachments/assets/cdc1b35f-ec1b-4c8c-8596-0cbd1486ac33)

**SOLUTION**
```sql
WITH LaggedSales AS (
    SELECT
        Month,
        Year,
        TotalSales,
        LAG(TotalSales) OVER (ORDER BY Year, Month) AS PreviousTotalSales
    FROM
        MonthlySales
)
SELECT
    Month,
    Year,
    TotalSales,
    PreviousTotalSales,
    ROUND(((TotalSales - PreviousTotalSales) / NULLIF(PreviousTotalSales, 0)) * 100, 2) AS GrowthRate
FROM
    LaggedSales
WHERE
    PreviousTotalSales IS NOT NULL; 
```

**OUTPUT**

![image](https://github.com/user-attachments/assets/86cd769a-7fd3-4c05-a74a-03952333a1ca)

