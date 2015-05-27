ActiveReturn
============

描述
    ActivePremium（主动溢价）或ActiveReturn（主动收益）。投资者年化收益减去基准年化收益的收益。

    主动溢价 = 投资者年化收益 - 基准年化收益

用法
::

    ActiveReturn(Ra, Rb, scale = NA)

参数
    :Ra: 投资组合的收益向量
    :Rb: 基准资产的收益向量
    :scale: 一年内期数（日刻度=252，月刻度=12，季刻度=4）

参考
    Sharpe, W.F. The Sharpe Ratio,Journal of Portfolio Management,Fall 1994, 49-58.

另见
    InformationRatio TrackingError Return.annualized

范例
::

    data(managers)
    ActivePremium(managers[, "HAM1", drop=FALSE], managers[, "SP500 TR", drop=FALSE])
    ActivePremium(managers[,1,drop=FALSE], managers[,8,drop=FALSE])
    ActivePremium(managers[,1:6], managers[,8,drop=FALSE])
    ActivePremium(managers[,1:6], managers[,8:7,drop=FALSE])

