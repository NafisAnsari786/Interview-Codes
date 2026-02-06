<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">

![image](https://github.com/user-attachments/assets/2541a081-6b59-45bb-abd3-a3e869309305)

<img width="672" height="736" alt="image" src="https://github.com/user-attachments/assets/b5bf92ba-70db-4a49-bccd-7a63ae51811a" />

**SOLUTION**
```python
import pandas as pd

# Create dataset for the table
df = pd.DataFrame({
    "ProductID": range(201, 221),
    "Category": [
        "Electronics", "Electronics", "Electronics", "Electronics", "Electronics",
        "Furniture", "Furniture", "Furniture", "Furniture", "Furniture",
        "Clothing", "Clothing", "Clothing", "Clothing", "Clothing",
        "Groceries", "Groceries", "Groceries", "Groceries", "Groceries"
    ],
    "Sales": [
        10, 15, 8, 12, 20,
        5, 10, 7, 12, 6,
        20, 25, 30, 18, 22,
        50, 45, 60, 55, 48
    ],
    "Price": [
        500, 600, 550, 520, 650,
        300, 400, 350, 420, 380,
        50, 60, 55, 58, 52,
        40, 42, 38, 45, 41
    ],
    "OrderDate": pd.to_datetime([
        "2024-01-15", "2024-02-10", "2024-03-05", "2024-04-18", "2024-05-22",
        "2024-06-14", "2024-07-09", "2024-08-01", "2024-09-17", "2024-10-03",
        "2024-11-20", "2024-12-05", "2025-01-10", "2025-01-22", "2025-02-02",
        "2025-02-05", "2025-02-07", "2025-02-10", "2025-02-12", "2025-02-14"
    ]),
    "Region": [
        "North", "South", "East", "West", "North",
        "South", "East", "West", "North", "South",
        "East", "West", "North", "South", "East",
        "West", "North", "South", "East", "West"]
})
# Group by 'Category' and calculate total sales and average price
aggregated_data = df.groupby(Category).aff(
    total_sales = ('Sales', 'sum'),
    avg_price = ('Price', 'mean')

aggregated_data
```
**OUTPUT**

![image](https://github.com/user-attachments/assets/763c9659-c2f4-4c47-9d1b-1c9cc345aa22)
