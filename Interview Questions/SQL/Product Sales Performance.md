<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

![image](https://github.com/user-attachments/assets/4539db3d-1001-4baf-809a-6004dc3974d0)

**SOLUTION**

 
```sql
WITH TopProducts AS(
    SELECT ProductID, Category, Revenue,
    DENSE_RANK() OVER (PARTITION BY Category ORDER BY Revenue DESC) AS dense_rank
    FROM ProductSales
)
SELECT ProductID, Category, Revenue
FROM TopProducts
WHERE dense_rank <= 3;
```
**OUTPUT**
![image](https://github.com/user-attachments/assets/e6f0a55a-975d-4fa6-a3b5-128d028da1e9)
