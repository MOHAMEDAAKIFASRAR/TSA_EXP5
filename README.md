# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 17-11-2026

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
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

data = pd.read_csv("AirPassengers.csv")
data["Month"] = pd.to_datetime(data["Month"], format="%Y-%m")
data = data.dropna(subset=["#Passengers"])
data = data.sort_values("Month")
data.set_index("Month", inplace=True)

# =====================================
# Seasonal Decomposition
# =====================================
decomposition = seasonal_decompose(
    data["#Passengers"],
    model="additive",
    period=12
)

# =====================================
# Plot Results
# =====================================
plt.figure(figsize=(12, 12))

# -------------------------------
# Original AirPassengers
# -------------------------------
plt.subplot(411)
plt.plot(
    data["#Passengers"],
    label="Passengers",
    color="blue"
)
plt.title("Original AirPassengers Data")
plt.legend(loc="upper left")

# -------------------------------
# Trend
# -------------------------------
plt.subplot(412)
plt.plot(
    decomposition.trend,
    label="Trend",
    color="orange"
)
plt.title("Trend Plot")
plt.legend(loc="upper left")

# -------------------------------
# Seasonal
# -------------------------------
plt.subplot(413)
plt.plot(
    decomposition.seasonal,
    label="Seasonality",
    color="green"
)
plt.title("Seasonality Plot")
plt.legend(loc="upper left")

# -------------------------------
# Residual
# -------------------------------
plt.subplot(414)
plt.plot(
    decomposition.resid,
    label="Residual",
    color="red"
)
plt.title("Residual Plot")
plt.legend(loc="upper left")

plt.tight_layout()
plt.show()
```

### OUTPUT:

PLOTTING THE DATA:
<img width="1147" height="287" alt="image" src="https://github.com/user-attachments/assets/ba38ca80-dd73-44f7-81f2-eeba98352a56" />

TREND PLOT REPRESENTATION :
<img width="1137" height="282" alt="image" src="https://github.com/user-attachments/assets/c6e43434-545c-4dbd-9ef2-e9f593f9f435" />

SEASONAL PLOT REPRESENTATION :
<img width="1145" height="277" alt="image" src="https://github.com/user-attachments/assets/b436c97e-a403-4509-af85-998ae7355f19" />

OVERAL REPRESENTATION:
<img width="1145" height="286" alt="image" src="https://github.com/user-attachments/assets/3f89291b-9607-43a8-9746-3c55d2923cdc" />

### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
