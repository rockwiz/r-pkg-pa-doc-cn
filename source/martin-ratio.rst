MartinRatio
===========

描述
    将组合收益与无风险利率间的差除以Ulcer指数得到Martin比率

用法
::

    MartinRatio(R, Rf = 0, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rf: 同时期无风险收益率
    :...: 其它要传入的参数

说明
    .. math::

        MartinRatio=\frac{r_P-r_F}{\sqrt{\Sigma^n_{i=1}\frac{{D^{'}_i}^2}{n}}}

    其中， :math:`r_P` 是组合年化收益， :math:`r_F` 是无风险收益率， n是序列中观测点数量，
    :math:`D^{'}_i` 是第i期上个峰值后的回撤

参考
    1. Carl Bacon, Practical portfolio performance measurement and attribution, second edition 2008 p.91

范例
::

    data(portfolio_bacon)
    print(MartinRatio(portfolio_bacon[,1])) #expected 1.70
    data(managers)
    print(MartinRatio(managers[ 1996 ]))
    print(MartinRatio(managers[ 1996 ,1]))

