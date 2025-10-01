---
tags:
  - MFM714
Date: 2024-03-06
url: https://www.ijcb.org/journal/ijcb09q3a7.pdf
---
## Quantify Plausibility
Good practice in stress testing is to identify scenarios which have harmful implications for the portfolio and at the same time are not completely implausible. 
$r = (r1,\cdots, rn)$  are $n$ macro risk factors. These macro risk factor changes are distributed elliptically with covariance matrix $Cov$ and expectations $\mu$. Can think elliptical distribution as a more generalized version of multivariate normal distribution. 
### $MaxLoss$ (Previous Way)
Earlier work on MaxLoss defined plausibility in terms of the **probability mass** of the ellipsoid of all scenarios of equal or lower Maha. For example, MaxLoss was taken to be the worst loss among all scenarios within an ellipsoid of probability mass 0.95. 

But the probability mass of a ellipsoid of radius $k$:
$$
\int_{Maha(r)\leq k}f(r)d(r)=\frac{\pi^{n/2}}{\Gamma(n/2)}\int_0^{k^2}t^{\frac{n}{2}-1}g(t)dt$$is dependent on $n$, the number of macro risk factors we are considering. Fixing $k$, the dimension of our ellipsoid, increasing $n$ will decrease the probability mass.

### Maha Distance
Use Mahalanobis distance to quantify the plausibility of scenarios:
$$
Maha(r):=\sqrt{(r-\mu)^TCov^{-1}(r-\mu)}
$$
where $r = (r1,\cdots, rn)$  are $n$ macro risk factors. $Maha(r)$ can be interpreted as the number of standard deviations of the multivariate move from µ to r. $Maha$ takes into account the correlation structure between the risk factors. A high value of $Maha$ implies a low plausibility of the scenario r.

## Partial Scenario
A macro stress scenario is partial if ==it fixes the values of some but not all macro risk factors==. Let us call the risk factors whose value is specified by the partial macro scenario ‘the fixed risk factors’. 
	For example, in the scenario ‘The e falls by 20% against the CHF’ the fixed risk factor is the CHF/e rate. 
	
The standard stress testing procedure then is to analyse the implications of the scenario for the expected portfolio value, or for risk captial, or for capital ratios. 
A macro scenario typically is a partial scenario. It does not determine a unique portfolio value because it does not fix the values of the idiosyncratic risk factors. 

### Four Conditional Stress Distributions
- A) The conditional profit distribution given the macro scenario rA, in which the fixed risk factors have the value specified by the partial scenario, and the other macro risk factors remain at their **last observed value**. 
- (B) The conditional profit distribution given the macro scenario rB, in which the fixed risk factors have the value specified by the partial scenario, and the other macro risk factors take their **unconditional expectation** value. 
- (C) The conditional profit distribution given the macro scenario rC , in which the fixed risk factors have the value specified by the partial scenario, and the other macro risk factors take their **conditional expected value** given the values of the fixed risk factors. 
- (D) The conditional profit distribution given the partial macro scenario rD, in which the fixed risk factors have their value specified by the partial scenario, and the other macro factors are distributed according to the marginal distribution given the values of the fixed risk factors.
