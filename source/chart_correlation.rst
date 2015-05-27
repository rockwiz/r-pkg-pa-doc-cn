chart.Correlation
=================

描述
    相关系数矩阵的可视化。顶部，相关系数的（绝对）值加上cor.test的结果，星型。底部，二元散点图，带一条拟合线。

用法
::

    chart.Correlation(R, histogram = TRUE, ...)

参数
    :R: 给x轴的数据，可以取matrix（矩阵）、vector（向量）或timeseries（时间序列）
    :histogram: TRUE/FALSE，是否显示直方图
    :...: 任何其它传入pairs的参数

备注
    基于 plot at http://addictedtor.free.fr/graphiques/sources/source_137.R

另见
    table.Correlation

范例
::

    data(managers)
    chart.Correlation(managers[,1:8], histogram=TRUE, pch="+")


