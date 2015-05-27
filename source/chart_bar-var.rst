chart.BarVaR
============

描述
    在一个柱状图上标绘定期收益，并叠加一个风险矩阵计算。

用法
::

    chart.BarVaR (R, width = 0, gap = 12,
                  methods = c("none", "ModifiedVaR", "GaussianVaR", "HistoricalVaR", "StdDev", "ModifiedES",
                              "GaussianES", "HistoricalES"), p=0.95, clean = c("none", "boudt","geltner"),
                  all = FALSE, ..., show.clean = FALSE, show.horizontal = FALSE, show.symmetric = FALSE,
                  legend.loc="bottomleft", ylim = NA, lwd = 2, colorset = 1:12, lty = c(1,2,4,5,6), ypad=0,
                  legend.cex = 0.8 )

    charts.BarVaR (R, main = "Returns", cex.legend = 0.8, colorset=1:12, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :width: 为滚动期（rolling-period）计算指定的期数。注意width=0时，VaR、ES和Std Dev从时间序列起始处计算 N
    :gap: 从序列开始处算起用来训练风险计算的数值型期数
    :methods: 用来选择后续width 收益的风险参数，可为以下之一：

        - none – 不添加风险线
        - ModifiedVaR – 使用Cornish-Fisher 改进VaR
        - GaussianVaR – 使用传统在险价值
        - HistoricalVaR – 计算历史在险价值
        - ModifiedES – 使用Cornish-Fisher 改进期望差损
        - GaussianES – 使用传统期望差损
        - HistoricalES – 计算历史期望差损
        - StdDev – 每期（per-period）标准差

    :p: VaR或改进VaR计算的置信水平，缺省为.99
    :all: 如果为TRUE，为R中给定的每列计算风险线。如果为FALSE，则只计算第一列的风险线
    :clean: 用来在风险矩阵估计之前从收益数据中清洗异常值的方法。有关详情，参见Return.cleanand VaR
    :show.clean: 如果为TRUE 并且指定了“clean”方法，用清洗后数据覆盖实际数据。有关详情，参见Return.clean
    :...: 任何其它传入chart.TimeSeries的参数
    :show.horizontal: 如果为TRUE，在最近的VaR估计值处显示一条横过时间序列的直线，帮助读者评估距离那么远的异常数量
    :show.symmetric: 如果为TRUE并且矩阵是对称的，将显示矩阵的正值和负值，如同为"StdDev"方法一样
    :ylim: 设置y轴界限，同在plot中一样
    :lwd: 设置线宽，同在plot中一样
    :lty: 设置线型，同在plot中一样
    :legend.loc: 图例位置，同在chart.TimeSeries 中一样
    :ypad: 增加一个用数字表示的补白（padding）到y轴，当legend.loc="bottom"时，保持数据分开。参见以下范例
    :legend.cex: 设置图例文本大小，同在chart.TimeSeries 中一样
    :cex.legend: 设置图例文本大小，同在chart.TimeSeries 中一样
    :main: 设置标题文本，同在chart.TimeSeries 中一样
    :colorset: 调色板，同在chart.TimeSeries 中一样

说明
    注意，StdDev 和VaR是对称计算，所以高、低度量将被绘制出来。

    另一方面，ModifiedVaR是非对称的，因此只画出低端边界。

    创建一个标绘图，包括x轴上的时间和每期一条显示y轴上值的垂直线。

    叠加一条线表明计算出的那个时期风险矩阵值。

另见
    chart.TimeSeries plot ES VaR Return.clean

范例
::

    data(managers)
    # plain
    chart.BarVaR(managers[,1,drop=FALSE], main="Monthly Returns")

    # with risk line
    chart.BarVaR(managers[,1,drop=FALSE], methods="HistoricalVaR", main="... with Empirical VaR from Inception")

    # with lines for all managers in the sample
    chart.BarVaR(managers[,1:6], methods="GaussianVaR", all=TRUE, lty=1, lwd=2,
                 colorset= c("red", rep("gray", 5)), main="... with Gaussian VaR and Estimates for Peers")

    # with multiple methods
    chart.BarVaR(managers[,1,drop=FALSE],methods=c("HistoricalVaR", "ModifiedVaR", "GaussianVaR"),
                 main="... with Multiple Methods")

    # cleaned up a bit
    chart.BarVaR(managers[,1,drop=FALSE],methods=c("HistoricalVaR", "ModifiedVaR", "GaussianVaR"),
                 lwd=2, ypad=.01, main="... with Padding for Bottom Legend")

    # with 'cleaned' data for VaR estimates
    chart.BarVaR(managers[,1,drop=FALSE],methods=c("HistoricalVaR", "ModifiedVaR"), lwd=2, ypad=.01,
                 clean="boudt", main="... with Robust ModVaR Estimate")

    # Cornish Fisher VaR estimated with cleaned data, with horizontal line to show exceptions
    chart.BarVaR(managers[,1,drop=FALSE],methods="ModifiedVaR", lwd=2, ypad=.01, clean="boudt",
                 show.horizontal=TRUE, lty=2, main="... with Robust ModVaR and Line for Identifying Exceptions")

