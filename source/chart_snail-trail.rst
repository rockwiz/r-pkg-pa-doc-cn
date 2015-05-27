chart.SnailTrail
================

描述
    显示年化收益和年化标准偏差随时间的滚动计算图。时期较近的线和点较暗。

用法
::

    chart.SnailTrail(R, Rf = 0, main = "Annualized Return and Risk",
                     add.names = c("all", "lastonly", "firstandlast", "none"),
                     xlab = "Annualized Risk", ylab = "Annualized Return", add.sharpe = c(1, 2, 3),
                     colorset = 1:12, symbolset = 16, legend.loc = NULL, xlim = NULL, ylim = NULL, width = 12,
                     stepsize = 12, lty = 1, lwd = 2, cex.axis = 0.8, cex.main = 1, cex.lab = 1, cex.text = 0.8,
                     cex.legend = 0.8, element.color = "darkgray", ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rf: 与收益同时期的无风险收益率
    :main: 设置图表标题，同在plot中一样
    :add.names: 用数据点标绘行名字，缺省为TRUE。可通过将其设为NULL清除
    :xlab: 设置x轴标签，与在plot中一样
    :ylab: 设置y轴标签，与在plot中一样
    :add.sharpe: 画出夏普比率线，其y截距为无风险收益率，斜率代表夏普比率水平（c(1,2,3)）。没有合适值的话（例如，sharpe.ratio = NULL），
                 比率线将被去除
    :colorset: 调色板，缺省设为合理选择
    :symbolset: 从pchin绘图，数据集提交时，以相同的顺序提交一组符号
    :cex.legend: 用来确定图例大小的相对“cex”当前设置的放大倍数
    :element.color: 图表元素的绘制颜色，例如箱线、坐标线等等。缺省为“darkgray”（深灰）
    :legend.loc: 把图例放置在图表上9个位置之一：bottomright、bottom、bottomleft、left、topleft、top、topright、right或center
    :xlim: 设置x轴界限，与在plot中一样
    :ylim: 设置y轴界限，与在plot中一样
    :width: 在其之上应用计算的期数，有时也称之为“窗口”
    :stepsize: 进行计算的频率
    :lty: 设置线型，与在plot中一样
    :lwd: 设置线宽，与在plot中一样
    :cex.lab: 确定标签大小的相对“cex”当前设置的放大倍数，与在plot中一样
    :cex.main: 确定标题大小的相对“cex”当前设置的放大倍数，与在plot中一样
    :cex.axis: 确定坐标轴文本大小的相对“cex”当前设置的放大倍数，与在plot中一样
    :cex.text: 确定文本大小的相对“cex”当前设置的放大倍数，与在plot中一样
    :...: 其它要传入的参数

另见
    chart.RiskReturnScatter

范例
::

    data(managers)
    chart.SnailTrail(managers[,c("HAM2","SP500 TR"),drop=FALSE], width=36, stepsize=12,
                     colorset=c('red','orange'),add.names="firstandlast", rf=.04/12,
                     main="Trailing 36-month Performance Calc'd Every 12 Months")


