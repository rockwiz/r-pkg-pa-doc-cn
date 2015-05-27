StdDev
======

描述
    计算单变量、多元变量序列的标准差，也计算投资组合标准差的成分贡献

用法
::

    StdDev(R, ..., clean = c("none", "boudt", "geltner"), portfolio_method = c("single", "component"),
           weights = NULL, mu = NULL, sigma = NULL)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo、xts对象
    :...: 其它要传入的参数
    :clean: 经由Return.clean的数据清洗方法。目前选项为“none”、“boudt”或“geltner”
    :portfolio_method: “single”、“component”之一，定义是做单变量/多元还是成分计算，参见说明部分
    :weights: 组合权重向量，缺省为NULL，参见说明部分
    :mu: 如果为单变量，mu是序列均值。否则，mu是收益序列均值向量，缺省为NULL，参见说明部分
    :sigma: 如果为单变量，sigma 是序列方差。否则，sigma是收益序列协方差矩阵，缺省为NULL，参见说明部分

说明
    该封装函数为单变量、多元变量和投资组合标准差的成分贡献（component decomposition）提供快速矩阵计算。

    可能需要这些说明的只有成分贡献。它提供每个投资组合元素给整个组合单变量标准差贡献的加权分解。

    形式上，这是每个单变量标准差关于权重的偏导数。

    正如VaR一样，该贡献也表现为两种形式：标量形式，其相加之和为组合单变量标准差的标量形式；百分比形式，其相加之和为100%。注意，
    如同其它贡献的计算，贡献可为负值。这表明所研究的资产对组合的总体标准差起到分散作用，提高它相当于组合其余部分的权重将降低组合总体标准差。

另见
    Return.clean sd

范例
::

    data(edhec)
    # first do normal StdDev calc
    StdDev(edhec)
    # or the equivalent
    StdDev(edhec, portfolio_method="single")
    # now with outliers squished
    StdDev(edhec, clean="boudt")
    # add Component StdDev for the equal weighted portfolio
    StdDev(edhec, clean="boudt", portfolio_method="component")


