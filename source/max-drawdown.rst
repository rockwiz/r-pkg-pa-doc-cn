maxDrawdown
===========

描述
    从峰值权益中计算最大回撤。要发现收益序列中的最大回撤（drawdown），需要首先计算累积收益和到该点的最大累积收益。任何时候，
    当累积收益跌破到最大累积收益以下时，它就是一个回撤。回撤度量为最大累积收益的百分比，实际上，即从峰值权益度量

用法
::

    maxDrawdown(R, weights=NULL, geometric = TRUE, invert=TRUE, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :weights: 组合权重向量，缺省为NULL，参见说明部分
    :geometric: 生成几何（TRUE）或简单（FALSE）收益，缺省为TRUE
    :invert: TRUE/FALSE，是否反转回撤度量。参见说明部分
    :...: 其它要传入的参数

说明
    针对度量的invert 选项将调和理论与实践工作者。缺省选项invert=TRUE 将以一个正数提供回撤值。这有助于优化（通常是要获得一个最小值）
    和表格（每个数字前的负号会被认为是杂物7）。实践工作者会争辩说回撤意味损失，应该内在地与分位数（一个负数）保持一致，此处，
    invert=FALSE 将提供他们想要的值。个别地，不同的偏好选项可应用于图表的清晰化与紧凑化。正因如此，我们提供了选项，
    但对哪种方式更好不做判断。

参考
    Bacon, C. Practical Portfolio Performance Measurement and Attribution. Wiley. 2004. p. 88

另见
    findDrawdowns sortDrawdowns table.Drawdowns table.DownsideRisk chart.Drawdown

范例
::

    data(edhec)
    t(round(maxDrawdown(edhec[,"Funds of Funds"]),4))
    data(managers)
    t(round(maxDrawdown(managers),4))

