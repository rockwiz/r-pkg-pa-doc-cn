InformationRatio
================

描述
    信息比率=主动溢价/追踪误差

    主动溢价（Active Premium）除以追踪误差（Tracking Error）。

    InformationRatio = ActivePremium/TrackingError

    它将一项投资打败基准的程度与打败基准的一致性联系起来。

用法
    InformationRatio(Ra, Rb, scale = NA)

参数
    :Ra: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rb: 基准资产的收益向量
    :scale: 一年的期数（日刻度=252，月刻度=12，季刻度=4）

备注
    William Sharpe now recommends InformationRatio preferentially to the original SharpeRatio

参考
    1. Sharpe, W.F. The Sharpe Ratio,Journal of Portfolio Management,Fall 1994, 49-58.

另见
    TrackingError ActivePremium SharpeRatio

范例
::

    data(managers)
    InformationRatio(managers[,"HAM1",drop=FALSE], managers[, "SP500 TR", drop=FALSE])
    InformationRatio(managers[,1:6], managers[,8,drop=FALSE])
    InformationRatio(managers[,1:6], managers[,8:7])

