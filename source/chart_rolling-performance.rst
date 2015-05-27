chart.RollingPerformance
========================

描述
    在线图中创建滚动绩效矩阵的封装函数

用法
::

    chart.RollingPerformance(R, width = 12, FUN = "Return.annualized", ..., na.pad = TRUE, ylim = NULL, main = NULL)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :width: 应用滚动函数窗口的期数
    :FUN: 任何可用单一系列收益解析的函数（例如，滚动CAPM.beta不可以，而Return.annualized可以）
    :na.pad: TRUE/FALSE。如果为TRUE，将任何不在结果中的时间以NA值添加；如果为FALSE，则丢弃那些时间
    :main: 设置图表标题，同在plot中一样
    :ylim: 设置y轴界限，与在plot中一样
    :...: 任何其它传入plot或其它指定函数的参数

另见
    charts.RollingPerformance rollapply

范例
::

    data(edhec)

    chart.RollingPerformance(edhec[, 1:3], width = 24)

    chart.RollingPerformance(edhec[, 1:3], FUN = 'mean', width = 24, colorset = rich8equal, lwd = 2,
                             legend.loc = "topleft", main = "Rolling 24-Month Mean Return")

    chart.RollingPerformance(edhec[, 1:3], FUN = 'SharpeRatio.annualized', width = 24, colorset = rich8equal, lwd = 2,
                             legend.loc = "topleft", main = "Rolling 24-Month Sharpe Ratio")

