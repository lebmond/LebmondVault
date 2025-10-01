> [!Description]
> The EMA is a moving average that places a greater weight on the most recent data points than the SMA (Simple Moving Average).

# 1. Mathematical Form
$$EMA_{\text{Today}}​=​\text{Value}_{\text{Today}}​\times\frac{\text{Smoothing​}}{1+\text{Days}}+EMA_{\text{Yesterday}}​\times(1−\frac{\text{Smoothing}}{1+\text{Days}})$$​
If the smoothing factor is increased, more recent observations is more influential. For a rule of thumb,  $\text{Smoothing}=2$ is preferred. 

# 2. Python Implementation
## 2.1 Self-Defined
```Python
import numpy as np  
  
def exponential_moving_average(prices, period, weighting_factor=0.2):  
ema = np.zeros(len(prices))  
sma = np.mean(prices[:period])  
ema[period - 1] = sma  
for i in range(period, len(prices)):  
ema[i] = (prices[i] * weighting_factor) + (ema[i - 1] * (1 - weighting_factor))  
return ema  
  
prices = [100, 105, 110, 115, 120, 125, 130, 135, 140, 145]  
period = 5  
weighting_factor = 0.2  
  
ema = exponential_moving_average(prices, period, weighting_factor)  
print(ema)
```
## 2.2 Pandas DataFrame Attribute
```Python
import pandas as pd  
# Create a dataset with closing prices for a stock  
prices = [100, 105, 110, 115, 120, 125, 130, 135, 140, 145] 
df = pd.DataFrame({'close': prices})  
# Calculate the EMA with a period of 5 days and a weighting factor of 0.2  
df['ema'] = df['close'].ewm(span=5, adjust=False, min_periods=5).mean()  
print(df)
```
