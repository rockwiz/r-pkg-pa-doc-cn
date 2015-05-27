chart.Scatter
=============
描述
    画出散点图。这是另一张“原始”图，因为它只是包含一些合乎情理（sensible）的缺省值。

用法
::

    chart.Scatter(x, y, reference.grid = TRUE, main = "Title", ylab = NULL, xlab = NULL, xlim = NA, ylim = NA,
                  colorset = 1, symbolset = 1, element.color = "darkgray", cex.axis = 0.8, cex.legend = 0.8,
                  cex.lab = 1, cex.main = 1, ...)

参数
    :x: x轴数据，可取matrix、vector或timeseries
    :y: y轴数据，可取matrix、vector或timeseries
    :reference.grid: 如果为TRUE，画出与x、y轴上点排列对齐的网格线
    :main: 设置图表标题，同在plot中一样
    :ylab: 设置y轴标签，与在plot中一样
    :xlab: 设置x轴标签，与在plot中一样
    :xlim: 设置x轴界限，与在plot中一样
    :ylim: 设置y轴界限，与在plot中一样
    :colorset: 调色板，缺省设为合理选择
    :symbolset: 从pchin绘图，数据集提交时，以相同的顺序提交一组符号
    :element.color: 图表元素的绘制颜色，例如箱线、坐标线等等。缺省为“darkgray”（深灰）
    :cex.lab: 用来确定x和y轴标签大小的相对“cex”当前设置的放大倍数
    :cex.axis: 用来确定坐标轴标注大小的相对“cex”当前设置的放大倍数，与在plot中一样
    :cex.main: 用来确定标题大小的相对“cex”当前设置的放大倍数
    :cex.legend: 用来确定图例大小的相对“cex”当前设置的放大倍数
    :...: 其它要传入的参数

备注
    大多数输入和“plot”一样，并且基本都包括进来了，以便可设置一些实用的缺省值。

另见
    plot

范例
::

    data(edhec)
    chart.Scatter(edhec[,1],edhec[,2])

