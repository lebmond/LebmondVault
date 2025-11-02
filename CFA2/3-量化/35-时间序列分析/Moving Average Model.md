---
aliases:
  - MA Model
---
使用过去的error来预测未来的自己
$$\begin{aligned}
\text{MA}(q): x_{t}=\epsilon_{t}+\sum_{i=1}^q\theta_{i}\epsilon_{t-i}
\end{aligned}$$where $E[\epsilon_t]=0$, $E[\epsilon_t^2]=\sigma^2$, $Cov(\epsilon_t,\epsilon_s)=0$ for $t\not=s$ 