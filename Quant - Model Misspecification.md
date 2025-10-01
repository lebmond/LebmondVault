# Type I & Type II Error
## Type I Error
- 去真 (False Positive), 结果为真,
- 错误地拒绝了一个正确的Null Hypothesis.犯一类错误的概率就是significance level ($\alpha$) 
## Type II Error^177ff8

存伪 (False Negative)

Regression Analysis
# Model Misspecification
## Heteroskedasticity
1. 影响:Heteroskedasticity分为unconditional heteroskedasticity和conditional heteroskedasticity.第一种并不需要特别处理.
2. 两种都不影响模型估算的系数的consistency
3. 但是第二种会给系数的估计带来**更大的**standard deviation.
4. 检测: Breusch-Pagan test, a **one-tail, right-side $\chi^2$ test**. 
	1. $H_0$: there is NO heteroskedasticity in the model specified.
	2. Test statistic: $\chi^2_{\text{BP, }k}=n\times R^2$ where the degree of freedom is $k$, and the $R^2$ is the coefficient of determination of the sub-model (对error term做关于自变量的线性回归): $$
\varepsilon^2_{t}=a_{0}+a_{1}x_{1}+\dots+\mu_{t}
$$
	3. Since this is a one-tail test, compare the test statistic with $\chi^2_{1-\alpha,k}$
## Serial Correlation ^95ab44

Under the serial correlation, the coefficient estimates is **invalid**, and the standard errors are **deflated**.
### Durbin-Watson (DW) Test
1. $H_0$: NO serial correlation at order $1$;
2. Test statistic: $$\text{DW}=\frac{\sum_{t=2}^T(\hat\epsilon_{t}-\hat\epsilon_{t-1})^2}{\sum_{t=1}^T \hat{\epsilon}_{t}^2}\approx 2(1-r)$$
3. Clearly, from the approximation, can be seen that DW test statistic close to 0 indicate perfectly positive correlation, and 4 indicate perfectly negative correlation.
The DW statistic cannot be appropriately used for a regression that has a lagged value of the dependent variable as one of the explanatory variables. To test for serial correlation, we need to examine the [[241116 Quantitative#^95ab44 |autocorrelation]].
### Breusch-Godfrey (BG) Test
Can detect autocorrelation up to order $p$.

## Multi-Collinearity
1. 影响: 不影响模型估算的系数的consistency,但是会使得估算系数的标准差变大(t-stat更小,更不容易拒绝$H_0$,更容易犯[[#^177ff8|Type II Error]]).估算的系数也变得极为不可靠和不准确
2. 检测:
	1. 传统来说:可以看是否每个系数都各自不显著,但是模型整体看则显著
	2. Independent Variables' Pairwise Correlation 存在较高的相关性
	3. VIF:
		1. A VIF above 10 indicates serious multicollinearity issues requiring correction;
		2. while a VIF above 5 warrants further investigation of the given variable.
		3. To test the multi-collinearity of $X_1$ with $X_2$ and $X_3$, build a sub-model $M_2$: $$x_{1}=\beta_{0}'+\beta_{1}'x_{2}+\beta_{2}'x_{3}+\epsilon$$ and the $VIF_{(X_1,X_2 \& X_3)}=\frac{1}{1-R^2_{M_{2}}}$ where $R^2_{M_2}$ is the coefficient of determination for $M_2$. 
