# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 23.09.2025

### AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average temperature of a city/country and for airline passengers.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```python
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Load dataset
data = pd.read_csv("gold_price.csv")

# Clean Price column (remove commas, convert to float)
data["Price"] = data["Price"].str.replace(",", "").astype(float)

# Convert Date column to datetime
data["Date"] = pd.to_datetime(data["Date"], format="%m/%d/%Y")

# Sort by Date (just in case)
data = data.sort_values("Date")

# Set Date as index (time series)
data.set_index("Date", inplace=True)

# Perform seasonal decomposition (daily data, let's assume weekly seasonality=7)
result = seasonal_decompose(data["Price"], model="additive", period=7)

# Plot decomposition
plt.rcParams['figure.figsize'] = [12, 8]
result.plot()
plt.suptitle("Seasonal Decomposition of Gold Price", fontsize=14)
plt.show()
```
### OUTPUT:

<img width="986" height="494" alt="image" src="https://github.com/user-attachments/assets/453cbe6e-5da5-4f23-b9ba-13cc599d67cb" />


### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
