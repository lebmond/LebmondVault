---
aliases:
  - BG Test
---
The regression models to which the test can be applied include cases where lagged values of the dependent variables are used as independent variables in the model's representation for later observations (i.e. [[autocorrelation]])

Null Hypothesis: 不存在serial correlation 或者[[autocorrelation]]
先考虑如下的线性回归:
$$
Y_{t}=\beta_{0}+\vec{\beta}\vec{X_{t}}+\varepsilon_{t}
$$
如果怀疑误差服从AR($p$) 自回归模型,那么可以再fit一个新的线性回归:
$$
\hat{\mu_{t}}=\alpha_{0}+\vec{\alpha}\cdot\vec{X_{t}}+p_{1}\mu_{t-1}+p_{2}\mu_{t-2}+\dots+p_{p}\mu_{t-p}+e_{t}
$$
test statistics大约服从一个F distribution, 自由度为($n-p-k-1$,$p$)
