## Influence Analysis
## High-Leverage Point

### Leverage

#### Threshold
All observation with leverage ratio $h_{ii}>3\left(\frac{k+1}{n}\right)$ are considered as high-leverage points
- $k$ is the number of explanatory variables, and 
- $n$ is the number of total observations.

## Outlier
An observation with an extremely high value of dependent variables
### Studentized Residuals $t_{i*}$
1. 检测Outliers
2. $t_{i*}=\frac{e_{i*}}{S_{e^*}}=e_{i}\sqrt{\frac{n-k-1}{SSE(1-h_{ii})-e_{i}^2} }$
Rule of thumb: $|t_{i*}|>3$ are considered as **outliers**, and $|t_{i*}|>t\text{-}stat_{0.95,n-k-2}$ are considered as **potentially influential points**.

## Cook's Distance
可以同时检查两种influential points.一个观测对象的Cook's Distance越大,越有可能是influential point.
### Threshold
一般认为如果一个点的Cook's Distance 大于0.5则有可能是influential,大于1或者大于$2\sqrt{ \frac{k}{n} }$ 都非常可能是.