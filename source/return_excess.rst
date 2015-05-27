Return.excess
=============

描述
    计算一项资产在一定时期超出给定无风险收益率的收益。理想情况下，无风险收益率应该对应观测值的每个时期，但是该时期内的一个单一平均收益也可以工作。

用法
::

    Return.excess(R, Rf=0)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rf: 与收益同时期的无风险收益率，或者作为一个单一的数字平均

说明
    期间收益减去期间无风险收益率的均值 :math:`\overline{(R_a-R_f)}`

    或者，期间收益均值减去单一数值无风险收益率 :math:`\overline{R_a}-R_f`

    注意，为了与常见学术使用保持一致，我们假设第二个参数为无风险收益率，你也可用其它时间序列作为第二个参数。一个常见的替代做法是用基准来生成在
    一个指定基准之上的超额收益。


参考
    1. Bacon, Carl. Practical Portfolio Performance Measurement and Attribution. Wiley. 2004. p. 47-52

范例
::

    data(managers)
    head(Return.excess(managers[,1,drop=FALSE], managers[,10,drop=FALSE]))
    head(Return.excess(managers[,1,drop=FALSE], .04/12))
    head(Return.excess(managers[,1:6], managers[,10,drop=FALSE]))
    head(Return.excess(managers[,1,drop=FALSE], managers[,8,drop=FALSE]))


