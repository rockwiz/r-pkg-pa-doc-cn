CAPM.CML.slope
==============

描述
    资本资产定价模型，源自流行的夏普比率（SharpeRatio），是一种市场均衡理论。这些实用函数提供CAPM中提出的各种度量的值。

用法
::

    CAPM.CML.slope(Rb, Rf = 0 )
    CAPM.CML(Ra, Rb, Rf = 0)
    CAPM.RiskPremium(Ra, Rf = 0)
    CAPM.SML.slope(Rb, Rf = 0)

参数
    :Ra: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rb: 基准资产的收益向量
    :Rf: 与收益同时期的无风险收益率

说明
    通过假设不在效率前沿的资产要么升高要么降低其价格直到处于市场组合的效率前沿，CAPM提供了被动或指数投资的理由。

    一项投资的CAPM风险溢价是资产绩效在多大程度上与无风险收益率不同的度量。负的风险溢价通常指投资是一项坏投资，
    资金应该分配到无风险资产或有较高风险溢价的资产上。

    资本市场线（Capital Market Line，CML）将一个有效率市场组合的超额预期收益与它的风险联系起来。
    CML的斜率是该市场组合的夏普比率（Sharpe Ratio）。证券市场线（Security Market line，SML）通过计算风险溢价对CAPM.beta的线性来构造。
    对基准资产，它将为1。CML也描述了一个投资组合绩效超出效率前沿CAPM允许的唯一途径：它描述一个杠杆化组合将占据的回报/风险线。
    因此，按照CAPM，没有以相同资产构造的组合能够处于CML之上。

    可能对CAPM在实际中（与其结构上的或理论上的批评相反）的最完全的批评是它假设市场均衡，但最常用一个部分均衡设置，
    例如通过利用S&P500作为基准资产。使用和检验CAPM的较好方法是用从所有资产类别中考虑全面资产的一般均衡模型。

    Ruppert(2004)的第七章给出了CAPM的广泛概述，它的假设和不足。CAPM.RiskPremium是返回给投资者的相对无风险资产的溢价：

    .. math::

        \overline{(R_\alpha-R_f)}

    CAPM.CML计算资产相对基准资本市场线的预期收益，CAPM.CML.slope计算资本市场线的斜率以查看一项特定资产与CML相比的情况，
    CAPM.SML.slope 计算证券市场线的斜率以查看一项特定资产与基准创建的SML相比较如何。

参考

* Sharpe, W.F. The Sharpe Ratio,Journal of Portfolio Management,Fall 1994, 49-58.
* Sharpe,W.F. Capital Asset Prices: A theory of market equilibrium under conditions of risk. Journal of finance, vol 19, 1964, 425-442.
* Ruppert, David. Statistics and Finance, an Introduction. Springer. 2004.

另见
    CAPM.beta CAPM.alpha SharpeRatio InformationRatio TrackingError ActivePremium

范例
::

    data(managers)
    CAPM.CML.slope(managers[,"SP500 TR",drop=FALSE], managers[,10,drop=FALSE])
    CAPM.CML(managers[,"HAM1",drop=FALSE], managers[,"SP500 TR",drop=FALSE], Rf=0)
    CAPM.RiskPremium(managers[,"SP500 TR",drop=FALSE], Rf=0)
    CAPM.RiskPremium(managers[,"HAM1",drop=FALSE], Rf=0)
    CAPM.SML.slope(managers[,"SP500 TR",drop=FALSE], Rf=0)
    # should create plots like in Ruppert 7.1 7.2

