charts.PerformanceSummary
=========================

描述
    创建合并财富指数、期间绩效和回撤图。对一组收益，创建一个财富指数图（wealth index chart）、月度绩效柱状图（bar）以及回撤水下图。

用法
::

    charts.PerformanceSummary(R, Rf = 0, main = NULL, geometric=TRUE, methods = "none", width = 0, event.labels = NULL,
                            ylog= FALSE, wealth.index = FALSE, gap = 12, begin =c("first", "axis"),
                            legend.loc = "topleft", p=0.95,...)

参数

:R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
:Rf: 与收益同时期的无风险收益率
:p: 用于计算的置信水平，缺省p=.95
:main: 设置图表标题，与在plot中一样
:geometric: 生成几何（TRUE）或简单（FALSE）收益，缺省为TRUE
:methods: 选择后续width 收益的风险参数用于chart.BarVaR面板，可为以下之一：

* none – 不添加风险线
* ModifiedVaR – 使用Cornish-Fisher 改进 VaR
* GaussianVaR – 使用传统在险价值
* HistoricalVaR – 计算历史在险价值
* ModifiedES – 使用Cornish-Fisher 改进期望差损
* GaussianES – 使用传统期望差损
* HistoricalES – 计算历史期望差损
* StdDev – 每期（per-period）标准差

:begin: 把传入chart.CumReturns的较短序列排列在：

* first – 给定为参考或较长序列的第一列的值之前，或者
* axis – 坐标轴的起始值（1或0）

:event.labels: TRUE/FALSE，是否显示历史市场震动事件（shock events）线和标签
:wealth.index: 如果wealth.index为TRUE，显示"value of $1"，从1而非0处开始累积收益
:width: 应用滚动函数窗口的期数
:gap: 从序列开始处起用来训练风险计算的期数
:ylog: TRUE/FALSE，将y轴设为对数刻度。缺省为FALSE
:legend.loc: 图例在图表上的位置，可设为NULL，或9个位置之一：bottomright、bottom、bottomleft、left、topleft、top、topright、right或center
:...: 其它要传入的参数

备注
    大多数输入和“plot”一样，并且基本都包括进来了，以便可设置一些实用的缺省值。

另见
    chart.CumReturns chart.BarVaR chart.Drawdown

范例
::

    data(edhec)
    charts.PerformanceSummary(edhec[,c(1,13)])

