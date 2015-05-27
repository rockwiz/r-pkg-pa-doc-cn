apply.rolling
=============
描述
    创建一个作用于一个滚动窗口的函数的结果的时间序列。

    rollapply的封装函数以隐藏一些管理单列zoo对象的复杂性。

用法
::

    apply.rolling(R, width, trim = TRUE, gap = 12, by = 1, FUN = "mean", ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :width: 运用滚动窗口函数的期数
    :gap: 自序列起始用来训练风险计算的数值型期数
    :trim: TRUE/FALSE，是否保持缺损值（NA）造成的排列
    :FUN: 任何可用单一系列收益解析的函数（例如，滚动beta不可以，而Return.annualized可以）
    :by: 在每第by个时间点上为后续宽度点计算FUN
    :...: 其它要传入的参数

返回值
    一个时间序列，为计算结果的zoo对象

另见
    apply rollapply

范例
::

    data(managers)
    apply.rolling(managers[,1,drop=FALSE], FUN="mean", width=36)

