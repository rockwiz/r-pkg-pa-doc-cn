Beta Co-Moments
===============

描述
    计算收益序列系统或beta协矩的函数，计算高阶矩或“系统”方差（“systematic” variance）、偏度（skewness）和峰度（kurtosis）。

用法
::

    BetaCoVariance(Ra, Rb)
    BetaCoSkewness(Ra, Rb, test = FALSE)
    BetaCoKurtosis(Ra, Rb)

说明
    协矩（co-moments），包括协方差（co-variance）、协偏度（co-skewness）和协峰度（co-kurtosis），不允许直接衡量一项资产对一个投资组
    合的边际影响。因而，Martellini 和Zieman (2007)开发出一个框架来评估一项资产可能带给一个组合的多元性。他们用高阶beta来估算增加一项资
    产对组合在对冲风险（即波动性）、非对称风险（即偏度）和极端风险（即峰度）等方面的影响有多大。那样允许他们显示，如果一项资产相对投资组合
    （或基准）的二阶beta小于1，向组合中增加该资产将会降低组合的方差。对三阶矩和四阶矩，他们也发展出同样的概念。作者提供这些高阶矩beta作为
    资产潜在分散性的度量。

    高阶beta被定义为投资组合的二阶、三阶、四阶矩的协方差、协偏度和协峰度的偏差关于组合权重的比例。beta协方差的计算如下

    .. math::

        \beta^{(2)}_{a,b} = \frac{CoV(R_aR_b)}{\mu^{(2)}R_b}

    Beta协偏度为：

    .. math::

        \beta^{(3)}_{a,b} = \frac{CoS(R_aR_b)}{\mu^{(3)}R_b}

    Beta协峰度为：

    .. math::

        \beta^{(4)}_{a,b} = \frac{CoK(R_aR_b)}{\mu^{(4)}R_b}

    其中，n阶中心矩计算如下：

    .. math::

        \mu^{(n)}(R) = E[{(R-E(R))}^n]

    beta大于1表明不要指望将资产引入到投资组合中能获得分散化好处。反过来，beta小于1则表明增加一项资产会降低增加资产后新组合的波动性和峰度，
    而增加组合的偏度。更具体地说，beta越小，普通风险（即波动性）的分散效应越高。同样，因为极端风险通常以负的偏度和正的峰度为特征，beta越小，
    那么在极端风险方面的分散效应越高（通过改进在险价值或ER反映）。

    当且仅当二阶矩（三阶矩和四阶矩各自的）beta小于1时，一小部分新资产增加到投资组合中导致组合二阶矩的减少（三阶矩和四阶矩分别增加和减少）。

    对偏度，涉及的解释稍多一些。如果投资组合的偏度为负，当三阶矩beta小于1 时，我们预期组合的偏度增加；如果投资组合的偏度为正，
    那么条件是三阶矩beta大于1，而不是小于1。

参数
    :Ra: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rb: 与之比较的指数、基准或第二个资产收益的xts、vector、matrix、data frame、timeSeries或zoo 对象
    :test: 条件，尚未实现

参考

* Boudt, Kris, Brian G. Peterson, and Christophe Croux. 2008. Estimation and Decomposition of Downside Risk for Portfolios with Non-Normal Returns. Journal of Risk. Winter.
* Martellini, Lionel, and Volker Ziemann. 2007. Improved Forecasts of Higher-Order Comoments and Implications for Portfolio Selection. EDHEC Risk and Asset Management Research Centre working paper.

另见
    CoMoments

范例
::

    data(managers)
    BetaCoVariance(managers[, "HAM2", drop=FALSE], managers[, "SP500 TR", drop=FALSE])
    BetaCoSkewness(managers[, "HAM2", drop=FALSE], managers[, "SP500 TR", drop=FALSE])
    BetaCoKurtosis(managers[, "HAM2", drop=FALSE], managers[, "SP500 TR", drop=FALSE])
    BetaCoKurtosis(managers[,1:6], managers[,8,drop=FALSE])
    BetaCoKurtosis(managers[,1:6], managers[,8:7])


