---
tags:
  - MFM714
aliases:
  - LGD
Date: "240110"
---

> [!NOTE] Definition
> The percentage of the principle you loss given that the counterparty defaults.

Which is define as $1-(\text{Recovery Percentage})$. It is particularly depends on seniority and security.
- Seniority: The priority of reclaiming residuals when default happens. We usually have senior, subordinated, and junior, priority shares and common shares finally.
- Security: We said the debt is secured when the debt-holder has a claim on collateral, or specific assets. If the debt-holder only has a overall claim on entity's general assets, it is unsecured.
- LGD is almost always unknown, and is considered correlated with systemic risk, thus is usually meant by expected value of LGD. 

# Modeling LGD (or Recovery Rate)
## Independent Beta Distribution
It is popular to model stochastic LGD by subtract a Beta-distributed recovery rate. For Beta distribution, it is bounded within 0 and 1, and the shape of the distribution is determined by two parameters, $\alpha$ and $\beta$. Thus, **use different $\alpha$ and $\beta$ to characterize different types of bonds and loans' Recover Rate**. 
1. **Alpha (α)**: Alpha determines the ==shape of the distribution's peak==. When α is small, the peak of the distribution is closer to 0; as α increases, the peak moves towards 1. Therefore, higher values of α result in distributions that are skewed towards 1, while lower values of α produce distributions skewed towards 0.
2. **Beta (β)**: Beta influences the ==spread or width== of the distribution. Larger values of β result in distributions that are more concentrated around the mean, whereas smaller values of β lead to distributions that are more spread out.

### Formula:
$$LGD=1.1\times Beta\text{-Distributed r.v.}$$So that $LGD$ can go as high as 110% to include legal costs and other expenses. Or include the recovery rate in the formula: $$LGD=1.1\times (1-\text{Recovery Rate}\times Beta\text{-Distributed r.v.})$$
### Disadvantage:
No guarantee that LGD of different loans from the same defaulted company maintain appropriate monotonicity (can be overcome by the following model)

## Recursive Beta Distribution
LGD for the first priority asset is not guaranteed to be lower than that for a second priority asset. Thus, can model LGD in another way:
$$\begin{aligned}LGD_{\text{senior secured}}&=1-\beta_1\\LGD_{\text{senior unsecured}}&=1-\beta_1\beta_2\\LGD_{\text{subordinated secured}}&=1-\beta_1\beta_2\beta_3\\&\cdots\\\end{aligned}$$
The distribution for $\beta_2$ and $\beta_3$, etc. can be bootstrapped to fit observed data.
## Considering Systemic Risk
If needed, can calibrate to the bad economic period.