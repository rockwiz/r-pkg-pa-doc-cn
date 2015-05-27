sortDrawdowns
=============
描述
    sortDrawdowns（findDrawdowns(R)）按最坏到最好的顺序给出回撤。

用法
::

    sortDrawdowns(runs)

参数
    :runs: 传入来自findDrawdowns ，要被排序的回撤区间（runs）数组

说明
    返回一个排序后的列表：

* return depth of drawdown 收益回撤深度
* from starting period 自起始时期
* to ending period 至终止时期
* length in periods 时期中的长度

参考
    Bacon, C. Practical Portfolio Performance Measurement and Attribution. Wiley. 2004. p. 88

另见
    DownsideDeviation maxDrawdown findDrawdowns sortDrawdowns chart.Drawdown table.Drawdowns table.DownsideRisk

范例
::

    data(edhec)
    findDrawdowns(edhec[,"Funds of Funds", drop=FALSE])
    sortDrawdowns(findDrawdowns(edhec[,"Funds of Funds", drop=FALSE]))


