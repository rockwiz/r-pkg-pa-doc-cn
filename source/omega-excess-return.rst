OmegaExcessReturn
=================

描述
    Omega超额收益是另一种形式的下方风险调整收益。基准风格的下方方差乘以3倍的beta风格

用法
::

    OmegaExcessReturn(Ra, Rb, MAR = 0, ...)

参数
    :Ra: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rb: 一个基准资产收益的向量
    :MAR: 最小可接受收益
    :...: 其它要传入的参数

说明
    .. math::

        \omega=r_P-3\times\beta_S\times{\sigma_{MD}}^2

    其中， :math:`\omega` 是超额收益， :math:`\beta` 是风格beta， :math:`\sigma_D` 是组合年化下方风险，
    :math:`\sigma_{MD}` 是基准年化下方风险

参考
    Carl Bacon, Practical portfolio performance measurement and attribution, second edition 2008 p.103

范例
::

    data(portfolio_bacon)
    MAR = 0.005
    print(OmegaExcessReturn(portfolio_bacon[,1], portfolio_bacon[,2], MAR)) #expected 0.0805
    data(managers)
    MAR = 0
    print(OmegaExcessReturn(managers[ 1996 ,1], managers[ 1996 ,8], MAR))
    print(OmegaExcessReturn(managers[ 1996 ,1:5], managers[ 1996 ,8], MAR))


