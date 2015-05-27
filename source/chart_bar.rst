chart.Bar
=========

描述
    在柱状图中创建一个定期收益图。这是一个很难阅读的图形，因此用的很少。但对单一系列数据还是有用的。

用法
::

    chart.Bar(R, legend.loc = NULL, colorset = (1:12), ...)
    charts.Bar (R, main = "Returns", cex.legend = 0.8, cex.main=1, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :legend.loc: 把图例放置在图表上9个位置之一：bottomright、bottom、bottomleft、left、topleft、top、topright、right或center
    :colorset: 调色板，缺省设为合理选择
    :cex.legend: 设置图例文本大小，如在chart.TimeSeries 中一样
    :cex.main: 设置标题文本大小，如在chart.TimeSeries 中一样
    :main: 设置标题文本，如在chart.TimeSeries 中一样
    :...: 其它要传入的参数，参见plot

说明
    这其实是一个chart.TimeSeries 的封装，因此也可传递一些其它属性。

    创建一个标绘图，包括x轴上的时间和每期一条显示y轴上值的垂直线。

另见
    chart.TimeSeries plot

范例
::

    data(edhec)
    chart.Bar(edhec[,"Funds of Funds"], main="Monthly Returns")

