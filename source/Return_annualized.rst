Return.annualized
=================

描述
    计算年化收益以比较历史长度不同的证券。

用法
::

    Return.annualized(R, scale = NA, geometric = TRUE)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :scale: 一年的期数（日刻度=252，月刻度=12，季刻度=4）
    :geometric: 生成几何（TRUE）或简单（FALSE）收益，缺省为TRUE

说明
    年化收益有助于比较两种资产。要做到这点，必须通过把复合收益提升到到一年的期数，然后取总观测值数量次根来将你的观测值伸缩到年度刻度。

    .. math::

        {prod(1+R_a)}^{\frac{scale}{n}}=\sqrt[3]{{prod(1+R_a)}^{\frac{scale}{n}}-1}

    其中，scale 是一年的期数，n是观测值的总期数。

    对简单收益（geometric=FALSE），公式为 :math:`\overline{R_a}\centerdot{scale}`

参考
    Bacon, Carl. Practical Portfolio Performance Measurement and Attribution. Wiley. 2004. p. 6

另见
    Return.cumulative

范例
::

    data(managers)
    Return.annualized(managers[,1,drop=FALSE])
    Return.annualized(managers[,1:8])
    Return.annualized(managers[,1:8],geometric=FALSE)

