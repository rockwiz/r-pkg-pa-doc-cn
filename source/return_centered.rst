Return.centered
===============

描述
    计算中心化收益。n阶中心矩计算如下

    .. math::

        \mu^{(n)}(R)=E[{(R-E(R))}^n]

    这些函数被PerformanceAnalytics内部用于计算多元分布的中心距和投资组合分布的标准化矩。展示在这里只是为了那些要直接使用它们的用户，
    如果可以，我们会提供更多文档。

用法
::

    centeredcomoment (Ra, Rb, p1, p2, normalize = FALSE)
    centeredmoment (R, power)
    Return.centered (R, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Ra: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rb: 一个用来比较的指数、基准、组合或第二项资产的收益的xts、vector、matrix、data frame、timeSeries或zoo对象
    :power: 要计算的幂或矩
    :p1: 协矩的一次幂
    :p2: 协矩的二次幂
    :normalize: 是否要计算结果标准化以符合常见用法，或保留缺省的数学含义
    :...: 其它要传入的参数

说明
    这些函数首先由Boudt、Peterson和Croux于2008年采用，接着我们将其用于其它研究

参考
    1. Boudt, Kris, Brian G. Peterson, and Christophe Croux. 2008. Estimation and Decomposition of Downside Risk for Portfolios with Non-Normal Returns. Journal of Risk. Winter.
    2. Martellini, Lionel, and Volker Ziemann. 2007. Improved Forecasts of Higher-Order Comoments
    3. and Implications for Portfolio Selection. EDHEC Risk and Asset Management Research Centre working paper.
    4. Ranaldo, Angelo, and Laurent Favre Sr. 2005. How to Price Hedge Funds: From Two- to Four-Moment CAPM. SSRN eLibrary.
    5. Scott, Robert C., and Philip A. Horvath. 1980. On the Direction of Preference for Moments of Higher Order than the Variance. Journal of Finance 35(4):915-919.

范例
::

    data(managers)
    Return.centered(managers[,1:3,drop=FALSE])


