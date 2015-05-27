Return.cumulative
=================

描述
    计算复合（几何）累积收益。该函数计算一段时期，比如一个日历年，的累积收益。可以生成简单或几何收益。

用法
::

    Return.cumulative(R, geometric = TRUE)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :geometric: 生成几何（TRUE）或简单（FALSE）收益，缺省为TRUE

说明
    所有单期收益的累积为：

参考
    1. Bacon, Carl. Practical Portfolio Performance Measurement and Attribution. Wiley. 2004. p. 6

另见
    Return.annualized

范例
::

    data(managers)
    Return.cumulative(managers[,1,drop=FALSE])
    Return.cumulative(managers[,1:8])
    Return.cumulative(managers[,1:8],geometric=FALSE)

