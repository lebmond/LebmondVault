---
aliases:
  - DW Test
---
仅能用于检测非时间序列中的一阶[[Serial Correlation]]
The DW statistic cannot be appropriately used for a regression that has a lagged value of the dependent variable as one of the explanatory variables. To test for [[serial correlation]], we need to examine the [[Autocorrelation#^95ab44|autocorrelation]].

1. $H_0$: NO [[serial correlation]] at order $1$;
2. DW test statistics为$$\text{DW-stat}=\frac{\sum_{t=2}^T(\hat\epsilon_{t}-\hat\epsilon_{t-1})^2}{\sum_{t=1}^T \hat{\epsilon}_{t}^2}\approx2(1-\rho_{\varepsilon_{t},\varepsilon_{t-1}})$$
Clearly, from the approximation, can be seen that DW test statistic close to 0 indicate perfectly positive correlation, and 4 indicate perfectly negative correlation.
DW test的critical value需要查一个特殊的DW test表