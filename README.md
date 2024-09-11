### Developed by : Karnan K
### Reg no : 212222230062
### Data :
# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)

### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.
### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Calculate autocorrelation for different lags (1 to 35).
5. Plot the autocorrelation values for each lag in graph.
### PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Load the airline complaints dataset
df = pd.read_csv('/content/baggagecomplaints.csv')

# Calculate the mean and variance
mean_X = np.mean(df['Enplaned'])
var_X = np.var(df['Enplaned'])

# Normalize the data
X_normalized = (df['Enplaned'] - mean_X) / np.sqrt(var_X)

# Pre-allocate autocorrelation table
acf_table = np.zeros((35, 1))

# Calculate autocorrelation for each lag
for k in range(1, 36):
    autocorrelation_k = np.sum(X_normalized[:-k] * X_normalized[k:]) / (len(X_normalized) - k)
    acf_table[k-1] = autocorrelation_k

# Display the ACF graph
plt.plot(acf_table)
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')
plt.title('ACF of Airline Complaints (First 35 Lags)')
plt.show()
```
### OUTPUT:

![Screenshot 2024-09-11 092814](https://github.com/user-attachments/assets/7ef36b7d-2740-49f4-a713-bbe5c28b0c64)

### RESULT:
        Thus the program was successfully created to the auto correlation function airline complaints dataset.
