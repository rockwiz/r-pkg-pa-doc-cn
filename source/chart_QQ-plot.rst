chart.QQPlot
============

描述
    标绘一个收益数据相对任一理论分布的Q-Q图。

用法
::

    chart.QQPlot(R, distribution = "norm", ylab = NULL, xlab = paste(distribution, "Quantiles"),
                 main = NULL, las = par("las"), envelope = FALSE, labels = FALSE, col = c(1, 4),
                 lwd = 2, pch = 1, cex = 1, line = c("quartiles", "robust", "none"), element.color = "darkgray",
                 cex.axis = 0.8, cex.legend = 0.8, cex.lab = 1, cex.main = 1, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :distribution: 比较分布的根名称，例如“norm”代表（normal）正态分布，“t”代表t分布。参见范例获知其它资讯
    :xlab: 设置x轴标签，与在plot中一样
    :ylab: 设置y轴标签，与在plot中一样
    :main: 设置图表标题，同在plot中一样
    :las: 设置坐标轴标签排列方向，与在plot中一样
    :envelope: 点级（point-wise）置信包络线的置信水平，或“FALSE”指示无包络（no envelope）
    :labels: 用于交互点标识的点标签向量，或“FALSE”指示无标签（no labels）
    :col: 点和线的颜色，缺省为当前调色板中的第二项（参见“palette”和“par”）
    :lwd: 设置线宽，与在plot中一样
    :pch: 要用的符号，也参见plot
    :cex: 要用的符号，也参见plot
    :line: “quartiles”一条线穿过四分位对，或“robust”代表文件回归线，后者使用MASS包中rlm函数。设定line=none，不输出线
    :element.color: 图表元素的绘制颜色，例如箱线、坐标线等等。缺省为“darkgray”（深灰）
    :cex.legend: 用来确定图例大小的相对“cex”当前设置的放大倍数
    :cex.axis: 用来确定坐标轴标注大小的相对“cex”当前设置的放大倍数
    :cex.lab: 用来确定x和y轴标签大小的相对“cex”当前设置的放大倍数
    :cex.main: 用来确定标题大小的相对“cex”当前设置的放大倍数
    :...: 任何其它传入distribution函数的参数

说明
    分位图是设计用来将数据与理论分布作比较的散点图，以形象化地确定观测值是否来自一个已知族群中。实证分位数相对y轴标绘，而x轴包含理论模型的值。
    一个45度参考线也标绘出来。如果实证数据来自带有选定分布的族群，那么点应该落在参考线附近；离开参考线距离越大，
    数据来自一个带有不同分布4的族群的证据越大。

参考
    主要代码借自（ forked/borrowed/ported）卓越的：

    Fox, John (2007) car: Companion to Applied Regression

    http://www.r-project.org, http://socserv.socsci.mcmaster.ca/jfox/

另见
    qqplot qq.plot plot

范例
::

    library(MASS)
    data(managers)
    x = checkData(managers[,2, drop = FALSE], na.rm = TRUE, method = "vector")
    #layout(rbind(c(1,2),c(3,4)))
    # Panel 1, Normal distribution
    chart.QQPlot(x, main = "Normal Distribution", distribution = 'norm', envelope=0.95)
    # Panel 2, Log-Normal distribution
    fit = fitdistr(1+x, 'lognormal')
    chart.QQPlot(1+x, main = "Log-Normal Distribution", envelope=0.95, distribution='lnorm')#,
                 meanlog = fit$estimate[[1]], sdlog = fit$estimate[[2]])
    ## Not run:
    # Panel 3, Skew-T distribution
    library(sn)
    fit = st.mle(y=x)
    chart.QQPlot(x, main = "Skew T Distribution", envelope=0.95, distribution = 'st', location = fit$dp[[1]],
                 scale = fit$dp[[2]], shape = fit$dp[[3]], df=fit$dp[[4]])
    #Panel 4: Stable Parietian
    library(fBasics)
    fit.stable = stableFit(x,doplot=FALSE)
    chart.QQPlot(x, main = "Stable Paretian Distribution", envelope=0.95, distribution = 'stable',
                 alpha = fit.stable@fit$estimate[[1]], beta = fit.stable@fit$estimate[[2]],
                 gamma = fit.stable@fit$estimate[[3]], delta = fit.stable@fit$estimate[[4]], pm = 0)

    ## End(Not run)

