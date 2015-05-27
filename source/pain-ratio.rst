PainRatio
=========

描述
    痛苦比率（Pain Ratio）等于组合收益和无风险收益率之间的差除以痛苦指数（Pain Index）

用法
::

    PainRatio(R, Rf = 0, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rf: 同时期无风险收益率
    :...: 其它要传入的参数

说明
    .. math::

        PainRatio=\frac{r_P-r_F}{\Sigma^n_{i=1}\frac{\vert{D^{'}_i}\vert}{n}}

    其中， :math:`r_P` 是组合年化收益， :math:`r_F` 是无风险收益率， n是序列观测样本数， :math:`D^{'}_i` 是第i期上个峰值后的回撤

参考
    Carl Bacon, Practical portfolio performance measurement and attribution, second edition 2008 p.91

范例
::

    data(portfolio_bacon)
    print(PainRatio(portfolio_bacon[,1])) #expected 2.66

    data(managers)
    print(PainRatio(managers[ 1996 ]))
    print(PainRatio(managers[ 1996 ,1]))

