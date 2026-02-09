For simplicity, we denote the currency longed as $A$, the currency paid/shorted as $B$. 


# Valuation
假如在$t=0$时刻进入的、$T$时刻到期的currency swap的两侧的fixed rate分别是$r_{a,0}$和$r_{b,0}$，那么在$t$时刻，该currency swap的（以货币$A$计价的）价值等于：做多的债券的价值减去以$t$时刻汇率计算的做空债券的价值：
$$
\begin{align}
V_{t}&=V_{{A,t}}-S_{A/B,t}V_{B,t}\\ \\
&=\mathcal{N}_{A}\left(r_{a,0}\sum_{i=1}^Tdf_{a,i}(1)+df_{a,T}(1)\right)-S_{A/B,t}\mathcal{N}_{B}\left(r_{b,0}\sum_{i=1}^Tdf_{b,i}(1)+df_{b,T}(1)\right)
\end{align}

$$
