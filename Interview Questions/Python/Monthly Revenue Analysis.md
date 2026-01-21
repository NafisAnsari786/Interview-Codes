<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">

![image](https://github.com/user-attachments/assets/2a69f044-8d08-4af4-8494-cac8ab5d9c1d)

**SOLUTION**
```python
import pandas as pd
import matplotlib.pyplot as plt

# Sample dataset, you could load the data from revenue_data.csv
data = {
    'Month': ['Jan', 'Feb', 'Mar'],
    'Revenue': [10000, 15000, 12000]
}

# Creating a DataFrame
df = pd.DataFrame(data)

# Calculate the monthly revenue
monthly_rev = df.groupby('Month')['Revenue'].sum()

# Plotting the monthly revenue trend
monthly_rev.plot(kind='bar', color='skyblue', title='Monthly Revenue Trend')
plt.xlabel('Month')
plt.ylabel('Revenue')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```
**OUTPUT**
![image](https://github.com/user-attachments/assets/3853406f-9654-4f66-8897-254df186eba8)

