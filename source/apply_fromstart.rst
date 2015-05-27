apply.fromstart
===============

描述
    计算一个作用于一个扩展窗口（expanding window）的函数，总是从序列的起点开始

用法
::

    apply.fromstart(R, FUN = "mean" , gap = 1, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo、xts对象
    :FUN: 任何可用单一系列收益解析的函数（例如，滚动beta不可以，而Return.annualized可以）
    :gap: “训练”（train）计算所需从序列开始处的数据点数量
    :...: 其它要传入的参数

另见
    rollapply

范例
::

    data(managers)
    apply.fromstart(managers[,1,drop=FALSE], FUN="mean", width=36)

