# Ex.No: 02 LINEAR AND POLYNOMIAL TREND ESTIMATION
### Date: 02/05/2026
### NAME : SANJAY C
### REG NO : 212223240150
### AIM:
To Implement Linear and Polynomial Trend Estiamtion Using Python.
# REQUIREMENTS:
```
1.DATASET : APPLE STOCK PRICE
2.TECHNOLOGY USED : GOOGLE COLLAB
```
### ALGORITHM:
```
1.Import necessary libraries (NumPy, Matplotlib)
2.Load the dataset
3.Calculate the linear trend values using least square method
4.Calculate the polynomial trend values using least square method
5.End the program
```
### PROGRAM:
#### A - LINEAR TREND ESTIMATION
```py
import pandas as pd, numpy as np, matplotlib.pyplot as plt

d = pd.read_csv('apple.csv', parse_dates=['Date'], index_col='Date')
r = d['Volume'].resample('YE').sum().reset_index()
r['Year'] = r['Date'].dt.year

X = r['Year'] - r['Year'].mean()
b, a = np.polyfit(X, r['Volume'], 1)

print(f"Linear Equation for Volume: y = {a:.2f} + {b:.2f}(Year - {r['Year'].mean():.0f})")

r['Linear Trend'] = a + b * X
r.set_index('Year')[['Volume','Linear Trend']].plot(marker='o')

plt.title('Linear Trend for Volume')
plt.grid(); plt.show()
```
#### B- POLYNOMIAL TREND ESTIMATION
```py
import pandas as pd, numpy as np, matplotlib.pyplot as plt

d = pd.read_csv('apple.csv', parse_dates=['Date'], index_col='Date')
r = d['Volume'].resample('YE').sum().reset_index()
r['Year'] = r['Date'].dt.year

X = r['Year'] - r['Year'].mean()
c, b, a = np.polyfit(X, r['Volume'], 2)

print(f"Polynomial Equation for Volume: y = {a:.2f} + {b:.2f}(Year - {r['Year'].mean():.0f}) + {c:.4f}(Year - {r['Year'].mean():.0f})²")

r['Polynomial Trend'] = a + b * X + c * X**2
r.set_index('Year')[['Volume','Polynomial Trend']].plot(marker='o')

plt.title('Polynomial Trend for Volume (Degree 2)')
plt.grid(); plt.show()
```
### OUTPUT
#### A - LINEAR TREND ESTIMATION
<img width="684" height="544" alt="image" src="https://github.com/user-attachments/assets/0b199e13-bacc-4d85-af12-df4de05087af" />


#### B- POLYNOMIAL TREND ESTIMATION
<img width="994" height="536" alt="image" src="https://github.com/user-attachments/assets/62c68ecd-28bf-427f-9f15-a223bf52fa10" />


### RESULT:
Thus the python program for linear and Polynomial Trend Estiamtion has been executed successfully.
