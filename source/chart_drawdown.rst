chart.Drawdown
==============

描述
    一个用来展示从达到的顶峰权益回撤（drawdowns）随时间演变的时间序列图，从定期收益中计算。

用法
::

    chart.Drawdown(R, geometric=TRUE, legend.loc = NULL, colorset = (1:12), ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :geometric: 生成几何（TRUE）或简单（FALSE）收益，缺省为TRUE
    :colorset: 调色板，缺省设为合理选择
    :legend.loc: 把图例放置在图表上9个位置之一：bottomright、bottom、bottomleft、left、topleft、top、topright、right或center
    :...: 其它要传入的参数

说明
    任何时候，累计收益跌破到最大累计收益之下，它就是一个回撤。回撤以最大累计收益的百分比来度量，实际上就是从峰值权益度量。

另见
    plot chart.TimeSeries findDrawdowns sortDrawdowns maxDrawdown table.Drawdowns table.DownsideRisk

范例
::

    data(edhec)
    chart.Drawdown(edhec[,c(1,2)], main="Drawdown from Peak Equity Attained", legend.loc="bottomleft")

