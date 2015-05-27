chart.RollingMean
=================

描述
    滚动均值收益图表。以95%置信区间创建一个滚动均值收益图表的封装函数。

用法
::

    chart.RollingMean(R, width = 12, xaxis = TRUE, ylim = NULL, na.pad =FALSE, lwd = c(2, 1, 1), ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :width: 应用滚动函数窗口的期数
    :xaxis: 如果为TRUE，画出x轴
    :ylim: 设置y轴界限，与在plot中一样
    :na.pad: TRUE/FALSE。如果为TRUE，将任何不在结果中的时间以NA值添加；如果为FALSE，则丢弃那些时间
    :lwd: 设置线宽，与在plot中一样。以主线和两条置信区间线顺序指定
    :...: 其它要传入的参数

范例
::

    data(edhec)
    chart.RollingMean(edhec[, 9, drop = FALSE])

