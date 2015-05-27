chart.Regression
================

描述
    使用散点图显示一组收益相对市场基准的关系。拟合一个线性模型并叠加由此产生的模型。也叠加一条Loess5线作比较。

用法
::

    chart.Regression(Ra, Rb, Rf, excess.returns = FALSE, reference.grid = TRUE, main = "Title", ylab = NULL,
                     xlab = NULL, xlim = NA, colorset = 1:12, symbolset = 1:12, element.color = "darkgray",
                     legend.loc = NULL, ylog = FALSE, fit = c("loess", "linear", "conditional", "quadratic"),
                     span = 2/3, degree = 1, family = c("symmetric", "gaussian"), ylim = NA, evaluation = 50,
                     legend.cex = 0.8, cex = 0.8, lwd = 2, ...)

参数
    :Ra: 一个要检验的收益向量。例如，待查资产
    :Rb: 一个与该资产相比的基准的matrix、data.frame或 timeSeries
    :Rf: 与收益同时期的无风险收益率
    :excess.returns: 逻辑值。超额收益应该用？
    :reference.grid: 如果为TRUE，画出与x、y轴上点排列对齐的网格线
    :main: 设置图表标题，同在plot中一样
    :ylab: 设置y轴标题，与在plot中一样
    :xlab: 设置x轴标题，与在plot中一样
    :xlim: 设置x轴界限，与在plot中一样
    :colorset: 调色板
    :symbolset: 要用的符号，也参见plot中的“pch”
    :element.color: 图表元素的绘制颜色，例如箱线、坐标线等等。缺省为“darkgray”（深灰）
    :legend.loc: 把图例放置在图表上9个位置之一：bottomright、bottom、bottomleft、left、topleft、top、topright、right或center
    :ylog: 没有用到
    :fit: 对“loess”、“linear”或“conditional”，画出一条曲线拟合数据。为正、负基准收益单独画出条件线。“Quadratic”还没有实现
    :span: 传递给loess线拟合，与在loess.smooth中一样
    :degree: 传递给loess线拟合，与在loess.smooth中一样
    :family: 传递给loess线拟合，与在loess.smooth中一样
    :ylim: 设置y轴界限，与在plot中一样
    :evaluation: 传递给loess线拟合，与在loess.smooth中一样
    :cex: 设置cex大小，与在plot中一样
    :legend.cex: 设置图例大小
    :lwd: 设置线宽，与在lines中一样
    :...: 任何其它传入plot的参数

参考
    Chapter 7 of Ruppert(2004) gives an extensive overview of CAPM, its assumptions and deficiencies.

另见
    plot

范例
::

    data(managers)
    chart.Regression(managers[, 1:2, drop = FALSE], managers[, 8, drop = FALSE], Rf = managers[, 10, drop = FALSE],
                     excess.returns = TRUE, fit = c("loess", "linear"), legend.loc = "topleft")

