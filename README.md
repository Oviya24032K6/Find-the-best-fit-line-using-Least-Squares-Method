# Implementation of Univariate Linear Regression
## AIM:
To implement univariate Linear Regression to fit a straight line using least squares.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Get the independent variable X and dependent variable Y.
2. Calculate the mean of the X -values and the mean of the Y -values.
3. Find the slope m of the line of best fit using the formula. 
<img width="231" alt="image" src="https://user-images.githubusercontent.com/93026020/192078527-b3b5ee3e-992f-46c4-865b-3b7ce4ac54ad.png">
4. Compute the y -intercept of the line by using the formula:
<img width="148" alt="image" src="https://user-images.githubusercontent.com/93026020/192078545-79d70b90-7e9d-4b85-9f8b-9d7548a4c5a4.png">
5. Use the slope m and the y -intercept to form the equation of the line.
6. Obtain the straight line equation Y=mX+b and plot the scatterplot.

## Program:
```
/*
Program to implement univariate Linear Regression to fit a straight line using least squares.
Developed by: OVIYA P
RegisterNumber:  212223110033
*/
```
```
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

# Load dataset from CSV
data = pd.read_csv('student_scores123.csv')

# Splitting the combined column into 'Hours' and 'Scores'
data[['Hours', 'Scores']] = data['Hours\tScores'].str.split('\t', expand=True)

# Convert to numeric data types
data['Hours'] = pd.to_numeric(data['Hours'])
data['Scores'] = pd.to_numeric(data['Scores'])

# Use the correct column names
X = data['Hours'].values
Y = data['Scores'].values

# Calculate means
Xmean = np.mean(X)
Ymean = np.mean(Y)

# Calculate coefficients
num = np.sum((X - Xmean) * (Y - Ymean))
den = np.sum((X - Xmean) ** 2)
m = num / den
c = Ymean - m * Xmean

# Print coefficients
print(f"Slope (m): {m:.4f}")
print(f"Intercept (c): {c:.4f}")

# Predict Y values
Y_pred = m * X + c

# Print predicted Y values
print("Predicted Y values:", Y_pred)

# Plotting
plt.scatter(X, Y, color="blue", label="Data points")
plt.plot(X, Y_pred, color="red", label="Regression line")
plt.xlabel("Hours")
plt.ylabel("Scores")
plt.title("Univariate Linear Regression")
plt.legend()
plt.show()

```
## Output:
![image](https://github.com/user-attachments/assets/f6b535b6-53a3-4116-bb7d-b94b8f7c257e)
![image](https://github.com/user-attachments/assets/c44efdc6-eb73-4629-a465-e3b77582f02e)



## Result:
Thus the univariate Linear Regression was implemented to fit a straight line using least squares using python programming.
