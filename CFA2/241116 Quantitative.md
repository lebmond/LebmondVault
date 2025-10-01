# Multi-Linear Regression
## Coefficient of Determination, $R^2$ 
$$R^2=\frac{RSS}{SST}=\frac{SST-SSE}{SST}$$
## Adjusted $R^2$
$$\text{Adjusted R}^2=1- \frac{n-1}{n-k-1}(1-R^2) $$
## AIC & BIC
AIC is preferred when we would like the model to have better forecasting power
BIC is preferred when we prefer the model to have a better goodness of fit.


#
# Stationary

 A Time Series is stationary if satisfying three principal requirements:
1.  Expected value of the time series is constant and finite in all periods. 
2. Variance of the time series is constant and finite in all periods.
3. The covariance of the time series with its lagged values must be constant and finite in all periods.
# Autoregressive Models (AR)
即使用自己的过去值来预计未来值; a p-order AR model is given by:
$AR(p):\ \ x_{t} = b_{0}+b_{1}x_{t-1}+b_{2}x_{t-2}+b_{p}x_{t-p}+\epsilon_{t}$ 
Can be estimated using OLS if:
- Covariance stationary;
- Uncorrelated Errors;
- Homoskedasticity (error term variance are time-independent)

## Mean reversion
AR(p) could be mean-reverting and is omitted here, AR(1) is mean reverting if $|\phi_{1}|<1$, and mean reverting level is $\frac{\phi_{0}}{1-\phi_{1}}$
if $|\phi_1|=1$, then AR(1) becomes a random walk, and it is not mean-reverting (use DF test to detect so)
if $|\phi_1|>1$ then AR(1) is explosive


## Autocorrelation
Can verify the second requirements above (i.e. uncorrelated errors) . 
Note that the DW statistic from [[241116 Quantitative#^95ab44|Serial Correlation]] cannot be appropriately used for a regression that has a lagged value of the dependent variable as one of the explanatory variables.
Use t-test to detect if residual autocorrelation is significantly different from zero:
$$t-stat=\frac{r_{\epsilon_{t},\epsilon_{t-k}}-0}{\frac{1}{\sqrt{ n }}}$$ where $n$ is the total observations in time series used to estimate the model

## Heteroskedasticity
Heteroskedasticity refers to non-constant variance of the error terms.
1. In Multi-linear regression, test heteroskedasticity with BP test;
2. In time-series, test if a time series is ARCH(1):
   $$\epsilon_{t}^2=a_{0}+a_{1}\epsilon_{t-1}^2+\mu_{t}$$
   If $a_1$ is significantly different from 0, then time series is ARCH(1), and the variance of ARCH is given by:$$\hat{\sigma}_{t+1}^2=\hat{a}_{0}+\hat{a}_{1}\hat{\epsilon}_{t}^2$$

# Moving-Average Models (MA)
使用过去的error来预测未来的自己
$$\begin{aligned}
\text{MA}(q): x_{t}=\epsilon_{t}+\sum_{i=1}^q\theta_{i}\epsilon_{t-i}
\end{aligned}$$where $E[\epsilon_t]=0$, $E[\epsilon_t^2]=\sigma^2$, $Cov(\epsilon_t,\epsilon_s)=0$ for $t\not=s$ 
