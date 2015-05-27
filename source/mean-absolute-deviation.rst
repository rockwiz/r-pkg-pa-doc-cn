MeanAbsoluteDeviation
=====================

描述
    收益和收益均值之间差的绝对值之和除以收益的次数

用法
::

    MeanAbsoluteDeviation(R, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :...: 其它要传入的参数

说明
    .. math::

        MeanAbsoluteDeviation=\frac{\Sigma^n_{i=1}\vert{r_i}-\overline{r}\vert}{n}

    其中，n是序列中观测样本数， :math:`r_i` 是第i个月的收益， :math:`\overline{r}` 是均值收益

参考
    Carl Bacon, Practical portfolio performance measurement and attribution, second edition 2008 p.62

范例
::

    data(portfolio_bacon)
    print(MeanAbsoluteDeviation(portfolio_bacon[,1])) #expected 0.0310
    data(managers)
    print(MeanAbsoluteDeviation(managers[ 1996 ]))
    print(MeanAbsoluteDeviation(managers[ 1996 ,1]))

