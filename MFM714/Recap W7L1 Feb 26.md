---
tags:
  - MFM714
  - Recap
Date: 2024-03-04
---
# Pricing the Credit-Risky Assets
We can use the discounted risk-neutral expectation of the asset prices to calculate the present values or present prices of these assets (as we have talked last term, these risk-neutral prices under Q-space is identical to the P-space prices). Thus, their formulas are given by: $$V(t)=\mathcal N\left[e^{-R(T-t)}[1-PD^\mathbb Q_t(T)]+PD^\mathbb Q_t(T)(1-LGD)e^{-R(T^*-t)}\right]$$
If we use $T$ to  approximate $T^*$, we can get the bond price is actually equal to %% its bond price discounted by risk free rate plus some spread %% :$$V(t)=\mathcal N e^{-(R+S)(T-t)}$$ Here, the spread $S$ is determined by $LGD\times PD$, the risk neutral expected loss $E^\mathbb Q[\text{loss}]$ . We normally **assume** that $PD$ and $LGD$ are identical within the firm range, thus we can use one (or multiple) observed assets value to value $PD$ and $LGD$ and further price any other credit risky instruments issued by the same firm.
## Problems
- Hard to create replicate hedges
- Hard to evaluate $PD$ and $LGD$, respectively

# Hazard Rate
Aggregate the time structure of yield into the discount factors, $r(t)$, instantaneous continuously compounding rate. For risk free assets, the grow in value must follow: $$dV=r(t)Vdt$$
In a similar manner, We can define the proportion of defaulted companies by time T as $S_t(T)$ and call it survival function. This process can be approximate by the observed cumulative frequency of defaulted companies to time T. Thus, we can take the partial derivative of proportion of comparable firms dying at at each time step to get the hazard rate, given by: $$\lambda(t)=-\frac{\frac{dS_t(t)}{dt}}{S_t}$$ This hazard rate is the instantaneous percentage rates of firm defaulting.
Thus, the probability of default from time $t$ to time $T$, $PD_t(T)$ is given by:$$PD_t(T)=1-exp\left\{-\int_t^T\lambda(s)ds\right\}$$
## Shorten Rate
If instead of modeling the proportion of defaulted companies, the proportion of defaulted amount is modeled, then we can get $PD\times LGD$  process together in a manner similar to the hazard rate above. Taking the partial derivative with respect to time $t$, we can get the **instantaneous percentage rates of defaulting**, call it $h(t)$.$$PD_t(T)\times LGD_t(T)=1-exp\left\{-\int_t^Th(s)ds\right\}$$