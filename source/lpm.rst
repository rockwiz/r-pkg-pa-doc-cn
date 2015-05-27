lpm
===

描述
    计算均值或指定阈值的下偏矩

用法
::

    lpm(R, n = 2, threshold = 0, about_mean = FALSE)

参数
    :na.rm: 逻辑值。缺损值应该被移去？
    :method: 指定计算方法的字符串。 “moment”、“fisher”或“excess”。
            如果选择“excess”，那么峰度的值通过“moment”方法计算，并将其结果减去3。“moment”方法基于分布偏度的定义，
            重采样（bootstrap 或jackknife）时 ，将用到这些形式。“fisher”方法对应于常见的样本方差的“无偏”（un-biased）定义，
            尽管在有偏度的情况下，精确的无偏（unbiasedness）是不可能的。
    :x: 一个数值型向量或对象
    :...: 要传递的参数

    :R: xts数据
    :n: 收益的n阶矩
    :threshold: 阈值可以是均值或任何其它期望点
    :about_mean: TRUE/FALSE，计算阈值以下均值的LPM或用阈值解出LPM（如果FALSE）

说明
    下偏距捕捉参考点的负偏差。该参考点可以是均值或对投资者有意义的指定阈值

参考
    1. Huffman S.P. & Moll C.R., "The impact of Asymmetry on Expected Stock Returns: An Investigation of Alternative Risk Measures", Algorithmic Finance 1, 2011 p. 79-93
