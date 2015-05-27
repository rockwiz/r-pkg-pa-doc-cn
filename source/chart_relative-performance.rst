chart.RelativePerformance
=========================

描述
    多个收益序列之间的相对绩效图。标绘一个时间序列图，显示两个资产在每个时点累积绩效的比率以使绩效低劣期和良好期更易查看。

用法
::

    chart.RelativePerformance(Ra, Rb, main = "Relative Performance", xaxis = TRUE, colorset = (1:12),
                              legend.loc = NULL, ylog = FALSE, elementcolor = "darkgray", lty = 1, cex.legend=0.7, ...)

参数
    :Ra: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rb: 基准资产的收益向量
    :main: 设置图表标题，同在plot中一样
    :xaxis: 如果为TRUE，画出x轴
    :colorset: 调色板，缺省设为合理选择
    :elementcolor: 不太重要的图表元素的颜色，例如箱线、坐标线等等。替换darken
    :legend.loc: 把图例放置在图表上9个位置之一：bottomright、bottom、bottomleft、left、topleft、top、topright、right或center
    :ylog: TRUE/FALSE，将y轴设为对数刻度。缺省为FALSE
    :cex.legend: 用来确定图例大小的相对“cex”当前设置的放大倍数
    :lty: 设置线型，与在plot中一样
    :...: 其它要传入的参数

说明
    要显示经历不同时期的低劣绩效和良好绩效，一个时间序列视图比较有帮助。图表的值不如直线的斜率重要。如果斜率为正，第一项资产（分子）的
    绩效表现超过第二项，反之亦然。也许用于查看相对同等组和同等组指数的基金收益，或者，它可用于将同行各自与一个资产类或同等组指数对比评价。

另见
    Return.relative

范例
::

    data(managers)
    chart.RelativePerformance(managers[, 1:6, drop=FALSE], managers[, 8, drop=FALSE], colorset=rich8equal,
                            legend.loc="bottomright", main="Relative Performance to S&P")

