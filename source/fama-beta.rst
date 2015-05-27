FamaBeta
========
描述
    法玛（Fama）beta用来计算多元化损失以便系统风险等于组合风险

用法
::

    FamaBeta(Ra, Rb, ...)

参数
    :Ra: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rb: 基准资产收益向量
    :...: 其它要传入的参数

参考
    Carl Bacon, Practical portfolio performance measurement and attribution, second edition 2008 p.78

另见
    sortDrawdowns maxDrawdown sortDrawdowns table.Drawdowns table.DownsideRisk chart.Drawdown

范例
::

    data(portfolio_bacon)
    print(FamaBeta(portfolio_bacon[,1], portfolio_bacon[,2])) #expected 1.03
    data(managers)
    print(FamaBeta(managers[ 1996 ,1], managers[ 1996 ,8]))
    print(FamaBeta(managers[ 1996 ,1:5], managers[ 1996 ,8]))

