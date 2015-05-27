Return.relative
===============
描述
    计算两项资产随时间流逝累积绩效比率，也即一项资产相对另外一项的相对收益

用法
::

    Return.relative(Ra, Rb, ...)

参数
    :Ra: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rb: 基准资产的收益向量
    :...: 忽略

返回值
    相关收益的xts或其它时间序列

另见
    chart.RelativePerformance

范例
::

    data(managers)
    head(Return.relative(managers[,1:3], managers[,8,drop=FALSE]),n=20)


