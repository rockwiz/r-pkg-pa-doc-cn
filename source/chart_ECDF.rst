chart.ECDF
==========
描述
    创建一个叠加累积分布函数（cumulative distribution function ，CDF）的经验累积分布函数
    （emperical cumulative distribution function ，ECDF）。

用法
::

    chart.ECDF(R, main = "Empirical CDF", xlab = "x", ylab = "F(x)", colorset = c("black", "#005AFF"),
               lwd = 1, xlim = NULL, ylim = NULL, lty = c(1, 1), element.color = "darkgray", ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo、xts对象
    :main: 设置图表标题，同在plot中一样
    :xlab: 设置x轴标签，与在plot中一样
    :ylab: 设置y轴标签，与在plot中一样
    :colorset: 调色板，缺省为c(black, "\#005AFF")，其中第一个值给单步函数（step function）标色，第二个颜色用于拟合正态
    :lwd: 设置线宽，与在plot中一样
    :xlim: 设置x轴界限，与在plot中一样
    :ylim: 设置y轴界限，与在plot中一样
    :element.color: 设置图表元素颜色，缺省为“darkgray”
    :lty: 设置线型，与在plot中一样
    :...: 任何其它传入plot的参数

说明
    经验累积分布（简称ECDF）计算观测值小于或等于给定值的分数。由此产生的绘图是一个在每个观测值上分数的单步函数。该函数使用ecdf ，
    并也在一个拟合正态函数上叠加CDF。

    受Ruppert (2004)中的一张图启发。

参考
    1.Ruppert, David. Statistics and Finance, an Introduction. Springer. 2004. Ch. 2 Fig. 2.5
    2.http://www.stat.tamu.edu/~ljin/Finance/chapter2/Fig2_5.txt

另见
    plot ecdf

范例
::

    data(edhec)
    chart.ECDF(edhec[, 1, drop=FALSE])

