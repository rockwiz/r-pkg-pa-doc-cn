DRatio
======

描述
    d比率和Bernado Ledoit比率类似，但是其倒数且考虑了正负收益的频数

用法
::

    DRatio(R, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :...: 其它要传入的参数

说明
    值在零和无限大之间。可用于对组合绩效进行评级。d比率的值越小，绩效越好。零值意味着没有小于零的收益，无限大意味没有大于零的收益。

.. math::

    DRatio(R)=\frac{n_d\times{\Sigma^n_{t=1}max(-R_t,0)}}{n_u\times{\Sigma^n_{t=1}max(R_t,0)}}

其中， n或者是整个序列观测值的数量， :math:`n_d` 是小于零的观测值数量， :math:`n_u` 是大于零的观察值数量

参考
    Carl Bacon, Practical portfolio performance measurement and attribution, second edition 2008 p.95

范例
::

    data(portfolio_bacon)
    MAR = 0.005
    print(DownsideFrequency(portfolio_bacon[,1], MAR)) #expected 0.458
    data(managers)
    print(DownsideFrequency(managers[ 1996 ]))
    print(DownsideFrequency(managers[ 1996 ,1])) #expected 0.25


