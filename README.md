# EXP-6-MOVING-AVERAGE-MODEL
## AIM:
Implementation of Moving Average Model Using Python.

## ALGROTHM:
1.Import necessary libraries

2.Read the electricity time series data from a CSV file,Display the shape and the first 20 rows of the dataset

3.Set the figure size for plots

4.Suppress warnings

5.Plot the first 50 values of the 'Value' column

6.Perform rolling average transformation with a window size of 5

7.Display the first 10 values of the rolling mean

8.Perform rolling average transformation with a window size of 10

9.Create a new figure for plotting,Plot the original data and fitted value

10.Show the plot

## PROGRAM:

```
import os
os.chdir("//content/sample_data")
import pandas as pd

from matplotlib import pyplot as plt
from statsmodels.tsa.api import ExponentialSmoothing,SimpleExpSmoothing,Holt
from pylab import rcParams
rcParams['figure.figsize']=20, 5
from statsmodels.tsa.api import SimpleExpSmoothing
import warnings
warnings.filterwarnings('ignore')
data=pd.read_csv("/content/powerconsumption.csv",header=0,index_col=0)
data.pop("Humidity")
data.pop("Temperature")
data.pop("WindSpeed")
data.pop("GeneralDiffuseFlows")
data.pop("DiffuseFlows")
data.pop("PowerConsumption_Zone2")
data.pop("PowerConsumption_Zone3")
data.shape
data.head()
data.isnull().sum()
plt.plot(data[1:35]['PowerConsumption_Zone1'])
plt.xticks(rotation=30)
plt.show()
rollingseries =data[1:35].rolling(window=5)
rollingmean = rollingseries.mean()
print(rollingmean.head(10))

df = data['PowerConsumption_Zone1'][1:35]


model = SimpleExpSmoothing(df)


fit1 = model.fit(smoothing_level=0.2, optimized=False)
fit2 = model.fit(smoothing_level=0.8, optimized=False)
plt.figure(figsize=(12,5))
plt.plot(data[1:35],marker='o',color='black')
plt.xticks(rotation=10)
plt.plot(fit1.fittedvalues,marker='o',color='black')
plt.plot(fit2.fittedvalues,marker='o',color='green')
rollingmean.plot(color='red')
plt.show()

```



## OUTPUT:
### Moving Average 
![image](https://github.com/s-adhithya/EXP-6-MOVING-AVERAGE-MODEL/assets/113497423/fbfc63b2-67a2-4950-a960-28f8eed0c02f)

### Plot Transform Dataset

![image](https://github.com/s-adhithya/EXP-6-MOVING-AVERAGE-MODEL/assets/113497423/06892159-8e4d-43ba-b2b1-09cecca55950)

### Exponential Smoothing image

![image](https://github.com/s-adhithya/EXP-6-MOVING-AVERAGE-MODEL/assets/113497423/37e515fe-892a-4e8b-8f5b-dd6a5d78fa9f)

## RESULT:
Thus we have successfully implemented the Moving Average Model using above mentioned program.
