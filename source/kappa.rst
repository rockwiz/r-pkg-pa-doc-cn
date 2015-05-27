Kappa
=====

描述
    Kappa是一个广义下方风险调整绩效测度，由Kaplan和Knowles在2004年引进

用法
::

    Kappa(R, MAR, l, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :MAR: 与实际收益同时期的最小可接受收益
    :l: kappa系数

说明
    .. math::

        Kappa(R, M AR, l)=\frac{r_p-MAR}{\sqrt[l]{\frac{1}{n}\times\Sigma^n_{t=1}{max(MAR-R_t,0)}^l}}

    l=1，Kappa就是Sharpe-omega比率；l=2，Kappa就是sortino比率。Kappa不应用于评定组合级别，因为很难解释kappa之间的绝对差值。
    kappa越高，绩效越好。

参考
    1. Carl Bacon, Practical portfolio performance measurement and attribution, second edition 2008 p.96

范例
::

    l = 2
    data(portfolio_bacon)
    MAR = 0.005
    print(Kappa(portfolio_bacon[,1], MAR, l)) #expected 0.157
    data(managers)
    MAR = 0
    print(Kappa(managers[ 1996 ], MAR, l))
    print(Kappa(managers[ 1996 ,1], MAR, l)) #expected 1.493

