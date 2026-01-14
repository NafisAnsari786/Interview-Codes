<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">

![image](https://github.com/user-attachments/assets/34290515-7c8b-462b-b2b8-cd62719e85c3)

**SOLUTION**

```python
import pandas as pd

df = pd.DataFrame({
    'SalesID': [1,2,3,4],
    'ProductID': [201,202,201,203],
    'Quantity': [2,3,2,1],
    'Revenue': [500,600,500,300]
})

unique_df = df.drop_duplicates(subset=['ProductID','Quantity','Revenue'], keep='first')
unique_df
```
**OUTPUT**

![image](https://github.com/user-attachments/assets/0e3d9db1-5663-4529-abd5-eb4240eb72fa)
