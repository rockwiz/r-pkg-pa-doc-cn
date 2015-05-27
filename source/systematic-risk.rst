SystematicRisk
==============

描述
    Bacon(2008)定义的系统风险是市场风险beta的乘积。小心！它与詹森（Michael Jensen）定义的那个不一样。
    市场风险是基准的标准差。系统风险是年化风险

用法
::

    SystematicRisk(Ra, Rb, Rf = 0, scale = NA, ...)

参数
    :Ra: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rb: 基准资产的收益向量
    :Rf: 与收益同时期的无风险收益率
    :scale: 一年内期数（日刻度=252，月刻度=12，季刻度=4）
    :...: 其它要传入的参数

说明
    .. math::

        \sigma_s=\beta\times{\sigma_m}

    其中， :math:`\sigma_s` 是系统风险， :math:`\beta` 是回归beta， :math:`\sigma_m` 是市场风险

参考
    Carl Bacon, Practical portfolio performance measurement and attribution, second edition 2008 p.75

范例
::

    data(portfolio_bacon)
    print(SystematicRisk(portfolio_bacon[,1], portfolio_bacon[,2])) #expected 0.013

    data(managers)
    print(SystematicRisk(managers[ 1996 ,1], managers[ 1996 ,8]))
    print(SystematicRisk(managers[ 1996 ,1:5], managers[ 1996 ,8]))


