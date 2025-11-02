---
aliases:
  - AR Model
  - 自回归模型
---

即使用因变量的过去值来预计未来的因变量 a p-order AR model is given by:
$\text{AR}(p):\ \ x_{t} = b_{0}+b_{1}x_{t-1}+b_{2}x_{t-2}+b_{p}x_{t-p}+\epsilon_{t}$ 

如果想使用Oridinary Least Square的方法来计算AR模型,那么需要满足以下三个条件:
1. 时间序列是[[Covariance Stationary]]的;
2. 误差项之间uncorrelated;
3. 误差项符合homoskedasticity (error term variance are time-independent)
