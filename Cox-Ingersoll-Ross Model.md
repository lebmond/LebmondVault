---
aliases:
  - CIR Model
tags:
  - CFA
  - InterestRate
  - Fixed_Income
---
CIR model is an [[Equilibrium Interest Model]] and is mean reverting. 
The variance of rate changes differs depending on the level of rates (for a higher interest rates, the volatility is higher)

$$dr_{t}=k(\theta-r_{t})dt + \sigma \sqrt{ r_{t} }dZ$$Unlike [[Vasicek Model]], CIR model assumes **volatility to be a function of short rate** and does not permit negative interest rate.