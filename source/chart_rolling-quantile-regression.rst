chart.RollingQuantileRegression
===============================

描述
    一个创建相对回归绩效随时间演变的图表的封装函数。

    charts.RollingRegression中的一组图表在一个设备中以三个排成一列的图表显示alpha、beta和R-squared估计。

用法
::

    chart.RollingRegression(Ra, Rb, width = 12, Rf = 0, attribute = c("Beta", "Alpha", "R-Squared"),
                            main=NULL, na.pad = TRUE, ...)

    chart.RollingQuantileRegression(Ra, Rb, width = 12, Rf = 0, attribute = c("Beta", "Alpha", "R-Squared"),
                                    main=NULL, na.pad = TRUE, ...)

    charts.RollingRegression(Ra, Rb, width = 12, Rf = 0, main = NULL, legend.loc = NULL, event.labels = NULL, ...)

参数
    :Ra: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rb: 基准资产的收益向量
    :Rf: 与收益同时期的无风险收益率
    :width: 应用滚动函数窗口的期数
    :attribute: “Beta”、“Alpha”、“R-Squared”之一，要显示的属性
    :main: 设置图表标题，同在plot中一样
    :event.labels: TRUE/FALSE，是否显示历史市场震动事件（shock events）线和标签签
    :legend.loc: 把图例放置在图表上9个位置之一：bottomright、bottom、bottomleft、left、topleft、top、topright、right或center
    :na.pad: TRUE/FALSE。如果为TRUE，将任何不在结果中的时间以NA值添加；如果为FALSE，则丢弃那些时间
    :...: 任何其它传入chart.TimeSeries的参数

说明
    attribute参数可能是最令人困惑的。在数学意义上，不同选择结果如下：

    | Alpha – 显示y截距
    | Beta – 显示回归直线的斜率
    | R-Squared – 显示回归直线与数据间的拟合程度
    | chart.RollingQuantileRegression 使用rq 而不是lm作回归，也许对数据中的异常值更稳健。

备注
    大多数输入和“plot”一样，并且基本都包括进来了，以便可设置一些实用的缺省值。

另见
    lm rq

范例
::

    # First we load the data
    data(managers)
    chart.RollingRegression(managers[, 1, drop=FALSE],
    managers[, 8, drop=FALSE], Rf = .04/12)
    charts.RollingRegression(managers[, 1:6],
    managers[, 8, drop=FALSE], Rf = .04/12,
    colorset = rich6equal, legend.loc="topleft")
    dev.new()
    chart.RollingQuantileRegression(managers[, 1, drop=FALSE],
    managers[, 8, drop=FALSE], Rf = .04/12)

    # not implemented yet
    #charts.RollingQuantileRegression(managers[, 1:6],
    # managers[, 8, drop=FALSE], Rf = .04/12,
    # colorset = rich6equal, legend.loc="topleft")

