Can verify the second requirements above (i.e. uncorrelated errors) . 
Note that the [[Durbin-Waston Test|DW test]] from [[Serial Correlation]] cannot be appropriately used for a regression that has a lagged value of the dependent variable as one of the explanatory variables, but [[Breusch-Godfrey Test|BG Test]] can.
Use t-test to detect if residual autocorrelation is significantly different from zero:
$$t-stat=\frac{r_{\epsilon_{t},\epsilon_{t-k}}-0}{\frac{1}{\sqrt{ n }}}$$ where $n$ is the total observations in time series used to estimate the model


