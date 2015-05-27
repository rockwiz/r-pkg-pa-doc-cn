charts.RollingPerformance
=========================

描述
    一个封装函数，用来创建滚动年化收益图、滚动年化标准偏差图和滚动年化夏普比率图。

用法
::

    charts.RollingPerformance(R, width = 12, Rf = 0, main = NULL, trim = TRUE, event.labels = NULL, legend.loc = NULL, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :width: 应用滚动函数的期数
    :Rf: 与收益同时期的无风险收益率
    :main: 设置图表标题，同在plot中一样
    :trim: TRUE/FALSE，是否保持NA引起的排列对齐
    :event.labels: TRUE/FALSE，是否显示历史市场震动事件（shock events）线和标签
    :legend.loc: 把图例放置在图表上9个位置之一：bottomright、bottom、bottomleft、left、topleft、top、topright、right或center
    :...: 其它要传入的参数

另见
    chart.RollingPerformance

范例
::

    data(managers)
    charts.RollingPerformance(managers[,1:8], Rf=managers[,10,drop=FALSE], colorset=tim8equal,
                              main="Rolling 12-Month Performance", legend.loc="topleft")


