# Module 1
A $1\times 4$ FRA is a forward contract expires in 1 month, and the underlying is settled in **4** months (from now) with a **3-month** notional loan period. The underlying interest rate is **90-day MRR in 30 days from now**.

## Bond Futures Price
Bonds futures are quoted as the clean price, but the settlement price is the dirty price.
Bond futures contracts have more than one deliverable bond from the seller, and the seller usually only deliver the Cheapest to Deliver bond (after adjusting for the Conversion Factor, CF). ==Quoted== Future prices is obtained by the clean price of the bond divided by the CF.
# Module 2
![[Pasted image 20241103232555.png]]

## Black Scholes Merton Model
$$C=S_{0}N(d_{1})-e^{ -rT }KN(d_{2})$$
$$P=e^{ -rT }KN(-d_{2})-S_{0}N(-d_{1})$$
where $d_1=\frac{\left( ln(S_0/K)+\left( r-\gamma+\frac{\sigma^2}{2} \right)T \right)}{\sigma \sqrt{ T }}$ and $d_{2}=d_{1}-\sigma \sqrt{ T }$
Risk-neutral probability of going up = $\frac{e^{ rT }-d}{u-d}$ 
