MSquaredExcess
==============

描述
    超额散度是标准散度之上的数量。存在一个优于Bacon和算术超额收益的几何超额收益

用法
::

    MSquaredExcess(Ra, Rb, Rf = 0, Method = c("geometric", "arithmetic"), ...)

参数
    :Ra: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rb: 一个基准资产收益的向量
    :Rf: 同时期无风险收益率
    :method: 计算MSquareExcess的方法，几何还是算数
    :...: 其它要传入的参数

说明
    .. math::

        M^{2}excess(geometric)=\frac{1+M^2}{1+b}-1

        M^{2}excess(arithmetic)=M^2-b

    其中， :math:`M^2` 是MSquared， :math:`b` 是基准年化收益

参考
    Carl Bacon, Practical portfolio performance measurement and attribution, second edition 2008 p.68

范例
::

    data(portfolio_bacon)
    MSquaredExcess(portfolio_bacon[,1], portfolio_bacon[,2]) #expected -0.00998
    MSquaredExcess(portfolio_bacon[,1], portfolio_bacon[,2], Method="arithmetic") #expected -0.011
    data(managers)
    MSquaredExcess(managers[ 1996 ,1], managers[ 1996 ,8])
    MSquaredExcess(managers[ 1996 ,1:5], managers[ 1996 ,8])

