Return.annualized.excess
========================

描述
    计算年化超额收益以便于比较

用法
::

    Return.annualized.excess(Rp, Rb, scale = NA, geometric = TRUE)

参数
    :Rp: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rb: 一个基准资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :scale: 一年的期数（日刻度=252，月刻度=12，季刻度=4）
    :geometric: 生成几何（TRUE）或简单（FALSE）收益，缺省为TRUE

说明
    年化收益有助于比较两种资产。要做到这点，必须通过把复合收益提升到到一年的期数，然后取总观测值数量n次根来将观测值伸缩到年度刻度。

    .. math::

        {prod(1+R_a)}^{\frac{scale}{n}}=\sqrt[3]{{prod(1+R_a)}^{\frac{scale}{n}}-1}

    其中，scale 是一年的期数，n是观测值的总期数。
    最终，在得出年化组合收益和基准收益后，我们可以计算年化超额收益，其算数方法为：

    .. math::

        er=R_{pa}-R_{ba}

    几何方法为：

    .. math::

        er=\frac{1+R_{pa}}{1+R_{ba}}-1

参考
    Bacon, Carl. Practical Portfolio Performance Measurement and Attribution. Wiley. 2004. p. 206

另见
    Return.annualized

范例
::

    data(managers)
    Return.annualized.excess(Rp = managers[,1], Rb = managers[,8])


