mean.geometric
==============

描述
    计算给定观测值序列均值相关属性，包括geometric、stderr、LCL和UCL

    | mean.geometric：几何均值
    | mean.stderr： 均值标准误（S.E. mean）
    | mean.LCL： 均值置信水平下界（LCL）
    | mean.UCL：均值置信水平上界（UCL）

用法
::

    ## S3 method for class 'geometric':
    mean(x, ...)
    ## S3 method for class 'stderr':
    mean(x, ...)
    ## S3 method for class 'UCL':
    mean(x, ci = 0.95, ...)
    ## S3 method for class 'LCL':
    mean(x, ci = 0.95, ...)

参数
    :x: 计算均值统计量的向量、矩阵、数据框或时间序列
    :ci: 置信区间
    :...: 其它要传入的参数

另见
    sd mean

范例
::

    data(edhec)
    mean.geometric(edhec[,"Funds of Funds"])
    mean.stderr(edhec[,"Funds of Funds"])
    mean.UCL(edhec[,"Funds of Funds"])
    mean.LCL(edhec[,"Funds of Funds"])

