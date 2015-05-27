Frequency
=========

描述
    给出收益分布期数（例如，月度收益为12，季度收益为4）

用法
::

    Frequency(R, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :...: 其它要传入的参数

范例
::

    data(portfolio_bacon)
    print(Frequency(portfolio_bacon[,1])) #expected 12
    data(managers)
    print(Frequency(managers[ 1996 ,1:5]))

