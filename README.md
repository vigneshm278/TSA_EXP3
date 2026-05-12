# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
# Date: 29/04/2026

### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.
### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.
### PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

df = pd.read_excel('/content/supermarket_10years.xlsx')

print("Columns in dataset:", df.columns)

data = df['Sales_Amount'].dropna().values

N = len(data)

lags = range(10)

autocorr_values = []

mean_data = np.mean(data)
variance_data = np.var(data)

for lag in lags:
    if lag == 0:
        autocorr_values.append(1)
    else:
        auto_cov = np.sum(
            (data[:-lag] - mean_data) *
            (data[lag:] - mean_data)
        ) / N

        autocorr_values.append(auto_cov / variance_data)

plt.figure(figsize=(10, 6))

plt.stem(lags, autocorr_values)

plt.title('Autocorrelation Function (ACF)')

plt.xlabel('Lag')
plt.ylabel('Autocorrelation')

plt.grid(True)

plt.show()
```

### OUTPUT:
<img width="1224" height="687" alt="image" src="https://github.com/user-attachments/assets/0207d255-c7a3-4741-a39f-a851e244a77a" />



### RESULT:
        Thus we have successfully implemented the auto correlation function in python.
