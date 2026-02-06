<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">

![image](https://github.com/user-attachments/assets/c381ddb0-e0f0-4ff3-bbf2-711fd5af710e)

<img width="667" height="436" alt="image" src="https://github.com/user-attachments/assets/7fce6e3c-261c-4762-a578-6b0a5bca414a" />


**SOLUTION**
```python
import pandas as pd

# Create customer dataset
df = pd.DataFrame({
    "CustomerID": [101, 102, 103, 104, 105, 106, 107, 108, 109, 110],
    "Age": [25, 30, 35, 28, 42, 50, 38, 45, 29, 33],
    "Income": [30000, 40000, 50000, 38000, 65000, 80000, 58000, 72000, 41000, 47000],
    "JoinDate": pd.to_datetime([
        "2023-01-15", "2023-03-20", "2023-06-10", "2023-09-05", "2024-01-12",
        "2024-04-18", "2024-07-22", "2024-10-30", "2025-01-08", "2025-02-01"
    ]),
    "LastTransactionDate": pd.to_datetime([
        "2025-01-25", "2025-01-28", "2025-02-02", "2025-01-30", "2025-02-03",
        "2025-02-04", "2025-02-01", "2025-02-02", "2025-02-05", "2025-02-04"
    ])
})

df

# Correlation
correlation = df.cor(df)
```

**OUTPUT**
![image](https://github.com/user-attachments/assets/af41e7ef-d7c4-49aa-9a9f-8f640c09dc02)
