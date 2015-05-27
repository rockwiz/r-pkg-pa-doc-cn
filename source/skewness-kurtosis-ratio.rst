SkewnessKurtosisRatio
=====================

描述
    Skewness-Kurtosis比率即偏度峰度比

用法
::

    SkewnessKurtosisRatio(R, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :...: 其它要传递的参数

说明
    和夏普比率一起评定组合级别。值越高越好

    .. math::

        SkewnessKurtosisRatio(R, M AR)=\frac{S}{K}

    其中， S是偏度，K是峰度

参考
    Carl Bacon, Practical portfolio performance measurement and attribution, second edition 2008 p.100

范例
::

    data(portfolio_bacon)
    print(SkewnessKurtosisRatio(portfolio_bacon[,1])) #expected -0.034

    data(managers)
    print(SkewnessKurtosisRatio(managers[ 1996 ]))
    print(SkewnessKurtosisRatio(managers[ 1996 ,1]))

