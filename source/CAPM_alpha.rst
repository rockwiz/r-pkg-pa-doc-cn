CAPM.alpha
==========
描述
    计算CAPM alpha，这是一个计算CAPM alpha的封装函数。

    “Alpha”据称是经理技能的度量，它衡量经理收益中没有归因于“Beta”的部分，或绩效中归因于基准的部分。

用法
    CAPM.alpha(Ra, Rb, Rf = 0)

参数
    :Ra: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rb: 基准资产的收益向量
    :Rf: 与收益同时期的无风险收益率

参考

* Sharpe,W.F. Capital Asset Prices: A theory of market equilibrium under conditions of risk. Journal of finance, vol 19, 1964, 425-442.
* Ruppert, David. Statistics and Finance, an Introduction. Springer. 2004.

另见
    CAPM.beta CAPM.utils

范例
::

    # First we load the data
    data(managers)
    CAPM.alpha(managers[,1,drop=FALSE], managers[,8,drop=FALSE], Rf=.035/12)
    CAPM.alpha(managers[,1,drop=FALSE], managers[,8,drop=FALSE], Rf= managers[,10,drop=FALSE])
    CAPM.alpha(managers[,1:6], managers[,8,drop=FALSE], Rf=.035/12)
    CAPM.alpha(managers[,1:6], managers[,8,drop=FALSE], Rf= managers[,10,drop=FALSE])
    CAPM.alpha(managers[,1:6], managers[,8:7,drop=FALSE], Rf=.035/12)
    CAPM.alpha(managers[,1:6], managers[,8:7,drop=FALSE], Rf= managers[,10,drop=FALSE])

