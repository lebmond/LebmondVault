
# Module 2
![[Pasted image 20241103232555.png]]

## Black Scholes Merton Model
$$C=S_{0}N(d_{1})-e^{ -rT }KN(d_{2})$$
$$P=e^{ -rT }KN(-d_{2})-S_{0}N(-d_{1})$$
where $d_1=\frac{\left( ln(S_0/K)+\left( r-\gamma+\frac{\sigma^2}{2} \right)T \right)}{\sigma \sqrt{ T }}$ and $d_{2}=d_{1}-\sigma \sqrt{ T }$
Risk-neutral probability of going up = $\frac{e^{ rT }-d}{u-d}$ 
