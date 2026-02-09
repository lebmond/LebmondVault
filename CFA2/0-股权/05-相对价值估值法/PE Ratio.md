---
aliases:
  - P/E Ratio
  - 市盈率
  - PE ratio
tags:
  - Equity
---
## Leading P/E
Leading P/E ratio use the future earnings for the next 12 months.
$$
\text{Leading P/E Ratio}=\frac{P_{0}}{\mathbb{E}[EPS_{1}]}=\frac{1-b}{r-g}
$$

# PVGO
$PVGO = P_{0}-\frac{\mathbb{E}[EPS_{1}]}{r_{E}}$ 
Can be used to calculate the P/E Ratio: $$\text{Leading P/E Ratio}=\frac{1}{r}+\frac{\text{PVGO}}{\mathbb{E}[E_{1}]}$$
# Normalizing PE Ratio
## Historical Average EPS
Calculate the [[PE Ratio]] by dividing price by historical average EPS:
1. Avereage PE ratio across the **most recent full cycle**
2. Did not account for changes in **business size**,可能使得PE Ratio偏大
## Average ROE
1. 使用最近一整个周期的[[ROE]] (Return on Equity),乘以股票的当前的每股账面价值(Book Value per share)来求出股票的EPS
2. 因为使用了每股账面价值,所以考虑到了公司体量的变动对于EPS的影响


# Portfolio PE Ratio
Portfolio or Index P/E Ratio is usually calculated as the **weighted harmonic mean P/E ratio** of constituent stocks.
$$
\text{Portfolio P/E Ratio}=\frac{1}{\sum_{i=1}^N\frac{W_{i}}{PE_{i}}}
$$
