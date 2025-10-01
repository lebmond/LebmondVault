---
tags:
  - MFM714
  - Recap
Page: "64"
Date: "20240212"
---
# Collateral 

> [!NOTE] Definition
> Assets or property pledged by a borrower to a lender, serving as a guarantee that the lender can seize and sell in the event of default to recover the outstanding debt.

Usual form: cash or government securities. In the setting of credit risk, collateral is used to offset potential default in the future.

## Up-Front Collateral
A pre-determined fixed amount of collateral that is pledged at the beginning of the loan.

## Variational Collateral
The amount of collateral changes as the market-to-market value change.
Can be either:
- Match the [[Exposure]] exactly;
- Grant some open [[Exposure]] ($Margin < Exposure$);
- Excess collateral (overcollateralization).
	- Offset at least partial amount of close out risk.

To model this, use nested Monte Carlo Simulation. The outer Monte Carlo simulation iterates through quarterly basis and the inner simulation iterates through 10-day movement measure. That means we calculate the how the exposure can change in 10 days on a quarterly basis[^1].

We also consider the threshold and minimum transfer amount:
- Threshold: the client does not need to pledge any collateral until reach this $threshold$.
- Minimum Transfer amount: the incremental amount of lump-sum pledge every time the obligator needs to pledge more collateral.
## Netting Collateral
Putting multiple collateralized contract together under the Credit Support Annex to avoid necessary multiple pledges made to different counterparty.

# Counterparty Credit Risk and Capital
This section discusses how can we fit a derivative's credit risk into the credit risk model by determining how much capital should be put.
1. Ideal approach: "all-singing all-dancing model", doing a comprehensive simulation on the market with consideration of many factors like collateral, correlated migration, [[Loss Given Default|LGD]], [[Exposure At Default|EAD]], etc.
2. CVA
3. Loan Equivalent Amount:
> [!Definition]
>    the loan equivalent amount represents the notional value of the underlying credit exposure that the derivative contract is referencing

## Regulator's Way to Get LEA
$=\text{Average Exposure}\times\text{Multiplier}$, where the $\text{Multiplier}$ is generally 1.2 to 1.4, determined by the regulators worldwide.

## Lozinski's TD Way to Get LEA
Equating the variance of a derivative's loss and the variance of a loan's lose to determine the derivative's LEA.
- Variance of a loan's loss: $Var(Loss)=N^2\cdot LGD^2\cdot p\cdot (1-p)$ 
- Similarly, variance of Derivative loss: $Var(Loss)=LEQ^2\cdot LGD^2\cdot p\cdot (1-p)$ 
- Variance of Actual Derivative loss: $Var(Derivative)=\mathbb{E}[\text{Exposure}]^2\cdot LGD^2\cdot p\cdot (1-p)+p\cdot Var(\text{Exposure})\cdot LGD^2$
- Equate them to get the LEQ

[^1]: This basis can also be unequal gap, like measure 10-day exposure process on a more frequent basis. 