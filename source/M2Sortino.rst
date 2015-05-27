M2Sortino
=========

描述
    Sortino的M平方是适合下方风险而非总风险的M平方

用法
::

    M2Sortino(Ra, Rb, MAR = 0, ...)

参数
    :Ra: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rb: 基准收益向量
    :MAR: 最小可接受收益，与收益的周期性相同
    :...: 其它要传入的参数

说明
    .. math::

        M^2_S=r_p+Sortinoratio\times{(\sigma_{DM}-\sigma_D)}

    其中， :math:`M^2_S` 是Sortino的M平方， :math:`r_p` 是年化组合收益， :math:`\sigma_{DM}` 是基准年化下方风险，
    D是组合的年化下方风险

参考
    1. Carl Bacon, Practical portfolio performance measurement and attribution, second edition 2008 p.102-103

范例
::

    data(portfolio_bacon)
    MAR = 0.005
    print(M2Sortino(portfolio_bacon[,1], portfolio_bacon[,2], MAR)) #expected 0.1035
    data(managers)
    MAR = 0
    print(MSquaredExcess(managers[ 1996 ,1], managers[ 1996 ,8], MAR))
    print(MSquaredExcess(managers[ 1996 ,1:5], managers[ 1996 ,8], MAR))


