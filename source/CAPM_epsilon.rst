CAPM.epsilon
============

描述
    回归epsilon是度量方程预测的收益和实际结果之间垂直距离的误差项

用法
::

    CAPM.epsilon(Ra, Rb, Rf = 0, ...)

参数
    :Ra: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rb: 基准资产的收益向量
    :Rf: 与收益同时期的无风险收益率
    :...: 其它要传入的参数

详细
    .. math::

        \epsilon_r=r_p-\alpha_r-\beta_{r}\times{b}

    其中， :math:`\alpha_r` 是回归alpha， :math:`\beta_r` 是回归beta，:math:`r_p` 是组合收益， b是基准收益

参考
    Carl Bacon, Practical portfolio performance measurement and attribution, second edition 2008, P71

范例
::

    data(portfolio_bacon)
    print(SFM.epsilon(portfolio_bacon[,1], portfolio_bacon[,2])) #expected -0.013
    data(managers)
    print(SFM.epsilon(managers[ 1996 ,1], managers[ 1996 ,8]))
    print(SFM.epsilon(managers[ 1996 ,1:5], managers[ 1996 ,8]))
