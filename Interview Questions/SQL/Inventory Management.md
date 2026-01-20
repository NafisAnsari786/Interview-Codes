<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

![image](https://github.com/user-attachments/assets/224a8050-79f4-4a62-a202-61d3528a864b)


**SOLUTION**
```sql
WITH LowStock AS (
    SELECT 
        ProductID,
        CASE Month
            WHEN 'Jan' THEN 1
            WHEN 'Feb' THEN 2
            WHEN 'Mar' THEN 3
        END AS MonthNum,
        StockLevel,
        ReorderLevel,
        CASE 
            WHEN StockLevel < ReorderLevel THEN 1
            ELSE 0
        END AS BelowReorderFlag
    FROM Inventory
),
ThreeMonthWindow AS (
    SELECT 
        ProductID,
        SUM(BelowReorderFlag) OVER (
            PARTITION BY ProductID 
            ORDER BY MonthNum 
            ROWS BETWEEN 2 PRECEDING AND CURRENT ROW
        ) AS BelowReorderCount
    FROM LowStock
)
SELECT DISTINCT ProductID
FROM ThreeMonthWindow
WHERE BelowReorderCount = 3
ORDER BY ProductID;

```
**OUTPUT**

![image](https://github.com/user-attachments/assets/8e6689e1-420b-409c-a836-5342084dc77b)

![image](https://github.com/user-attachments/assets/b41777d6-0024-453b-b70c-13bf543d5843)

![image](https://github.com/user-attachments/assets/018ecc30-7238-4b09-a282-261e1b50db34)


