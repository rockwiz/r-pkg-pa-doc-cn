CoMoments
=========

描述
    计算协偏度和协峰度作为两个互为参考的资产的偏度和峰度。

用法
::

    CoSkewnessMatrix(R, ...)
    CoKurtosisMatrix(R, ...)

    CoVariance(Ra, Rb)
    CoSkewness(Ra, Rb)
    CoKurtosis(Ra, Rb)

    M3.MM(R, ...)
    M4.MM(R, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Ra: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rb: 一个用来比较的指数、基准、组合或第二项资产的收益的xts、vector、matrix、data frame、timeSeries或zoo对象
    :...: 其它要传入的参数

说明
    Ranaldo and Favre (2005) 将协偏度（coskewness）和协峰度（cokurtosis）定义为与参考资产或资产组合一起分析的给定资产的偏度与峰度。
    增加一项对组合协偏度有显著水平的资产到一个资产组合，例如一个对称基金中能提高或降低由此产生的组合的偏度。同样，
    向一个对冲基金增加一个正的协峰度系数将增加组合的峰度。

    协矩（co-moments）有助于度量每项资产给组合带来风险的边际贡献。因此，资产收益分布的协矩作为组合优化除协方差矩阵之外的输入是有用的。
    Martellini 和Ziemann (2007)指出资产组合选择问题变成在包含期望收益与资产收益的二阶、三阶和四阶中心矩的四个维度中选择切点之一的问题。

    甚至在优化问题之外，度量协矩也将是一种评估一项资产是否可能给一个资产组合不仅在普通风险（即波动性）而且在非对称（偏度）和极端事件（峰度）
    风险方面带来潜在分散性的有用工具。

参考
    1. Boudt, Kris, Brian G. Peterson, and Christophe Croux. 2008. Estimation and Decomposition of Downside Risk for Portfolios with Non-Normal Returns. Journal of Risk. Winter.
    2. Martellini, Lionel, and Volker Ziemann. 2007. Improved Forecasts of higher-Order Comoments
    3. and Implications for Portfolio Selection. EDHEC Risk and Asset Management Research Centre working paper.
    4. Ranaldo, Angelo, and Laurent Favre Sr. 2005. How to Price Hedge Funds: From Two- to Four-Moment CAPM. SSRN eLibrary.
    5. Scott, Robert C., and Philip A. Horvath. 1980. On the Direction of Preference for Moments of Higher Order than the Variance. Journal of Finance 35(4):915-919.

另见
    BetaCoSkewness BetaCoKurtosis BetaCoMoments

范例
::

    data(managers)
    CoVariance(managers[, "HAM2", drop=FALSE], managers[, "SP500 TR", drop=FALSE])
    CoSkewness(managers[, "HAM2", drop=FALSE], managers[, "SP500 TR", drop=FALSE])
    CoKurtosis(managers[, "HAM2", drop=FALSE], managers[, "SP500 TR", drop=FALSE])


