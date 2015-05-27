CAPM.jensenAlpha
================

描述
    詹森alpha是CAPM回归方程的截距，实际上是系统风险的超额收益

用法
::

    CAPM.jensenAlpha(Ra, Rb, Rf = 0, ...)

参数
    :Ra: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rb: 基准资产的收益向量
    :Rf: 与收益同时期的无风险收益率
    :...: 其它要传入的参数

详细
    .. math::

        \alpha=r_p-r_p-r_f-\beta_{p}\times{b-r_f}

    其中， :math:`r_f` 是无风险收益率， :math:`\beta_r` 是回归beta，:math:`r_p` 是组合收益， b是基准收益

参考
    Carl Bacon, Practical portfolio performance measurement and attribution, second edition 2008, P72

范例
::

    data(portfolio_bacon)
    print(SFM.jensenAlpha(portfolio_bacon[,1], portfolio_bacon[,2])) #expected -0.014
    data(managers)
    print(SFM.jensenAlpha(managers[ 1996 ,1], managers[ 1996 ,8]))
    print(SFM.jensenAlpha(managers[ 1996 ,1:5], managers[ 1996 ,8]))

