---
aliases:
  - BP Test
---
用于检测是否存在[[Heteroskedasticity]].

 $H_0$: there is NO heteroskedasticity in the model specified.
 
Fit Regression Model on the residual: $\varepsilon_{t}=\alpha_{0}+\sum_{i=0}^k\alpha_{k}x_{k}+\mu_{t}$, 计算新模型的$R^2$,称之为$R^2_{\varepsilon}$
计算: $\chi^2\text{-stat}=nR^2_{\varepsilon}\sim \chi^2(k)$ 
Since this is a one-tail test, compare the test statistic with $\chi^2_{1-\alpha,k}$