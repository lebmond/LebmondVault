指的是模型的残值之间存在了相关性$Cov_{\varepsilon_{i},\varepsilon_{i+1}}\not=0$
会使得系数的标准差的估算**偏小**,在对系数进行t test的时候会使得t-stat变大,从而更容易拒绝一个Null Hypothesis,更容易犯[[Type I Error]], 去真.

| If Independent Variable Contains <br>Lag Value of Dependent Variable | Valid Coefficients' Estimate | Valid Coefficients'<br>Standard Deviation |
| :------------------------------------------------------------------: | :--------------------------: | :---------------------------------------: |
|                                  No                                  |             Yes              |                    No                     |
|                                 Yes                                  |              No              |                    No                     |
如果是第二种情况,则为时间序列,此时不能使用[[Durbin-Waston Test|DW Test]]来检测Serial Correlation,而应当使用[[Breusch-Godfrey Test|BG Test]]来检查他们的[[Autocorrelation]]

# 检测方法
## [[Durbin-Waston Test|DW Test]]

## [[Breusch-Godfrey Test|BG Test]]