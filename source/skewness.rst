skewness
========

描述
    计算单变量分布的偏度。

用法
::

    skewness(x, na.rm = FALSE, method = c("moment", "fisher"), ...)

参数
    :na.rm: 逻辑值。缺损值应该被移去？
    :method: 指定计算方法的字符串。要么是“moment”，要么是“fisher”。“moment”方法基于分布偏度的定义，
             重采样（bootstrap 或jackknife）时 ，将用到这些形式。“fisher”方法对应于常见的样本方差的“无偏”（un-biased）定义，
             尽管在有偏度的情况下，精确的无偏（unbiasedness）是不可能的。
    :x: 一个数值型向量或对象
    :...: 要传递的参数

说明
    该函数从RMetrics 包中fUtilities 函数移植过来，消除了每次加载fUtilties的依赖性。除了额外的checkData和labeling，函数是一样的。

另见
    kurtosis

范例
::

    ## mean -
    ## var -
    # Mean, Variance:
    r = rnorm(100)
    mean(r)
    var(r)
    ## skewness -
    skewness(r)
    data(managers)
    skewness(managers)


