---
tags:
  - Derivative
---
## Valuation
对于一个付固定利率（类比做空一个债券）换取equity return（类比做多equity）的交易方，equity swap的估值如下：
$$
\begin{align}
V_{t}=\left[\frac{P_{t}}{P_{t^-}}-(c\sum_{i=1}^Tdf_{i}(1)+1\cdot df_{T}(1)\right]\cdot\mathcal{N}
\end{align}
$$
Where $P_t$ is the current price of the equity, and $P_{t^-}$ is the price of the equity on **last reset date**.