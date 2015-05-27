NetSelectivity
==============

描述
    超过所承担风险的超额收益

用法
::

    NetSelectivity(Ra, Rb, Rf = 0, ...)

参数
    :Ra: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rb: 一个基准资产收益的向量
    :Rf: 同时期无风险收益率
    :...: 其它要传入的参数

说明
    如果Netselectivity是负值，表明资产组合经理分散风险导致的损失不合理

    .. math::

        Netselectivity=\alpha-d

    其中， :math:`\alpha` 是选择能力， :math:`d` 是多元化

参考
    Carl Bacon, Practical portfolio performance measurement and attribution, second edition 2008 p.68

范例
::

    data(portfolio_bacon)
    print(NetSelectivity(portfolio_bacon[,1], portfolio_bacon[,2])) #expected -0.017
    data(managers)
    print(NetSelectivity(managers[ 1996 ,1], managers[ 1996 ,8]))
    print(NetSelectivity(managers[ 1996 ,1:5], managers[ 1996 ,8]))


