# Forward
远期的价格不会变化，但是他的价值会在确定当天等于0、之后则随市场波动而变化。
### 定价公式
对于一个在$0$时刻确定的在$T$时刻到期的远期，他的（到期的交割）价格为：
$$
FP_{0,T}=S_{0}(1+r)^T-\sum FV_{T}(\text{Carrying Benefits})+\sum FV_{T}(\text{Carrying Costs})
$$
Carrying Benefits：如果标的物是股票，那么Carrying Benefits可以是dividend。如果标的物是老母鸡，则Carrying Benefits是老母鸡的蛋。
Carrying Costs：如果标的物是经济作物，那么Carrying Costs可以是存储这些作物所需要的仓库等条件的维持费用。

其定价公式假设了套利机会不存在。但是如果套利机会存在，则可以采取买低卖高的策略：
[[Cash-and-Carry Arbitrage]]
### 估值公式
对于一个在$0$时刻进入的远期合约，他的$t$时刻的价值等于:
$$
V_{t}=\frac{FP_{t,T}-FP_{{0,T}}}{(1+r)^{(T-t)}}=S_{t}-\sum PV_{t}(\text{Carrying Benefits})+\sum PV_{t}(\text{Carrying Costs})-\frac{FP_{0,T}}{(1+r)^{T-t}}
$$

## [[Equity Index Forward]]

## [[Forward Rate Agreement]]

# Bond Futures Price
Bonds futures are quoted as the clean price, but the settlement price is the dirty price.
Bond futures contracts have more than one deliverable bond from the seller, and the seller usually only deliver the Cheapest to Deliver bond (after adjusting for the Conversion Factor, CF). ==Quoted== Future prices is obtained by the clean price of the bond divided by the CF.

# Swap
## [[Currency Swap]]
## [[Equity Swap]]