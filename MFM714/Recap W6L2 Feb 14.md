---
tags:
  - MFM714
  - Recap
Date: "240214"
Page: "67"
---
# SA-CCR
Standardized Approach for Counterparty Credit Risk:
$$\begin{aligned}&\text{Exposure at default under SA}\\=& [Exposure At Default|EAD]\\=&\alpha\times (RC+ PFE)\end{aligned}$$
Terminology:
1. EE: expected [[exposure]], the average of $max(0,\text{Mark to Market})$.
2. EPE: expected positive [[exposure]]: time average of EE up to the time horizon of interest.
	1. Need to consider time horizon of interest. There is no reason to defer profits for potential exposure in a distant future.
3. Effective EE: the EE that did not recognize decline occurring before the horizon of interest ends.
4. Effective EPE: Time-weighted average of Effective EE.

# Wrong-way Risk

> [!Note] Definition
> The wrong-way risk characterize the risk that counterparty's credit quality and the financial institution's exposure to them move in a different direction.

The risks that arises when %%market factors%% both increase the [[exposure]] and deteriorate the counterparty credit quality at the same time.
- Example: suppose the financial institution involves in a oil commodity swap with an oil producer, and the former pays floating rate and the latter pays fixed rate. When the oil price goes up, the oil producer's financial status improves and they can receive more from the commodity swap. Thus, the exposure decreases as the credit quality increases and vice versa. This is an example of wrong-way risk
## Quantify Wrong-Way Risk
Use [[exposure]] conditioning on whether the counterparty default so that can work with distributions of exposure under different scenarios.
Use [[Probability of Default|PD]] conditional on adverse market movements.
Use higher value of $\alpha$, the regulator coefficient.