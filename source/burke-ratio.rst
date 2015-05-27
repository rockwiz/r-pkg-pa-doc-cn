BurkeRatio
==========

描述
    组合收益和无风险利率的差，然后除以回撤平方和的平方根，得到Burke比率。将Burke比率乘以数据个数的平方根得到修正Burke比率

用法
::

    BurkeRatio(R, Rf = 0, modified = FALSE, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo、xts对象
    :Rf: 无风险收益率
    :modified: 逻辑值，决定用Burke比率还是修正Burke比率
    :...: 其它要传入的参数

细节
    .. math::

        BurkeRatio=\frac{r_P-r_F}{\sqrt{\Sigma^d_{t=1}{D_t}^2}}

        ModifiedBurkeRatio=\frac{r_P-r_F}{\sqrt{\Sigma^d_{t=1}\frac{{D_t}^2}{n}}}

    其中，n是序列中观测样本数，d是回撤数， :math:`r_P` 是组合收益， :math:`r_F` 是无风险收益， :math:`D_t` 是第t期回撤

参考
    Carl Bacon, Practical portfolio performance measurement and attribution, second edition 2008 p.90-91

范例
::

    data(portfolio_bacon)
    print(BurkeRatio(portfolio_bacon[,1])) #expected 0.74
    print(BurkeRatio(portfolio_bacon[,1], modified = TRUE)) #expected 3.65
    data(managers)
    print(BurkeRatio(managers[1996]))
    print(BurkeRatio(managers[1996,1]))
    print(BurkeRatio(managers[1996], modified = TRUE))
    print(BurkeRatio(managers[1996,1], modified = TRUE))

