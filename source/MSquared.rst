MSquared
========

描述
    散度（M squared）是一种用于判断不同组合间相对绩效大小风险调整收益，利用散度可以在不同风险水平上比较组合

用法
::

    MSquared(Ra, Rb, Rf = 0, ...)

参数
    :Ra: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rb: 一个基准资产收益的向量
    :Rf: 同时期无风险收益率
    :...: 其它要传入的参数

说明
    .. math::

        M^2=r_P+SR\times(\sigma_M-\sigma_P)=(r_P-r_F)\times\frac{\sigma_M}{\sigma_P}+r_F

    其中， :math:`r_P` 是组合年化收益， :math:`\sigma_M` 是市场风险， :math:`\sigma_P` 是组合风险

参考
    Carl Bacon, Practical portfolio performance measurement and attribution, second edition 2008 p.67-68

范例
::

    data(portfolio_bacon)
    print(MSquared(portfolio_bacon[,1], portfolio_bacon[,2])) #expected 0.10062
    data(managers)
    print(MSquared(managers[ 1996 ,1], managers[ 1996 ,8]))
    print(MSquared(managers[ 1996 ,1:5], managers[ 1996 ,8]))

