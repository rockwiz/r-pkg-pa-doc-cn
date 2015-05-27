chart.VaRSensitivity
====================

描述
    按置信区间为多个方法创建在险价值和/或期望差损估计图。

用法
::

    chart.VaRSensitivity(R,
                         methods=c("GaussianVaR", "ModifiedVaR", "HistoricalVaR","GaussianES", "ModifiedES", "HistoricalES"),
                         clean = c("none", "boudt", "geltner"), elementcolor = "darkgray",
                         reference.grid = TRUE, xlab = "Confidence Level", ylab = "Value at Risk", type = "l",
                         lty = c(1, 2, 4), lwd = 1, colorset = (1:12), pch = (1:12), legend.loc = "bottomleft",
                         cex.legend = 0.8, main = NULL, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :methods: 一种或多种计算方法“GaussianVaR”、 “ModifiedVaR”、“HistoricalVaR”、“GaussianES”、 “ModifiedES”、 “HistoricalES”。
              详情参见VaR或ES
    :clean: 经由Return.clean的数据清洗方法。目前选项为“none”、“boudt”或“geltner”
    :elementcolor: 画图表元素的颜色，缺省为“darkgray”（深灰）
    :reference.grid: 如果为TRUE，画出与x、y轴上点排列对齐的网格线
    :ylab: 设置y轴标签，与在plot中一样
    :xlab: 设置x轴标签，与在plot中一样
    :type: 设置图表类型，与在plot中一样
    :lty: 设置线型，与在plot中一样
    :lwd: 设置线宽，与在plot中一样
    :colorset: 调色板，缺省设为合理选择
    :pch: 要用的符号，也参见plot
    :legend.loc: 把图例放置在图表上9个位置之一：bottomright、bottom、bottomleft、left、topleft、top、topright、right或center
    :cex.legend: 用来确定图例大小的相对“cex”当前设置的放大倍数
    :main: 设置图表标题，同在plot中一样
    :...: 其它要传入的参数

说明
    该图表为选定的计算方法显示沿着一系列置信区间的估计VaR 。将一个方法与历史VaR（historical VaR）计算做比较时有用。

参考
    Boudt, K., Peterson, B. G., Croux, C., 2008. Estimation and Decomposition of Downside Risk for Portfolios with Non-Normal Returns. Journal of Risk, forthcoming.

另见
    VaR ES

范例
::

    data(managers)
    chart.VaRSensitivity(managers[,1,drop=FALSE], methods=c("HistoricalVaR", "ModifiedVaR", "GaussianVaR"),
                        colorset=bluefocus, lwd=2)

