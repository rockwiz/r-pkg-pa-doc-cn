ProspectRatio
=============

描述
    前景比率用来惩罚亏损，因为大多数人对损失的感受大于收益

用法
::

    ProspectRatio(R, MAR, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :MAR: 最小可接受收益，与收益的周期性相同
    :...: 其它要传入的参数

说明
    .. math::

        ProspectRatio(R)=\frac{\frac{1}{n}\times\Sigma^n_{i=1}(Max(r_i,0)+2.25\times{(Min(r_i,0))}-MAR)}{\sigma_D}

    其中， n是序列观测样本数，MAR是最小可接受收益， :math:`\sigma_D` 是下方风险

参考
    Carl Bacon, Practical portfolio performance measurement and attribution, second edition 2008 p.100

范例
::

    data(portfolio_bacon)
    MAR = 0.05
    print(ProspectRatio(portfolio_bacon[,1], MAR)) #expected -0.134
    data(managers)
    MAR = 0
    print(ProspectRatio(managers[ 1996 ], MAR))
    print(ProspectRatio(managers[ 1996 ,1], MAR))


