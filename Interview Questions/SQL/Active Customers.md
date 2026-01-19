<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">

![image](https://github.com/user-attachments/assets/73a364c7-aede-47f1-be5c-6022b80061de)

<img width="888" height="420" alt="image" src="https://github.com/user-attachments/assets/f9b59c61-083d-484a-9c1f-52c42eaaa170" />

**Table and data**
CREATE TABLE CustomerData (
    CustomerID INT PRIMARY KEY,
    Name VARCHAR(50),
    JoinDate DATE,
    LastPurchaseDate DATE,
    Status VARCHAR(20)
);

INSERT INTO CustomerData (CustomerID, Name, JoinDate, LastPurchaseDate, Status) VALUES
(1, 'Alice',  '2024-01-10', '2026-01-05', 'Active'),
(2, 'Bob',    '2023-05-12', '2025-06-15', 'Inactive'),
(3, 'Charlie','2022-08-20', '2025-12-28', 'Active'),
(4, 'Dave',   '2021-03-18', '2024-11-10', 'Inactive'),
(5, 'Eva',    '2024-06-05', '2026-01-12', 'Active'),
(6, 'Frank',  '2023-09-22', '2025-10-01', 'Active'),
(7, 'Grace',  '2022-02-14', '2024-08-20', 'Inactive'),
(8, 'Henry',  '2024-07-09', '2026-01-08', 'Active'),
(9, 'Ivy',    '2025-01-30', '2025-12-18', 'Active'),
(10,'Jack',   '2021-11-11', '2024-05-10', 'Inactive'),
(11,'Karen',  '2024-03-01', '2026-01-02', 'Active'),
(12,'Leo',    '2022-09-17', '2025-04-05', 'Inactive'),
(13,'Mona',   '2024-05-14', '2026-01-10', 'Active'),
(14,'Nate',   '2023-06-21', '2024-12-01', 'Inactive'),
(15,'Olivia', '2025-02-02', '2026-01-14', 'Active'),
(16,'Paul',   '2021-01-19', '2024-03-22', 'Inactive'),
(17,'Quinn',  '2024-09-10', '2026-01-11', 'Active'),
(18,'Rose',   '2023-04-25', '2025-02-15', 'Inactive'),
(19,'Steve',  '2025-06-18', '2026-01-13', 'Active'),
(20,'Tina',   '2022-10-07', '2024-09-12', 'Inactive');

**SOLUTION MySQL**


```SQL
SELECT COUNT(*) AS ActiveCustomerCount
FROM CustomerData
WHERE LastPurchaseDate >= CURRENT_DATE - INTERVAL '6 months';
```

![image](https://github.com/user-attachments/assets/c5715b4e-7c67-4942-a8f2-aa1046569dcc)
