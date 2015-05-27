chart.RollingCorrelation
========================

描述
    多项资产滚动相关系数图表。在线图中创建一个滚动相关系数矩阵的封装函数。

用法
::

    chart.RollingCorrelation(Ra, Rb, width = 12, xaxis = TRUE, legend.loc = NULL, colorset = (1:12), na.pad = FALSE, ...)

参数
    :Ra: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rb: 基准资产的收益向量
    :width: 应用滚动函数窗口的期数
    :xaxis: 如果为TRUE，画出x轴
    :legend.loc: 把图例放置在图表上9个位置之一：bottomright、bottom、bottomleft、left、topleft、top、topright、right或center
    :colorset: 调色板，缺省设为合理选择
    :na.pad: TRUE/FALSE。如果为TRUE，将任何不在结果中的时间以NA值添加；如果为FALSE，则丢弃那些时间
    :...: 其它要传入的参数

范例
::

    # First we get the data
    data(managers)
    chart.RollingCorrelation(managers[, 1:6, drop=FALSE],
                             managers[, 8, drop=FALSE], colorset=rich8equal, legend.loc="bottomright", width=24,
                             main = "Rolling 12-Month Correlation")

