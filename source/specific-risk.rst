SpecificRisk
============

描述
    特定风险是回归方程中误差项的标准偏差

用法
::

    SpecificRisk(Ra, Rb, Rf = 0, ...)

参数
    :Ra: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rb: 基准资产的收益向量
    :Rf: 与收益同时期的无风险收益率
    :...: 传入的任何其它参数

参考
    Carl Bacon, Practical portfolio performance measurement and attribution, second edition 2008 p.75

范例
::

    data(portfolio_bacon)
    print(SpecificRisk(portfolio_bacon[,1], portfolio_bacon[,2])) #expected 0.0329

    data(managers)
    print(SpecificRisk(managers[ 1996 ,1], managers[ 1996 ,8]))
    print(SpecificRisk(managers[ 1996 ,1:5], managers[ 1996 ,8]))


