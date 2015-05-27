HurstIndex
==========

描述
    赫斯特指数也被称为重标极差(R/S)分析方法

用法
::

    HurstIndex(R, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :...: 其它要传入的参数

说明
    .. math::

        H=\frac{log(m)}{log(n)}

    其中， :math:`m=\frac{max(r_{i})-min(r_{i})}{\sigma_p}` ， n=观测值数量

赫斯特指数有三种形式：

1. 如果H=0.5，表明时间序列可以用随机游走来描述；
2. 如果0.5<H<1，表明时间序列存在长期记忆性；
3. 如果0≤H<0.5，表明粉红噪声(反持续性)即均值回复过程。也就是说，只要H≠0.5，就可以用有偏的布朗运动(分形布朗运动)来描述该时间序列数据。

参考
    1. Clarkson, R. (2001) FARM: a financial actuarial risk model. In Chapter 12 of Managing Downside Risk in Financial Markets, F. Sortino and S.
    2. Satchel. Butterworth-Heinemann Finance.
    3. Peters, E.E (1991) Chaos and Order in Capital Markets, New York: Wiley.
    4. Bacon, Carl. (2008) Practical Portfolio Performance Measurement and Attribution, 2nd Edition. London: John Wiley & Sons.
