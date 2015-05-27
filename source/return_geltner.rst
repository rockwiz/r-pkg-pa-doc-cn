Return.Geltner
==============

描述
    David Geltner开发了一种消除房地产指数收益的估计或流动性偏见的方法。显示自相关或流动性不足效应已经成功应用于其它序列。
    该理论通过自相关修正，将从包含流动性不足或手工定价效应的一组观测收益中揭示出一个“真实的”收益。

用法
::

    Return.Geltner(Ra, ...)

参数
    :Ra: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :...: 其它要传入的参数

说明
    Geltner 自相关调整收益序列的计算如下

    .. math::

        R_G=\frac{R_t-(R_{t-1}\centerdot\rho_1)}{1-\rho_1}

    其中，  为收益序列 :math:`R_a` 的一阶自相关， :math:`R_t` 是 :math:`R_a` 在时刻t的收益，而是一期滞后收益。

参考
    1. "Edhec Funds of Hedge Funds Reporting Survey : A Return-Based Approach to Funds of Hedge Funds Reporting",
        Edhec Risk and Asset Management Research Centre, January 2005,p. 27
    2. Geltner, David, 1991, Smoothing in Appraisal-Based Returns, Journal of Real Estate Finance and Economics,
        Vol.4, p.327-345.
    3. Geltner, David, 1993, Estimating Market Values from Appraised Values without Assuming an Efficient Market,
        Journal of Real Estate Research, Vol.8, p.325-345.

范例
::

    data(managers)
    head(Return.Geltner(managers[,1:3]),n=20)


