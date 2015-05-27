AverageDrawdown
===============

描述
    计算观测到回撤的平均深度

    .. math::

        ADD=\sum_{j=1,2,...,d}\frac{D^{'}_j}{d}

    其中， :math:`D^{'}_j` 是整个期间第j个回撤,d是整个期间回撤总数

用法
::

    AverageDrawdown(R, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo、xts对象
    :...: 其它要传入的参数
