chart.TimeSeries
================

描述
    画一个线图并用合适的日期给x轴作标签。这其实是一个“原始的（primitive）”，因为它扩展了基本plot并标准化图表元素。
    增加了时间线的阴影区域和顺时间轴排列垂直线的属性。该函数的本意是用在其它图表函数内。

用法
::

    chart.TimeSeries(R, auto.grid = TRUE, xaxis = TRUE, yaxis = TRUE, yaxis.right = FALSE, type = "l", lty = 1,
                     lwd = 2, main = NULL, ylab = NULL, xlab = "Date", date.format.in = "%Y-%m-%d", date.format = NULL,
                     xlim = NULL, ylim = NULL, element.color = "darkgray", event.lines = NULL, event.labels = NULL,
                     period.areas = NULL, event.color = "darkgray", period.color = "aliceblue", colorset = (1:12),
                     pch = (1:12), legend.loc = NULL, ylog = FALSE, cex.axis = 0.8, cex.legend = 0.8, cex.lab = 1,
                     cex.labels = 0.8, cex.main = 1, major.ticks = "auto", minor.ticks = TRUE, grid.color = "lightgray",
                     grid.lty = "dotted", xaxis.labels = NULL, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :auto.grid: 如果为TRUE，画出与x、y轴上点排列对齐的网格线
    :grid.color: 设置参考网格的颜色
    :grid.lty: 定义网格线型
    :xaxis: 如果为TRUE，画出x轴
    :yaxis: 如果为TRUE，画出y轴
    :yaxis.right: 如果为TRUE，将y轴画在标绘图的右手边
    :type: 设置图表类型，与在plot中一样
    :lty: 设置线型，与在plot中一样
    :lwd: 设置线宽，与在plot中一样
    :main: 设置图表标题，同在plot中一样
    :ylab: 设置y轴标签，与在plot中一样
    :xlab: 设置x轴标签，与在plot中一样
    :date.format: 重新设定x轴日期格式，缺省为“%m/%y”
    :xlim: 设置x轴界限，与在plot中一样
    :ylim: 设置y轴界限，与在plot中一样
    :event.lines: 如果不是NULL ，将画出垂直线指示在此期间发生了一件事。event.lines应该是一个日期列表（例如，c( "09/03", "05/06")），日期格式与date.format一样。该函数用events.list匹配重新格式化的行名称（日期），因此需要正确匹配格式
    :event.labels: 如果不是NULL，并且event.lines 也非NULL，对所画的垂直线应用一个文本标签（例如，c("This Event", "That Event")）列表
    :period.areas: 由起始日期和终止日期指明的阴影区域，日期格式与date.format 一样。以成对列表的方式提供，如list(c("10/26","11/27"), c("08/29", "03/33"))
    :event.color: 以指定颜色画出event.labels描述的事件
    :period.color: 以指定颜色画出period.areas 描述的阴影区域
    :colorset: 调色板，缺省设为合理选择
    :pch: 要用的符号，也参见plot
    :element.color: 设定图表元素的颜色，缺省为“darkgray”
    :legend.loc: 把图例放置在图表上9个位置之一：bottomright、bottom、bottomleft、left、topleft、top、topright、right或center
    :ylog: TRUE/FALSE，将y轴设为对数刻度。缺省为FALSE
    :date.format.in: 数据对象中允许其它日期格式，缺省为"%Y-%m-%d"
    :cex.axis: 用来确定坐标轴标注大小的相对“cex”当前设置的放大倍数，与在plot中一样
    :cex.legend: 用来确定图例大小的相对“cex”当前设置的放大倍数
    :cex.labels: 用来确定事件线标签的相对“cex”的当前设置的放大倍数
    :cex.lab: 用来确定x和y轴标签大小的相对“cex”当前设置的放大倍数
    :cex.main: 用来确定图表标题的相对“cex”的当前设置的放大倍数
    :major.ticks: 要画出主刻度并标记之？缺省为“auto”
    :minor.ticks: 要画出次刻度并标记之？缺省为TRUE
    :xaxis.labels: 允许日期轴的非日期标签，缺省为NULL
    :...: 其它要传入的参数

另见
    plot par axTicksByTime

范例
::

    # These are start and end dates, formatted the same way as the default axis labels
    cycles.dates = list(
        c("Oct 26","Nov 27"),
        c("Aug 29","Mar 33"),
        c("May 37","Jun 38"),
        c("Feb 45","Oct 45"),
        c("Nov 48","Oct 49"),
        c("Jul 53","May 54"),
        c("Aug 57","Apr 58"),
        c("Apr 60","Feb 61"),
        c("Dec 69","Nov 70"),
        c("Nov 73","Mar 75"),
        c("Jan 80","Jul 80"),
        c("Jul 81","Nov 82"),
        c("Jul 90","Mar 91"),
        c("Mar 01","Nov 01"))
    # Event lists - FOR BEST RESULTS, KEEP THESE DATES IN ORDER
    risk.dates = c(
        "Oct 87",
        "Feb 94",
        "Jul 97",
        "Aug 98",
        "Oct 98",
        "Jul 00",
        "Sep 01")
    risk.labels = c(
        "Black Monday",
        "Bond Crash",
        "Asian Crisis",
        "Russian Crisis",
        "LTCM",
        "Tech Bubble",
        "Sept 11")
    data(edhec)

    R=edhec[,"Funds of Funds",drop=FALSE]
    Return.cumulative = cumprod(1+R) - 1
    chart.TimeSeries(Return.cumulative)
    chart.TimeSeries(Return.cumulative, colorset = "darkblue", legend.loc = "bottomright",
                     period.areas = cycles.dates, period.color = "lightblue", event.lines = risk.dates,
                     event.labels = risk.labels, event.color = "red", lwd = 2)


