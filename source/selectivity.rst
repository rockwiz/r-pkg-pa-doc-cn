Selectivity
===========
描述
    Selectivity和詹森alpha一样

用法
::

    Selectivity(Ra, Rb, Rf = 0, ...)

参数
    :Ra: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rb: 基准资产的收益向量
    :Rf: 与收益同时期的无风险收益率
    :...: 传入的任何其它参数

说明
    .. math::

        Selectivity=r_p-r_f-\beta_p\times{(b-rf)}

    其中， :math:`r_f` 是无风险收益率， :math:`\beta_r` 是回归beta， :math:`r_p` 是组合收益，b是基准收益

参考
    Carl Bacon, Practical portfolio performance measurement and attribution, second edition 2008 p.78

范例
::

    data(portfolio_bacon)
    print(Selectivity(portfolio_bacon[,1], portfolio_bacon[,2])) #expected -0.0141
    data(managers)
    print(Selectivity(managers[ 1996 ,1], managers[ 1996 ,8]))
    print(Selectivity(managers[ 1996 ,1:5], managers[ 1996 ,8]))


