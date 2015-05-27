chart.Histogram
===============

描述
    创建一个收益的直方图，带有可选的密度和正态分布拟合曲线。这是一个hist 的封装函数，参见该函数的帮助文档了解你也许想传入的参数。

用法
::

    chart.Histogram(R, breaks="FD", main = NULL, xlab = "Returns", ylab = "Frequency",
                    methods = c("none","add.density", "add.normal", "add.centered", "add.cauchy", "add.sst", "add.rug",
                    "add.risk", "add.qqplot"), show.outliers = TRUE,
                    colorset = c("lightgray", "#00008F", "#005AFF", "#23FFDC", "#ECFF13", "#FF4A00", "#800000"),
                    border.col = "white", lwd = 2, xlim = NULL, ylim = NULL, element.color="darkgray",
                    note.lines = NULL, note.labels = NULL, note.cex = 0.7, note.color = "darkgray",
                    probability = FALSE, p = 0.95, cex.axis = 0.8, cex.legend = 0.8, cex.lab = 1, cex.main = 1,
                    xaxis=TRUE, yaxis=TRUE, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :breaks: 以下之一：

        | 给出直方图单元（histogram cells）之间间隔点（breakpoints）的向量
        | 给出直方图单元数的单一数字
        | 命名计算单元数算法的字符串（参见“说明”部分）
        | 计算单元数的函数

        后三种情况下，数字仅为建议。参见hist获知详情，缺省为“FD”

    :methods: 画什么图，以下中的一个或多个：

        | add.density – 显示密度图
        | add.normal – 在均值上显示拟合的正态分布线
        | add.centered – 在零值上显示拟合的正态分布线
        | add.rug – 显示一片观测值
        | add.risk – 显示常见风险矩阵
        | add.qqplot – 在直方图上角显示一个小Q-Q图

    :p: 用于计算的置信水平，缺省p=.99
    :probability: 逻辑值。如果为TRUE，直方图表示频数，即结果中成分的个数；如果为FALSE，绘制出概率密度、成分密度（因此，直方图总面积为1）。
                  缺省为TRUE，当且仅当间隔等距（并且没有指定概率）。参见hist
    :show.outliers: 逻辑值。如果为TRUE（缺省地），直方图将显示所有的数据点。如果为FALSE，仅显示第一个到第四个四分位，而不包括异常值。
    :main: 设置图表标题，同在plot中一样
    :ylab: 设置y轴标签，与在plot中一样
    :xlab: 设置x轴标签，与在plot中一样
    :ylim: 设置y轴界限，与在plot中一样
    :border.col: 边框颜色
    :xlim: 设置x轴界限，与在plot中一样
    :lwd: 设置线宽，与在plot中一样
    :colorset: 调色板，缺省设为合理选择
    :element.color: 图表元素的绘制颜色，例如箱线、坐标线等等。缺省为“darkgray”（深灰）
    :note.lines: 画一条穿过给定值的垂直线
    :note.labels: 给指定为note.lines 的垂直线添加一个文本标签
    :note.cex: 用来确定备注线标签大小的相对“cex”当前设置的放大倍数
    :note.color: 指定画出的垂直线的颜色
    :cex.legend: 用来确定图例大小的相对“cex”当前设置的放大倍数
    :cex.axis: 用来确定坐标轴标注大小的相对“cex”当前设置的放大倍数，与在plot中一样
    :cex.lab: 用来确定x和y轴标签大小的相对“cex”当前设置的放大倍数.
    :cex.main: 用来确定标题大小的相对“cex”当前设置的放大倍数
    :xaxis: 如果为TRUE，画出x轴
    :yaxis: 如果为TRUE，画出y轴
    :...: 任何其它传入plot的参数

说明
    缺省状态下，breaks是 “FD”。其它指定用哪种算法的名字由“Sturges”（参见 nclass.Sturges）、“Scott”和“FD”/“Freedman-Diaconis”
    （以相应的函数nclass.scott 和nclass.FD）提供。忽略大小写并用部分匹配。

    或者，可提供一个计算预期breaks数量的R函数。

备注
    代码受以下网址上的图表启发：

    http://zoonek2.free.fr/UNIX/48_R/03.html

另见
    hist

范例
::

    data(edhec)
    chart.Histogram(edhec[,'Equity Market Neutral',drop=FALSE])

    # version with more breaks and the standard close fit density distribution
    chart.Histogram(edhec[,'Equity Market Neutral',drop=FALSE], breaks=40, methods = c("add.density", "add.rug") )

    chart.Histogram(edhec[,'Equity Market Neutral',drop=FALSE], methods = c( "add.density", "add.normal") )

    # version with just the histogram and normal distribution centered on 0
    chart.Histogram(edhec[,'Equity Market Neutral',drop=FALSE],
                    methods = c( "add.density", "add.centered") )

    # add a rug to the previous plot for more granularity on precisely where the distribution fell
    chart.Histogram(edhec[,'Equity Market Neutral',drop=FALSE],
                    methods = c( "add.centered", "add.density", "add.rug") )

    # now show a qqplot to give us another view on how normal the data are
    chart.Histogram(edhec[,'Equity Market Neutral',drop=FALSE],
                    methods = c( "add.centered", "add.density", "add.rug", "add.qqplot") )

    # add risk measure(s) to show where those are in relation to observed returns
    chart.Histogram(edhec[,'Equity Market Neutral',drop=FALSE],
                    methods = c("add.density", "add.centered", "add.rug", "add.risk") )

