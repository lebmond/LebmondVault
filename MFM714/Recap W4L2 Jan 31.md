---
tags:
  - MFM714
  - Recap
Date: "240131"
Page: "54"
---
# Price Setting for Each Loan
Need to use "RAROC" (Return Adjusted Return on Capital) to set the interest rate to charge the client.
$$RAROC=\frac{r-e-EL+IFC}{c},$$ where $r$ is $\text{Revenue}$,  $e$ is Expenses, $EL$ is the expected loss, $IFC$ is the Income from capital (capital charged * risk-free rate), $c$ is the Capital level.

Loan amount $\times$ capital rate needed $=$ capital needed (in dollar amount)
capital needed $\times$ RAROC = interests (in dollar amount) to be earned from the client.
The interest rate need to charge: $$\frac{\text{Interests amount to be earned}}{\text{Loan Amount}}+\text{risk-free rate}$$

Questions: what capital rate is needed? 

# Strategy to determine [[Capital]] Needed
### Incremental
$$\begin{aligned}\text{Capital Needed for the new loan} &= \\VaR_{99.5\%}(\Pi|\text{With new deal})&`-VaR_{99.5\%}(\Pi|\text{Without new deal})\end{aligned}$$
## TD Method: Proportional to asset's standalone standard deviation of loss
1. Calculate the standalone s.d. for all asset: $$\sigma_i=N_i\cdot LGD_i\sqrt{PD_i(1-PD_i)}$$
2. Match standalone s.d. with overall [[capital]] charged:$$\lambda\sum_{i}\sigma_i=\text{Total Capital}$$
3. [[Capital]] allocated for each asset is proportional to each asset's standard deviation: $$\lambda\cdot LGD_i\sqrt{PD_i(1-PD_i)}$$
4. Consider maturity difference: (the capital allocation difference must be higher between A and B should be higher than that between C and D, where A has maturity of 1 month, B of 6 month, C of 20year1month, and D of 20year6month)
5. Consider the industrial concentration factor: double the size of exposure in an industry should be allocated more the doubled capital.
