1. 影响: 不影响模型估算的系数的consistency,但是会使得估算系数的标准差变大(t-stat更小,更不容易拒绝$H_0$,更容易犯[[#^177ff8|Type II Error]]).估算的系数也变得极为不可靠和不准确
2. 检测:
	1. 传统来说:可以看是否每个系数都各自不显著,但是模型整体看则显著
	2. Independent Variables' Pairwise Correlation 存在较高的相关性
	3. VIF:
		1. A VIF above 10 indicates serious multicollinearity issues requiring correction;
		2. while a VIF above 5 warrants further investigation of the given variable.
		3. To test the multi-collinearity of $X_1$ with $X_2$ and $X_3$, build a sub-model $M_2$: $$x_{1}=\beta_{0}'+\beta_{1}'x_{2}+\beta_{2}'x_{3}+\epsilon$$ and the $VIF_{(X_1,X_2 \& X_3)}=\frac{1}{1-R^2_{M_{2}}}$ where $R^2_{M_2}$ is the coefficient of determination for $M_2$. 
