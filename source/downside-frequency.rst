DownsideFrequency
=================

描述
    要计算下方频数，取小于最低可接受收益（MAR）的子集，然后将该子集长度除以收益的总次数。

用法
::

    DownsideFrequency(R, MAR = 0, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :MAR: 最小可接受收益，与收益的周期性相同
    :...: 其它要传入的参数

说明
    .. math::

        DownsideFrequency(R, MAR)=\sum^n_{t=1}\frac{min[(R_t-MAR),0]}{R_t\times{n}}

    其中， n或者是整个序列观测值的数量

参考
    1. Carl Bacon, Practical portfolio performance measurement and attribution, second edition 2008 p.94

范例
::

    data(portfolio_bacon)
    MAR = 0.005
    print(DownsideFrequency(portfolio_bacon[,1], MAR)) #expected 0.458
    data(managers)
    print(DownsideFrequency(managers[ 1996 ]))
    print(DownsideFrequency(managers[ 1996 ,1])) #expected 0.25


