table.ProbOutPerformance
========================

描述
    卓越绩效和基准比较报告

用法
::

    table.ProbOutPerformance(R, Rb, period_lengths = c(1, 3, 6, 9, 12, 18, 36))

参数
    :R: 一个资产收益的时间序列或zoo, xts对象
    :Rb: 基准资产的收益时间序列或zoo, xts对象
    :period_lengths: 用户想要比较的时期向量，即 c(1,3,6,9,12,18,36)

说明
    返回一张记录不同时期长度下绩效超出基准的次数和概率表。作为资产或策略稳健性分析的工具，可被用于给出投资者投资绩效超出基准的概率。

范例
::

    data(edhec)
    table.ProbOutPerformance(edhec[,1],edhec[,2])
    title(main= Table of Convertible Arbitrage vs Benchmark )


