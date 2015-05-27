chart.Events
============
描述
    以事件日期为准线标绘一个时间序列。创建一个以一系列日期给定的事件为准线、相邻的之前和之后时序数据按顺序标绘的时间序列标绘图。x轴是时间，
    但是相对指定日期，例如事件发生前后的月数。

用法
::

    chart.Events(R, dates, prior = 12, post = 12, main = NULL, xlab = NULL, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :dates: 与R中格式一样的一个日期列表（如，c("09/03", "05/06")）
    :prior: 事件之前要绘制的期数，正数
    :post: 事件之后要绘制的期数，正数
    :main: 设置图表标题，同在plot中一样
    :xlab: 设置x轴标签，与在plot中一样
    :...: 任何其它传入plotfunction的参数

说明
    这是一个计量经济学中常用于事件研究的图表，通常对应于衰退的日子，展示时间序列进入和退出一个事件的路径。时间轴就是简单的事件发生前后的时期数，
    每条线代表一个不同的事件。注意，如果时期靠得足够近，而显示窗口又足够宽，数据就显得重复了，这可能会使人困惑，
    但函数目前还不允许围绕每个事件的不同窗口。

另见
    chart.TimeSeries plot par

范例
::

    data(managers)
    R = Drawdowns(managers[,2,drop=FALSE])
    n = table.Drawdowns(managers[,2,drop=FALSE])
    chart.Events(Drawdowns(managers[,2,drop=FALSE]), dates = n$Trough, prior=max(na.omit(n$"To Trough")),
                 post=max(na.omit(n$Recovery)), lwd=2, colorset=redfocus, legend.loc=NULL, main = "Worst Drawdowns")

