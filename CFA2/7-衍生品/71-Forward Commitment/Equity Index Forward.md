---
tags:
  - Derivative
---
Equity Index Forward Contracts 与单只股票的forward contract不同,他假设index涵盖的所有的股票都在每时每刻不停地付出股息,因此他使用的是连续复利率和连续股息率来定价

# Pricing
连续复利率: $R_{f}^C=\ln(1+R_{f})$, 这里的$C$就代表了是连续复利,$R_f$是**一年期**的无风险利率
Forward Pricing = $$
FP_{0,T}=S_{0}\times \exp\{(R^C_{f}-\delta ^C)\times T\}
$$

## Valuation
Given an Equity Index Forward initiated at time $0$ with price of $FP_{0,T}$ and valuated at time $t$, its valuation formula is given by:
$$
\begin{align}
V_{t}&=\frac{FP_{t,T}-FP_{0,T}}{\exp\{R^C_{f}\cdot (T-t)\}}
\end{align}
$$