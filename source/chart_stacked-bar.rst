chart.StackedBar
================

描述
    该函数创建一个带有水平轴上的时间和类别中的值的堆积列（stacked column）图。这种图表通常用于显示投资组合随时间的“权重”，尽管它可以按类别标绘任何值。

用法
::

    chart.StackedBar(w, colorset = NULL, space = 0.2, cex.axis=0.8, cex.legend = 0.8, cex.lab = 1,
                     cex.labels = 0.8, cex.main = 1, xaxis=TRUE, legend.loc="under",  element.color = "darkgray",
                     unstacked = TRUE, xlab="Date", ylab="Value", ylim=NULL, date.format = "%b %y",
                     major.ticks='auto', minor.ticks=TRUE, las = 0, xaxis.labels = NULL, ... )

参数
    :xaxis: 如果为TRUE，画出x轴
    :ylab: 设置y轴标签，与在plot中一样
    :date.format: 重新设定x轴日期格式，缺省为“%m/%y”
    :major.ticks: 要画出主刻度并标记之？缺省为“auto”
    :minor.ticks: 要画出次刻度并标记之？缺省为TRUE
    :xaxis.labels: 允许日期轴的非日期标签，缺省为NULL
    :cex.axis: 用来确定坐标轴文本大小的相对“cex”当前设置的放大倍数，与在plot中一样
    :las: 设置坐标轴标签排列方向，如par中所描述的。缺省为“3”
    :legend.loc: places a legend into a location on the chart similar to chart.TimeSeries.
                 The default, under is the only location currently implemented for this chart.
                 Use ’NULL’ to remove the legend.
    :element.color: 不太重要的图表元素的颜色，例如箱线、坐标线等等
    :unstacked: 逻辑值。如果设为TRUE，并且在“w”中仅提交一行数据，那么将创建一个普通列图；如果提交多行数据，那么该选项被忽略。参见以下范例
    :xlab: x轴标签，缺省为NULL
    :ylim: 设置y轴界限，与在plot中一样
    :...: 传入barplot的参数

说明
    该函数是barplot 的封装，但增加了三个额外功能。首先，它计算并为垂直旋转的长列名设置一个底部边缘部分。那不总是导致一个漂亮的图表，
    但确实保证了标签的可读性。

    其次，它将图例置于图形之下，而非图表边界以内（那可能遮掩数据）。当要展示超过一行数据时，缺省状态下，图例从列名字中生成。
    如果仅有一行数据，图表会是“无堆积的”（unstacked），图例也就去除了。

    第三，它从零原点标绘或堆积负值，与lattice包中的barchart行为相同。

备注
    “w”属性如此命名，因为这是随时间显示投资组合权重的流行方式。也就是说，该函数不局限于任何特定的值，并且也不提供任何规范化，
    所以图表可以更普遍地使用。

    堆积列图的最主要缺点是读者非常难判断第二、三个等等数据序列的大小，因为它们没有共同的基线。另一个缺点是当有大量序列时，
    很难辨别它们的颜色。作为替代，Cleveland 提倡使用网格类显示，而Tufte 提倡用多个小图。

参考
    1. Cleveland, W.S. (1994), The Elements of Graphing Data, Summit, NJ: Hobart Press.
    2. Tufte, Edward R. (2001) The Visual Display of Quantitative Information, 2nd edition. The Graphics Press, Cheshire, Connecticut. See http://www.edwardtufte.com for this and other references.

另见
    barplot par

范例
::

    data(weights)
    head(weights)

    # With the legend "under" the chart
    chart.StackedBar(weights, date.format="%Y", cex.legend = 0.7, colorset=rainbow12equal)

    # Without the legend
    chart.StackedBar(weights, colorset=rainbow12equal, legend.loc=NULL)

    # for one row of data, use 'unstacked' for a better chart
    chart.StackedBar(weights[1,,drop=FALSE], unstacked=TRUE, las=3)

