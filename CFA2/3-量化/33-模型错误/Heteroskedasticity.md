Heteroskedasticity refers to non-constant variance of the error terms.
 影响:Heteroskedasticity分为unconditional heteroskedasticity和conditional heteroskedasticity.第一种并不需要特别处理.但是第二种会给系数的估计带来**更大的**standard deviation.
## Unconditional Heteroskedasticity
一般来说不影响,模型中的残值存在没有规律的variance的变化

## Conditional Heteroskedasticity
需要处理
1. 不影响模型系数的[[一致性|consistent]]
2. 不影响模型系数的biased
3. 模型系数的标准差的估算biased
# 检测方式

1. 画Residual Plot
2. In Multi-linear regression, test heteroskedasticity with [[Breusch-Pagan Test|BP Test]]
3. In time series, test if a time series is [[ARCH Model|ARCH]](1):
   $$\epsilon_{t}^2=a_{0}+a_{1}\epsilon_{t-1}^2+\mu_{t}$$
   If $a_1$ is significantly different from 0, then time series is ARCH(1), and the variance of ARCH is given by:$$\hat{\sigma}_{t+1}^2=\hat{a}_{0}+\hat{a}_{1}\hat{\epsilon}_{t}^2$$

# 改正方式
计算robust standard errors 也被称为White-corrected standard errors和Heteroskedasticity-consistent errors, to correct the standard error of the estimated variables.