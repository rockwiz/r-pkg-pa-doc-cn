CAPM.beta
=========

描述
    CAPM Beta 一项资产相对于初始投资组合的方差和协方差的beta值。用于确定潜在分散性。
    该函数用线性插值模型获得与BetaCoVariance中使用的符号模型相同的结果。

用法
::

    CAPM.beta(Ra, Rb, Rf = 0)
    CAPM.beta.bull(Ra, Rb, Rf = 0)
    CAPM.beta.bear(Ra, Rb, Rf = 0)
    TimingRatio(Ra, Rb, Rf = 0)

参数
    :Ra: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rb: 基准资产的收益向量
    :Rf: 与收益同时期的无风险收益率

说明

.. math::

    \beta_{a,b}=\frac{CoV_{a,b}}{\sigma_a}=\frac{\Sigma(R_a-\overline{R}_a)(R_b-\overline{R}_b)}{\Sigma(R_a-\overline{R}_a)}

Ruppert(2004) 报告该方程将给出Ra对Rb线性回归的估计斜率，而该斜率可用于确定风险溢价或超额预期收益。

两个其它函数分别应用最优拟合正的与负的市场收益的观点。CAPM.beta.bull是仅对正的市场收益的回归，它可用于理解资产或资产组合在正的
或“牛”市上的表现；而CAPM.beta.bear提供负的市场收益的计算。

TimingRatio能帮助评估经理资产配置决策的择时能力。该比率计算如下

.. math::

    TimeingRatio=\frac{\beta^+}{\beta_-}

在上涨市场，最好大于1；在下跌市场，最好小于1。

参考

* Sharpe,W.F. Capital Asset Prices: A theory of market equilibrium under conditions of risk. Journal of finance, vol 19, 1964, 425-442.
* Ruppert, David. Statistics and Finance, an Introduction. Springer. 2004.
* Bacon, Carl. Practical portfolio performance measurement and attribution. Wiley. 2004.

另见
    BetaCoVariance CAPM.alpha CAPM.utils

范例
::

    data(managers)
    CAPM.alpha(managers[,1,drop=FALSE], managers[,8,drop=FALSE], Rf=.035/12)
    CAPM.alpha(managers[,1,drop=FALSE], managers[,8,drop=FALSE], Rf = managers[,10,drop=FALSE])
    CAPM.alpha(managers[,1:6], managers[,8,drop=FALSE], Rf=.035/12)
    CAPM.alpha(managers[,1:6], managers[,8,drop=FALSE], Rf = managers[,10,drop=FALSE])
    CAPM.alpha(managers[,1:6], managers[,8:7,drop=FALSE], Rf=.035/12)
    CAPM.alpha(managers[,1:6], managers[,8:7,drop=FALSE], Rf = managers[,10,drop=FALSE])
    CAPM.beta(managers[, "HAM2", drop=FALSE], managers[, "SP500 TR", drop=FALSE], Rf = managers[, "US 3m TR", drop=FALSE])
    CAPM.beta.bull(managers[, "HAM2", drop=FALSE], managers[, "SP500 TR", drop=FALSE], Rf = managers[, "US 3m TR", drop=FALSE])
    CAPM.beta.bear(managers[, "HAM2", drop=FALSE], managers[, "SP500 TR", drop=FALSE], Rf = managers[, "US 3m TR", drop=FALSE])

    TimingRatio(managers[, "HAM2", drop=FALSE], managers[, "SP500 TR", drop=FALSE], Rf = managers[, "US 3m TR", drop=FALSE])

    chart.Regression(managers[, "HAM2", drop=FALSE], managers[, "SP500 TR", drop=FALSE],
                     Rf = managers[, "US 3m TR", drop=FALSE], fit="conditional", main="Conditional Beta")



