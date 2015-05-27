StdDev.annualized
=================

描述
    年化标准差

用法
::

    StdDev.annualized(x, scale = NA, ...)

参数
    :x: 一个资产收益的向量、矩阵、数据框、时间序列或zoo、xts对象
    :scale: 一年内期数（日刻度=252，月刻度=12，季刻度=4）
    :...: 其它要传入的参数

说明
    .. math::

        \sigma=variance(R_\alpha), std=\sqrt{\sigma}

要注意：方差不是观测样本数的线性函数。要确定跨越多期的概率方差，将单期方差乘以期数是没有意义的：它将很快导致一个同方差（或风险）大于100的荒谬结果。
随着期数增加方差的增长应逐期递减。要归一化跨越多期的标准差，我们要乘上希望计算的期数的平方根；年化标准差，则乘以每年期数的平方根。

.. math::

    \sqrt{\sigma}\centerdot\sqrt{periods}

注意，如果观测样本数太小的话，任何多期或年化数都需持怀疑态度

参考
    Bacon, C. Practical Portfolio Performance Measurement and Attribution. Wiley. 2004. p. 27

另见
    sd http://wikipedia.org/wiki/inverse-square_law

范例
::

    data(edhec)
    sd.annualized(edhec)
    sd.annualized(edhec[,6,drop=FALSE])

    # now for three periods:
    sd.multiperiod(edhec[,6,drop=FALSE],scale=3)

