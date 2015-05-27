table.HigherMoments
===================

描述
    高阶矩概要：统计量和样式化事实。收益分布的高阶矩和高阶协矩的概要。用于确定潜在的分散性。在一些论文中也称为“系统”（systematic）矩。

用法
::

    table.HigherMoments(Ra, Rb, scale = NA, Rf = 0, digits = 4, method = "moment")

参数
    :Ra: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rb: 基准资产的收益向量
    :scale: 一年的期数（日刻度=252，月刻度=12，季刻度=4）
    :Rf: 与收益同时期的无风险收益率
    :digits: 进行四舍五入的指定位数
    :method: 计算峰度的方法，以下之一： excess、moment、fisher

参考
    Martellini L., Vaissie M., Ziemann V. Investing in Hedge Funds: Adding Value through Active Style Allocation Decisions. October 2005. Edhec Risk and Asset Management Research Centre.

另见
    CoSkewness CoKurtosis BetaCoVariance BetaCoSkewness BetaCoKurtosis skewness kurtosis

范例
::

    data(managers)
    table.HigherMoments(managers[,1:3],managers[,8,drop=FALSE])
    result=t(table.HigherMoments(managers[,1:6],managers[,8,drop=FALSE]))
    rownames(result)=colnames(managers[,1:6])

    require("Hmisc")

    textplot(format.df(result, na.blank=TRUE, numeric.dollar=FALSE, cdec=rep(3,dim(result)[2])),
             rmar = 0.8, cmar = 1.5,  max.cex=.9, halign = "center", valign = "top", row.valign="center",
             wrap.rownames=5, wrap.colnames=10, mar = c(0,0,3,0)+0.1)
    title(main="Higher Co-Moments with SP500 TR")

