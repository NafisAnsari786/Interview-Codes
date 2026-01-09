<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">

![image](https://github.com/user-attachments/assets/73a364c7-aede-47f1-be5c-6022b80061de)

**SOLUTION**

```SQL
SELECT COUNT(*) AS ActiveCustomerCount
FROM CustomerData
WHERE LastPurchaseDate >= CURRENT_DATE - INTERVAL '6 months';
```

![image](https://github.com/user-attachments/assets/c5715b4e-7c67-4942-a8f2-aa1046569dcc)
