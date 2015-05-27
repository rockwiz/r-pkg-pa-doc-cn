AdjustedSharpeRatio
===================

描述
    调整夏普比率由Pezier和White于2006年引入，通过一个结合负偏度和超峰度的惩罚因子来调整偏度和峰度。

用法
::

    AdjustedSharpeRatio(R, Rf = 0, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo、xts对象
    :Rf: 无风险收益率
    :...: 其它要传入的参数

细节
    .. math::

        AdjustedSharpeRatio=SR\times[1+(\frac{S}{6})\times{SR}-(\frac{K-3}{24})\times{SR}^2]

参考
    Carl Bacon, Practical portfolio performance measurement and attribution, second edition 2008 p.99

范例
::

    data(portfolio_bacon)
    print(AdjustedSharpeRatio(portfolio_bacon[,1])) #expected 0.81
    data(managers)
    print(AdjustedSharpeRatio(managers[ 1996 ]))
    print(AdjustedSharpeRatio(managers[ 1996 ,1]))

