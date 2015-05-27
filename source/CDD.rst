CDD
===

描述
    计算Uryasev提出的条件在险回撤（CDD或CDaR）度量。对某置信水平p，条件回撤是最恶劣的p%回撤的均值

用法
::

    CDD(R, weights = NULL, geometric = TRUE, invert = TRUE, p = 0.95, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo、xts对象
    :weights: 组合权重向量，缺省为NULL。参见说明部分
    :geometric: 生成几何（TRUE）或简单（FALSE）收益，缺省为TRUE
    :invert: TRUE/FALSE，是否反转回撤度量。 参见说明部分
    :p: 用于计算的置信水平，缺省p=0.95
    :...: 其它要传入的参数

参考

* Chekhlov, A., Uryasev, S., and M. Zabarankin. Portfolio Optimization With Drawdown Constraints.
* B. Scherer (Ed.) Asset and Liability Management Tools, Risk Books, London, 2003
* http://www.ise.ufl.edu/uryasev/drawdown.pdf

另见
    ES maxDrawdown

范例
::

    data(edhec)
    t(round(CDD(edhec),4))

