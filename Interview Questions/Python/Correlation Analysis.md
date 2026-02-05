<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">

![image](https://github.com/user-attachments/assets/c381ddb0-e0f0-4ff3-bbf2-711fd5af710e)

<img width="667" height="436" alt="image" src="https://github.com/user-attachments/assets/7fce6e3c-261c-4762-a578-6b0a5bca414a" />


**SOLUTION**
```python
import pandas as pd

# Load dataset
df = pd.DataFrame({
    'CustomerID': [101, 102, 103],
    'Age': [25, 30, 35],
    'Income': [30000, 40000, 50000]
})

# Calculate correlation between Age and Income
correlation = df[['Age', 'Income']].corr()

print(correlation)
```

**OUTPUT**
![image](https://github.com/user-attachments/assets/af41e7ef-d7c4-49aa-9a9f-8f640c09dc02)
