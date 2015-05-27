BernardoLedoitRatio
===================

描述
    取大于零的收益的子集的和，然后除以小于零的子集的和的相反数，得到BernardoLedoit比率

用法
::

    BernardoLedoitRatio(R, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo、xts对象
    :...: 其它要传入的参数

细节
    .. math::

        BernardoLedoitRatio(R)=\frac{\frac{1}{n}\Sigma^n_{t=1}max(R_t, 0)}{\frac{1}{n}\Sigma^n_{t=1}max(-R_t, 0)}

    其中，n是序列中观测样本数

参考
    Carl Bacon, Practical portfolio performance measurement and attribution, second edition 2008 p.95

范例
::

    data(portfolio_bacon)
    print(BernardoLedoitRatio(portfolio_bacon[,1])) #expected 1.78
    data(managers)
    print(BernardoLedoitRatio(managers[ 1996 ]))
    print(BernardoLedoitRatio(managers[ 1996 ,1])) #expected 4.598

