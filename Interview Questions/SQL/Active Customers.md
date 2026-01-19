<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">

![image](https://github.com/user-attachments/assets/73a364c7-aede-47f1-be5c-6022b80061de)

<img width="888" height="420" alt="image" src="https://github.com/user-attachments/assets/f9b59c61-083d-484a-9c1f-52c42eaaa170" />

CREATE TABLE CustomerData (
    CustomerID INT PRIMARY KEY,
    Name VARCHAR(50),
    JoinDate DATE,
    LastPurchaseDate DATE,
    Status VARCHAR(20)
);

**SOLUTION MySQL**


```SQL
SELECT COUNT(*) AS ActiveCustomerCount
FROM CustomerData
WHERE LastPurchaseDate >= CURRENT_DATE - INTERVAL '6 months';
```

![image](https://github.com/user-attachments/assets/c5715b4e-7c67-4942-a8f2-aa1046569dcc)
