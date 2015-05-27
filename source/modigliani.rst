Modigliani
==========

描述
    M2测度是由JP Morgan公司的Leah Modigliani及其祖父诺贝尔经济学奖得主Franco Modigliani对夏普测度进行改进后引入的

    .. math::

        MM_p=\frac{E[R_p-R-f]}{\sigma_p}=SR_p\times{\sigma_b}+E[R_f]

    其中， :math:`SR_p` 是夏普比率， :math:`\sigma_b` 是基准标准差

用法
::

    Modigliani(Ra, Rb, Rf = 0, ...)

参数
    :Ra: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rb: 一个基准资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rf: 同时期无风险收益率
    :...: 其它要传入的参数

说明
    M2测度也是对总风险进行调整的，它反映资产组合同相应的无风险资产混合以达到同市场组合具有同样的风险水平时，
    混合组合的收益高出市场收益的大小。其目的是纠正投资者只考虑基金原始业绩的倾向，鼓励他们应同时注意基金业绩中的风险因素，
    从而帮助投资者挑选出能带来真正最佳业绩的投资基金。同夏普比率相比，M2测度指标也把全部风险作为风险的度量。
    这种风险的调整方法很容易解释为什么相对于不同的市场基准指数，会有不同的收益水平。M2测度与夏普比率对基金绩效表现的排序是一致的。

    M2测度越大，基金的业绩表现越好；反之，基金表现越差。

参考
    1. J. Christopherson, D. Carino, W. Ferson. Portfolio Performance Measurement and Benchmarking. 2009. McGraw-Hill, p. 97-99.
    2. Franco Modigliani and Leah Modigliani, "Risk-Adjusted Performance: How to Measure It and Why," Journal of Portfolio Management, vol.23, no., Winter 1997, pp.45-54

范例
::

    data(managers)
    Modigliani(managers[,1,drop=FALSE], managers[,8,drop=FALSE], Rf=.035/12)
    Modigliani(managers[,1:6], managers[,8,drop=FALSE], managers[,8,drop=FALSE])
    Modigliani(managers[,1:6], managers[,8:7], managers[,8,drop=FALSE])


