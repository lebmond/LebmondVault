# Measure Goodness of Fit
1. Regression Sum of Square (RSS)
2. Total Sum of Square (TSS)
3. Sum of Square Error (SSE)
TSS = RSS + SSE
## Coefficient of Determination,  $R^2$ 
$R^2=\frac{RSS}{TSS}=1-\frac{SSE}{TSS}$
## Adjusted $R^2$ ($\bar{R^2}$)
$\bar{R^2}=1-\frac{SSE/(n-k-1)}{TSS/(n-1)}=1-\left[\left(\frac{n-1}{n-k-1}\right)(1-R^2)\right]$
When adding an independent variable whose t-statistic is greater than 1, $\bar{R^2}$ increased
## AIC
$AIC=n\ln\left( \frac{SSE}{n} \right)+2(k+1)$ 强调模型的准确度,更适用于预测目的
## BIC
$BIC = n\ln\left( \frac{SSE}{n} \right)+\ln(n)(k+1)$ 强调模型的简洁,更适用于best goodness of fit的需求

# Hypothesis Testing for Coefficients
## Test for Single Coefficients
Null Hypothesis: $H_{0}:b_{i}\text{ = hypothesized value of } b_{i}$ 
Test Statistics: $$
t=\frac{\hat{b}_{i}-\text{hypothesized alue of }b_{i}}{\sigma_{\hat{b}_{i}}}\sim T(n-k-1)
$$
## Joint F-Test
Null Hypothesis: $b_{m}=b_{m+1}=\dots=b_{m+q-1}=0$, thus $q$ coefficients in total.
Test statistics:$$
f=\frac{(SSE_{\text{restricted}}-SSE_{\text{unrestricted}})/q}{SSE_{\text{unrestricted}}/(n-1-k)} \sim F(q,n-k-1)
$$
## General F-Test
Null Hypothesis: $H_{0}:b_{1}=b_{2}=\dots=b_{k}=0$, thus all $k$ coefficients are tested whether they are statistically important.
Test statistics:$$
f=\frac{RSS/k}{SSE/(n-k-1)}\sim F(k, n-k-1)
$$
## Source of Error
### Model Error
## Sampling Error
