kurtosis
========

描述
    计算一个单变量分布的峰度

用法
::

    kurtosis(x, na.rm = FALSE, method = c("excess", "moment", "fisher"), ...)

参数
    :na.rm: 逻辑值。缺损值应该被移去？
    :method: 指定计算方法的字符串。 “moment”、“fisher”或“excess”。
            如果选择“excess”，那么峰度的值通过“moment”方法计算，并将其结果减去3。
            “moment”方法基于分布偏度的定义，重采样（bootstrap 或jackknife）时 ，将用到这些形式。
            “fisher”方法对应于常见的样本方差的“无偏”（un-biased）定义，尽管在有偏度的情况下，
            精确的无偏（unbiasedness）是不可能的。
    :x: 一个数值型向量或对象
    :...: 要传递的参数

说明
    该函数从RMetrics包中fUtilities函数移植过来，消除了每次加载fUtilties的依赖性。除了额外的checkData和labeling，函数是一样的。

另见
    skewness.

范例
::

    ## mean -
    ## var -
    # Mean, Variance:
    r = rnorm(100)
    mean(r)
    var(r)
    ## kurtosis -
    kurtosis(r)
    data(managers)
    kurtosis(managers[,1:8])


