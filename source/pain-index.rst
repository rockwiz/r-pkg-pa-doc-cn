PainIndex
=========

描述
    痛苦指数（pain index）是整个序列分析期间回撤的均值。该测度和Ulcer指数类似，除了回撤没有平方。它也不同于
    平均回撤，平均回撤的分子是所有观测数而非回撤个数

用法
::

    PainIndex(R, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :...: 其它要传入的参数

说明
    .. math::

        PainIndex=\sum^n_{i=1}\frac{\vert{D^{'}_i}\vert}{n}

    其中， n是序列观测样本数， :math:`D^{'}_i` 是第i期上个峰值后的回撤

参考
    Carl Bacon, Practical portfolio performance measurement and attribution, second edition 2008
    p.89, Becker, Thomas (2006) Zephyr Associates

范例
::

    data(portfolio_bacon)
    print(PainIndex(portfolio_bacon[,1])) #expected 0.04
    data(managers)
    print(PainIndex(100*managers[ 1996 ]))
    print(PainIndex(100*managers[ 1996 ,1]))


