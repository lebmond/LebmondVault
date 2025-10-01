# 1. Merton model:

Consider equity as an perpetual **American call** option on the value of the firm, strike price $K$ is the corporation Liability.

Default occur when the option falls out-of-the-money (i.e. **Asset** < **Liability** or other default threshold)

> [!NOTE] NOTE
> Better in theory than in practice

# 2. Moody's KMV
Industry Leader of such type of model. Measure the "distance to default".
## Default Level $L$
Roughly equal to all short-term debt + half of the long-term debt
## Distance to Default, $d_2$
$$
d_2=\frac{ln(\text{Asset}/L)}{\sigma\sqrt{\tau}}
$$
where $\tau$ is some appropriate time horizon.