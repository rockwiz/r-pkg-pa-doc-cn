Return.portfolio
================

描述
    计算资产组合的加权收益。如果有一个单一加权向量，或想要等权重组合，使用Return.portfolio 。如果有一个定期再平衡的组合，
    对应多个不同权重的时期，用Return.rebalancing 。两个函数都从收益序列中抽取仅包括提供了权重的资产的收益子集

用法
::

    Return.portfolio(R, weights = NULL, wealth.index = FALSE, contribution = FALSE, geometric = TRUE, ...)
    Return.rebalancing(R, weights, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :weights: 一个包含资产权重的时间序列或单行矩阵/向量，权重表示为百分数
    :wealth.index: TRUE/FALSE ，是否返回财富指数，缺省为FALSE
    :contribution: 如果为TRUE，添加在此期间该项资产贡献的加权收益
    :geometric: 生成几何（TRUE）或简单（FALSE）收益，缺省为TRUE
    :...: 其它要传入的参数

说明
    Return.rebalancing为再平衡期间xts风格子集使用权重时间序列或矩阵。再平衡期间可理解成在条形图封闭后立即生效。
    因此，3月31日的再平衡实际上在4月1日起作用，12月31日再平衡将在1月1日生效，等等。之所以选择这种惯例，因为它符合通常用法，
    也因为它通过端点简化了xts日期提取。

    Return.rebalancing只在每日或更低频率上做再平衡。如果要在日内（intraday）做再平衡，应该用交易/价格框架，而不是基于权重的收益框架。

返回值
    返回一个通过weights 参数加权的收益时间序列，可能包括各期贡献

参考
    Bacon, C. Practical Portfolio Performance Measurement and Attribution. Wiley. 2004. Chapter 2

另见
    Return.calculate

范例
::

    data(edhec)
    data(weights)

    # calculate an equal weighted portfolio return
    round(Return.portfolio(edhec),4)

    # now return the contribution too
    round(Return.portfolio(edhec,contribution=TRUE),4)

    # calculate a portfolio return with rebalancing
    round(Return.rebalancing(edhec,weights),4)



