OmegaSharpeRatio
================

描述
    Omega-Sharpe比率是omega比率转换为夏普比率常见形式的等级统计

用法
::

    OmegaSharpeRatio(R, MAR = 0, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :MAR: 最小可接受收益，与收益的周期性相同
    :...: 其它要传入的参数

说明
    Omega-Sharpe比率的计算是从组合收益中减去目标（或最小可接受收益），然后除以下方偏差的相反数

    .. math::

       OmegaSharpeRatio(R, MAR)=\frac{r_p-r_t}{\Sigma^n_{t=1}\frac{max(r_t-r_i,0)}{n}}

    其中，n是序列观测样本数

参考
    Carl Bacon, Practical portfolio performance measurement and attribution, second edition 2008 p.95

范例
::

    data(portfolio_bacon)
    MAR = 0.005
    print(OmegaSharpeRatio(portfolio_bacon[,1], MAR)) #expected 0.29
    MAR = 0
    data(managers)
    print(OmegaSharpeRatio(managers[ 1996 ], MAR))
    print(OmegaSharpeRatio(managers[ 1996 ,1], MAR)) #expected 3.60

