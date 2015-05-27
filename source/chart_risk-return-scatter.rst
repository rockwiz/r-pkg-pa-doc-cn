chart.RiskReturnScatter
=======================

描述
    创建一个用来比较经理绩效的年化收益相对年化风险的散点图的封装。将箱线图（box plot）放进边缘部分也有助于识别相对绩效四分位。

用法
::

    chart.RiskReturnScatter(R, Rf = 0, main = "Annualized Return and Risk", add.names = TRUE, xlab = "Annualized Risk",
                            ylab = "Annualized Return", method = "calc", geometric = TRUE, scale = NA,
                            add.sharpe = c(1, 2, 3), add.boxplots = FALSE, colorset = 1, symbolset = 1,
                            element.color = "darkgray", legend.loc = NULL, xlim = NULL, ylim = NULL, cex.legend = 1,
                            cex.axis = 0.8, cex.main = 1, cex.lab = 1, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo、xts对象
    :Rf: 与收益同时期的无风险收益率
    :scale: 一年的期数（日刻度=252，月刻度=12，季刻度=4）
    :geometric: 生成几何（TRUE）或简单（FALSE）收益，缺省为TRUE
    :main: 设置图表标题，同在plot中一样
    :add.names: 用数据点标绘行名字。缺省为TRUE。可通过将其设置为NULL清除
    :xlab: 设置x轴标签，与在plot中一样
    :ylab: 设置y轴标签，与在plot中一样
    :method: 如果设为“calc”，那么该函数从传入的收益中计算。如果设为“nocalc”，那么我们假设R是依此顺序的一列收益和一列风险（例如，年化收益和年化风险）。也可设置不同的风险/收益计算
    :add.sharpe: 夏普比率线，其y截距为无风险收益率，斜率代表夏普比率水平（c(1,2,3)）。没有合适值的话（例如，sharpe.ratio = NULL），比率线将被去除
    :add.boxplots: TRUE/FALSE，在坐标轴上添加数据的箱线图概要
    :colorset: 调色板，缺省设为合理选择
    :symbolset: 从pchin绘图，数据集提交时，以相同的顺序提交一组符号
    :element.color: 图表元素的绘制颜色，例如箱线、坐标线等等。缺省为“darkgray”（深灰）
    :legend.loc: 把图例放置在图表上9个位置之一：bottomright、bottom、bottomleft、left、topleft、top、topright、right或center
    :xlim: 设置x轴界限，与在plot中一样
    :ylim: 设置y轴界限，与在plot中一样
    :cex.axis: 用来确定坐标轴标注大小的相对“cex”当前设置的放大倍数，与在plot中一样
    :cex.legend: 用来确定图例大小的相对“cex”当前设置的放大倍数
    :cex.main: 用来确定标题大小的相对“cex”当前设置的放大倍数
    :cex.lab: 用来确定x和y标签大小的相对“cex”当前设置的放大倍数
    :...: 任何其它传入plot的参数

备注
    Code inspired by a chart on: http://zoonek2.free.fr/UNIX/48_R/03.html

范例
::

    data(edhec)
    chart.RiskReturnScatter(edhec, Rf = .04/12)
    chart.RiskReturnScatter(edhec, Rf = .04/12, add.boxplots = TRUE)

