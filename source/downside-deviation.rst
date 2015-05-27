DownsideDeviation
=================

描述
    收益分布的下方风险（偏差和方差）。
    下方偏差（Downside deviation）、半偏差（semi-deviation）和半方差（ semi-variance）是下方风险的度量。

用法
::

    DownsideDeviation(R, MAR = 0, method=c("subset","full"))
    SemiDeviation(R)
    SemiVariance(R)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :MAR: 最小可接受收益，与收益的周期性相同
    :method: “full”或“subset”之一，指明要使用全序列的长度或MAR之下序列子集的长度作为分母，缺省为“subset”。

说明
    下方偏差，与半偏差相同，在计算风险时剔除正收益。取代用均值收益或零，它使用夏普提出的最小可接受收益（Minimum Acceptable
    Returns，MAR，它也许是均值历史收益或零）。

    要计算它，取比目标收益（或最小可接受收益）短的收益子集，并取它们与目标间的差异。求平方和，并除以收益的总数目以获取一个低于目标的半方差。

    .. math::

        DownsideDeviation(R, MAR)=\delta_{MAR}=\sqrt{\frac{\sum^n_{t=1}{(R_t-MAR)}^2}{n}}

    其中， n或者是整个序列观测值的数量，或者是落在MAR以下的序列子集的观测值数量。

    SemiDeviation或SemiVariance是流行的可用来代替标准差或方差的替代下方风险度量。
    SemiDeviation和SemiVariance作为参数MAR=mean(R)的DownsideDeviation的封装实现。

    在许多函数，如马克维兹优化（Markowitz optimization）中，半偏差可被直接替换，协方差矩阵可从半偏差或均值以下收益向量，
    而不是方差或全部收益向量中构造。

    对半偏差，按惯例，n的值设为全部观测值的数量；对半方差，n的值设为均值以下收益的子集。应该注意，
    如果用低于均值或MAR的收益的时间序列构造一个用于投资组合优化的半协方差（semi-covariance）矩阵，尽管这是正确的半方差数学定义，
    其结果没有任何意义。

    Sortino建议采用连续拟合分布而非观测值的离散分布来计算下方偏差。这将有非常重要的实用性，尤其在少量观测值的情况下。
    他建议用对数分布或基于相关风格指数的拟合分布来构造低于MAR的收益以提高最终解释的可信度。希望在将来，我们会给该函数一个fitted选项。
    很高兴接受这方面的贡献。

参考
    1. Sortino, F. and Price, L. Performance Measurement in a Downside Risk Framework. Journal of Investing. Fall 1994, 59-65.
    2. Plantinga, A., van der Meer, R. and Sortino, F. The Impact of Downside Risk on Risk-Adjusted Performance of Mutual Funds in the Euronext Markets. July 19, 2001. Available at SSRN: http://ssrn.com/abstract=277352
    3. http://www.sortino.com/htm/performance.htm see especially end note 10
    4. http://en.wikipedia.org/wiki/Semivariance

范例
::

    data(managers)
    sd(managers[,1:6], na.rm=TRUE)
    DownsideDeviation(managers[,1:6])  # MAR 0%
    DownsideDeviation(managers[,1:6], MAR = .04/12) #MAR 4%
    SemiDeviation(managers[,1,drop=FALSE])
    SemiDeviation(managers[,1:6])
    SemiVariance (managers[,1,drop=FALSE])
    SemiVariance (managers[,1:6]) #calculated using method="subset"


