SharpeRatio
===========

描述
    计算收益相对StdDev 或VaR或ES 的传统或改进夏普比率。夏普比率（Sharpe ratio）仅仅是每个风险单位（表示为波动性）的收益。经典情况下，
    风险单位是收益的标准差。

    .. math::

        \frac{\overline{(R_\alpha-R_f)}}{\sqrt{\sigma{(R_\alpha-R_f)}}}

    William Sharpe现在建议InformationRatio的使用优先于原始的夏普比率。

    夏普比率越高，“风险”和收益的连结绩效越好。

    正如所提到的，传统的夏普比率是用标准差代表风险的收益的风险调整度量。

    一些论文现在建议用改进的Cornish-Fisher VaR 或CVaR / 期望差损（Expected Shortfall）作为风险度量来使用“改进夏普”比率。

    我们最近扩展了这个概念，为标准差、高斯VaR（Gaussian VaR）、改进VaR（modified VaR）、高斯期望差损（Gaussian Expected Shortfall）
    和改进期望差损（modified Expected Shortfall）创建多元改进夏普类（modified Sharpe-like）比率。参见VaR和ES。

    可通过...给VaR和ES传递额外的参数。最重要的参数可能是“method”。

    该函数返回一个输入数据同时期的传统或改进夏普比率（例如，月度data->月度SR）。

用法
::

    SharpeRatio.modified(R, Rf = 0, p = 0.95, FUN = c("StdDev","VaR","ES"), weights=NULL, ...)
    SharpeRatio(R, Rf = 0, p = 0.95, FUN = c("StdDev","VaR","ES"), weights=NULL, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rf: 与收益同时期的无风险收益率
    :p: 用于计算的置信水平，缺省p=.95
    :FUN: “StdDev”、“VaR”或“ES”之一，用作分母
    :weights: 投资组合权重向量，缺省为NULL
    :...: 任何其它传入VaR 或ES函数的参数

参考
    1. Sharpe, W.F. The Sharpe Ratio,Journal of Portfolio Management,Fall 1994, 49-58.
    2. Laurent Favre and Jose-Antonio Galeano. Mean-Modified Value-at-Risk Optimization with Hedge Funds. Journal of Alternative Investment, Fall 2002, v 5.

另见
    SharpeRatio.annualized InformationRatio TrackingError ActivePremium SortinoRatio VaR ES

范例
::

    data(managers)
    SharpeRatio(managers[,1,drop=FALSE], Rf=.035/12, FUN="StdDev")
    SharpeRatio(managers[,1,drop=FALSE], Rf = managers[,10,drop=FALSE], FUN="StdDev")
    SharpeRatio(managers[,1:6], Rf=.035/12, FUN="StdDev")
    SharpeRatio(managers[,1:6], Rf = managers[,10,drop=FALSE], FUN="StdDev")

    data(edhec)
    SharpeRatio(edhec[, 6, drop = FALSE], FUN="VaR")
    SharpeRatio(edhec[, 6, drop = FALSE], Rf = .04/12, FUN="VaR")
    SharpeRatio(edhec[, 6, drop = FALSE], Rf = .04/12, FUN="VaR" , method="gaussian")
    SharpeRatio(edhec[, 6, drop = FALSE], FUN="ES")

    # and all the methods
    SharpeRatio(managers[,1:9], Rf = managers[,10,drop=FALSE])
    SharpeRatio(edhec,Rf = .04/12)


