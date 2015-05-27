findDrawdowns
=============

描述
    findDrawdowns将查找回撤的起始时期、终止时期、总数和长度。常与sortDrawdowns一起使用来获取最大回撤

    Drawdowns将把回撤水平计算为百分数，用于chart.Drawdown

用法
::

    findDrawdowns(R, geometric = TRUE, ...)
    Drawdowns(R, geometric = TRUE, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :geometric: 生成几何（TRUE）或简单（FALSE）收益，缺省为TRUE
    :...: 其它要传入的参数

说明
    返回一个未排序的列表：

:return: 回撤深度
:from: 开始时期
:to: 结束时期
:length: 期间长度

参考
    Bacon, C. Practical Portfolio Performance Measurement and Attribution. Wiley. 2004. p. 88

另见
    sortDrawdowns maxDrawdown sortDrawdowns table.Drawdowns table.DownsideRisk chart.Drawdown

范例
::

    data(edhec)
    findDrawdowns(edhec[,"Funds of Funds", drop=FALSE])
    sortDrawdowns(findDrawdowns(edhec[,"Funds of Funds", drop=FALSE]))


