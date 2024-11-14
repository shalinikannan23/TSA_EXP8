# NAME : SHALINI K
# REGISTER NUMBER : 212222240095
# Ex.No: 08     MOVINTG AVERAGE MODEL AND EXPONENTIAL SMOOTHING
### Date: 


### AIM:
To implement Moving Average Model and Exponential smoothing Using Python.
### ALGORITHM:
1. Import necessary libraries
2. Read the electricity time series data from a CSV file,Display the shape and the first 20 rows of
the dataset
3. Set the figure size for plots
4. Suppress warnings
5. Plot the first 50 values of the 'Value' column
6. Perform rolling average transformation with a window size of 5
7. Display the first 10 values of the rolling mean
8. Perform rolling average transformation with a window size of 10
9. Create a new figure for plotting,Plot the original data and fitted value
10. Show the plot
11. Also perform exponential smoothing and plot the graph
### PROGRAM:
```py
# Import necessary libraries
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import warnings
from statsmodels.tsa.holtwinters import ExponentialSmoothing

# Suppress warnings
warnings.filterwarnings('ignore')

# Read the Bitcoin price data from a CSV file
data = pd.read_csv('coin_Bitcoin.csv')

# Convert 'Date' to datetime format and set it as the index
data['Date'] = pd.to_datetime(data['Date'], format='%Y-%m-%d %H:%M:%S')
data.set_index('Date', inplace=True)

# Focus on the 'Marketcap' column
data = data[['Marketcap']]

# Display the shape and the first 20 rows of the dataset
print("Shape of the dataset:", data.shape)
print("First 20 rows of the dataset:")
print(data.head(20))

# Plot Transform Dataset (Original Marketcap Data)
plt.figure(figsize=(12, 6))
plt.plot(data['Marketcap'], label='Original Marketcap Data', color='blue')
plt.title('Transform Dataset (Original Marketcap)')
plt.xlabel('Date')
plt.ylabel('Marketcap (USD)')
plt.legend()
plt.grid()
plt.show()

# Moving Average
# Perform rolling average transformation with a window size of 10
rolling_mean_10 = data['Marketcap'].rolling(window=10).mean()

# Plot Moving Average
plt.figure(figsize=(12, 6))
plt.plot(data['Marketcap'], label='Original Marketcap Data', color='blue')
plt.plot(rolling_mean_10, label='Moving Average (window=10)', color='orange')
plt.title('Moving Average of Marketcap')
plt.xlabel('Date')
plt.ylabel('Marketcap (USD)')
plt.legend()
plt.grid()
plt.show()

# Exponential Smoothing
model = ExponentialSmoothing(data['Marketcap'], trend='add', seasonal=None)
model_fit = model.fit()

# Make predictions for the next 30 periods (you can adjust this)
predictions = model_fit.predict(start=len(data), end=len(data) + 30)

# Plot the original data and Exponential Smoothing predictions
plt.figure(figsize=(12, 6))
plt.plot(data['Marketcap'], label='Original Marketcap Data', color='blue')
plt.plot(predictions, label='Exponential Smoothing Forecast', color='orange')
plt.title('Exponential Smoothing Predictions for Marketcap')
plt.xlabel('Date')
plt.ylabel('Marketcap (USD)')
plt.legend()
plt.xticks(rotation=45)
plt.grid(True)
plt.tight_layout()
plt.show()


```
### OUTPUT:


<table>
  <tr>
    <td style="width:50%">
      <h3>Original Image</h3>
      <img src="https://github.com/user-attachments/assets/afc76f52-6bfa-4657-85b8-df6eb69d67fb" style="width:48%; height:auto;">
    </td>
    <td style="width:50%">
      <h3>Moving Average</h3>
      <img src="https://github.com/user-attachments/assets/6034a007-721d-4645-9b41-c3c2b620f402" style="width:48%; height:auto;">
    </td>
  </tr>
  <tr>
    <td style="width:50%">
      <h3>Plot Transform Dataset</h3>
      <img src="https://github.com/user-attachments/assets/fccc8b91-6477-44db-adf8-8bb63b4f92cf" style="width:48%; height:auto;">
    </td>
    <td style="width:50%">
      <h3>Exponential Smoothing</h3>
      <img src="https://github.com/user-attachments/assets/b09a3289-8459-48c3-b729-e699fda0784c" style="width:48%; height:auto;">
    </td>
  </tr>
</table>


### RESULT:
Thus we have successfully implemented the Moving Average Model and Exponential smoothing using python.
