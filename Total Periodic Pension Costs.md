也被称为Periodic Pension Costs,他是养老金当期产生的所有剔除Employer Contribution后的**支出减去收益**(所以可以得到定义式:TPPC=ending funded status - beginning funded status - Employer Contribution)

US GAAP和IFRS下,plan assets和PBO的内容是一样的, 所以他们的total periodic pension costs也是一样的,但是把他们放在利润表和放在OCI的处理是不一样的.因此Total Periodic Pension 要么被记入利润表,要么被记入OCI,.所以我们也可以得到公式: 
TPPC = Periodic Pension Cost in I/S + Periodic Pension Cost in OCI

如果展开这个公式,我们可以得到:

> [!Note] TPPC
> TPPC = CSC + PSC + Interest Costs - Actual return - Acturial Gain
# IFRS
## 利润表
在IFRS下,以下内容走利润表:
1. Service Cost
	1. Current Service Cost
	2. Past Service Cost
2. Net Interest Expense/Income $(\text{PBA}_{\text{Beg}} - \text{PBO}_{\text{Beg}}) * r$
	1. Interest Cost
	2. Expected Return: 预期收益率使用和interst cost相同的折现率
## 其他综合收益
IFRS下,总共有两项,他们一起被称之为remeasurement:

> [!Summary] Remeasurement
> =精算益损+(实际收益-预期收益)

1. Actuarial gains and losses
2. 养老金基金实际收益和预期收益的差额(如果实际收益高于预期收益,那么应该表现为利润,在OCI里记录为正数)

# US GAAP
US GAAP在IFRS基础上额外增加三个知识点:
1. 使用expected return rate来计算养老金基金的预期收益(不一定等于interest rate的折现率)
2. Past Service Costs 先计入OCI,再摊销(如果大量的员工统一有追溯调整service cost,则按照IFRS的方法一年全部进入费用会使得公司当年的利润较差,不能准确反映公司当年的利润)
3. 当精算损益加上期望利润及实际利润的差值的和太大的时候,需要把OCI里的利润部分摊销到利润表中(如果长期来看OCI达到一个不可忽略的地步,则也可以在利润表里确认收入 )