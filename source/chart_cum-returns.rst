chart.CumReturns
================

描述
    累积给定定期收益的图表，并画出一条结果线作为“财富指数”（wealth index）。

用法
::

    chart.CumReturns(R, wealth.index = FALSE, geometric=TRUE, legend.loc = NULL, colorset =(1:12),
                     begin = c("first","axis"), ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :wealth.index: 如果wealth.index为TRUE，显示"value of $1"，从1而非0处开始累积收益
    :geometric: 生成几何（TRUE）或简单（FALSE）收益，缺省为TRUE
    :legend.loc: 把图例放置在图表上9个位置之一：bottomright、bottom、bottomleft、left、topleft、top、topright、right或center
    :colorset: 调色板，缺省设为合理选择
    :begin: 把较短序列排列在：

        | first – 给定为参考或较长序列的第一列的值之前，或者
        | axis – 坐标轴的起始值（1或0）

    :...: 其它要传入的参数

说明
    累积收益序列，并将其显示为一个财富指数（wealth index）或累积收益。

参考
    Bacon, Carl. Practical Portfolio Performance Measurement and Attribution. Wiley. 2004.

另见
    chart.TimeSeries plot

范例
::

    data(edhec)
    chart.CumReturns(edhec[,"Funds of Funds",drop=FALSE],main="Cumulative Returns")
    chart.CumReturns(edhec[,"Funds of Funds",drop=FALSE],wealth.index=TRUE, main="Growth of $1")

