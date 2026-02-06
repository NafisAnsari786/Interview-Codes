<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

**Clean the Dataset and generate a pivot table along with visualization using the cleaned dataset.**
<img width="797" height="511" alt="image" src="https://github.com/user-attachments/assets/11a0d4a4-4e6d-4d88-895b-d41f1b728415" />

**SOLUTION**

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

df = pd.DataFrame({
    "SalesID": [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12],
    "ProductID": [201, 202, 201, 203, 204, 202, 201, 205, 203, 202, 204, 201],
    "Quantity": [2, 3, 2, 1, 4, 3, 2, np.nan, 1, 3, 4, 2],
    "Revenue": [500, 600, 500, 300, 800, 600, 500, 1000, 300, np.nan, 800, 500],
    "TransactionDate": pd.to_datetime([
        "2024-12-15", "2024-12-16", "2024-12-15",
        "2024-12-18", "2025-01-05", "2024-12-16",
        "2024-12-15", "2025-01-10", "2024-12-18",
        "2024-12-16", None, "2024-12-15"
    ]),
    "StoreLocation": [
        "Pune", "Mumbai", "Pune",
        "Delhi", "Pune", "Mumbai",
        "Pune", "Bangalore", None,
        "Mumbai", "Pune", "Pune"
    ]
})

df
# identifying missing values
df.isnull().sum()

# Identify your actual measurement columns (excluding IDs)
measure_cols = ['Quantity', 'Revenue']

# Handling missing values from measures
df[measure_cols] = df[measure_cols].fillna(df[measure_cols].mean())

# Identifying and dropping missing values from ID columns
df.dropna(subset=['SalesID', 'ProductID'], inplace=True)

# Identifying & Handling missing values from Catgorical columns
df['StoreLocation'] = df['StoreLocation'].fillna(df['StoreLocation'].mode()[0])

# Handling the missing dates from TransactoinDate
df['TransactionDate'] = df['TransactionDate'].ffill() 

# Identifying columns and checking duplicates in those columns
check_cols =  ['ProductID', 'Quantity', 'Revenue', 'TransactionDate']

duplicate_count = df.duplicated(subset=check_cols).sum()
print(f"Total Duplicates found: {duplicate_count}")

# Dropping duplicates and keeping the first occurrence
df = df.drop_duplicates(subset=check_cols, keep='first')
df = df.round(2)
df

# Generating a Pivot table for a quick summary
pivot_report = df.pivot_table(
    index='StoreLocation',
    values=['Revenue', 'Quantity'],
    aggfunc={'Revenue':'sum', 'Quantity':'sum'}
)

pivot_report['Avg_Price_Per_unit'] = pivot_report['Revenue'] / pivot_report['Quantity']

pivot_report = pivot_report.sort_values(by='Revenue', ascending=False)
pivot_report

import matplotlib.pyplot as plt

# Generate the plot from the pivot table and use 'bar' for categorical comparisons
ax = pivot_report['Revenue'].plot(kind='bar', color='limegreen', edgecolor='black')
plt.title('Total Revenue by Store Location')
plt.xlabel('Store Location')
plt.ylabel('Revenue ($)')
plt.xticks(rotation=45)
plt.grid(axis='y', linestyle='--', alpha=0.8)
plt.tight_layout()

```
**OUTPUT**

![image](https://github.com/user-attachments/assets/0e3d9db1-5663-4529-abd5-eb4240eb72fa)
