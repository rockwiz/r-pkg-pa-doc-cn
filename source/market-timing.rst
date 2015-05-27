MarketTiming
============

描述
    允许估计Treynor-Mazuy（T-M）或Merton-Henriksson（M-H）市场时机选择模型。T-M模型本质上是基本CAPM的二次扩展，
    它用多次回归来估计。回归中的第二个概念是超额收益平方，如果回归中gamma系数为正，则估计的方程描述了一个向上倾斜的“凸”回归线。
    二次回归为：

    .. math::

        R_p-R_f=\alpha+\beta(R_b-R_f)+\gamma{(R_b-R_f)}^2+\epsilon_p

用法
::

    MarketTiming(Ra, Rb, Rf = 0, method = c("TM", "HM"))

参数
    :Ra: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rb: 一个基准资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rf: 同时期无风险收益率
    :method: 选择T-M模型还是M-H模型：

            * TM - Treynor-Mazuy模型
            * HM - Henriksson-Merton模型

            默认选择Treynor-Mazuy模型

    :...: 其它要传入的参数

说明
    M-H模型的基本思路是执行因变量的多次回归。当市场超额收益小于等于零时，第二个变量为零；否则，为1

    .. math::

        R_p-R_f=\alpha+\beta(R_b-R_f)+\gamma{D}+\epsilon_p

    其中， 所有变量都和CAPM中，除了 :math:`D=max(0,R_b-R_f)`

参考
    1. J. Christopherson, D. Carino, W. Ferson. Portfolio Performance Measurement and Benchmarking. 2009. McGraw-Hill, p. 127-133.
    2. J. L. Treynor and K. Mazuy, "Can Mutual Funds Outguess the Market?" Harvard Business Review, vol44, 1966, pp. 131-136
    3. Roy D. Henriksson and Robert C. Merton, "On Market Timing and Investment Performance. II.
    4. Statistical Procedures for Evaluating Forecast Skills," Journal of Business, vol.54, October 1981, pp.513-533


另见
    CAPM.beta

范例
::

    data(managers)
    MarketTiming(managers[,1], managers[,8], Rf=.035/12, method = "HM")
    MarketTiming(managers[80:120,1:6], managers[80:120,7], managers[80:120,10])
    MarketTiming(managers[80:120,1:6], managers[80:120,8:7], managers[80:120,10], method = "TM")


