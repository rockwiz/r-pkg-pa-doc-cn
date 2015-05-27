table.DownsideRisk
==================

描述
    下方风险概要：统计量和样式化事实。创建一个在多个证券或基金间比较下方风险的度量估计表

用法
::

    table.DownsideRisk(R, ci = 0.95, scale = NA, Rf = 0, MAR = 0.1/12, p = 0.95, digits = 4)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :ci: 置信区间，缺省为95%
    :scale: 一年的期数（日刻度=252，月刻度=12，季刻度=4）
    :Rf: 与收益同时期的无风险收益率
    :MAR: 最小可接受收益，与收益的周期性相同
    :p: 用于计算的置信水平，缺省p=.99
    :digits: 进行四舍五入的指定位数

另见
    DownsideDeviation maxDrawdown VaR ES

范例
::

    data(edhec)
    table.DownsideRisk(edhec, Rf=.04/12, MAR =.05/12, p=.95)

    result=t(table.DownsideRisk(edhec, Rf=.04/12, MAR =.05/12, p=.95))

    require("Hmisc")
    textplot(format.df(result, na.blank=TRUE, numeric.dollar=FALSE, cdec=rep(3,dim(result)[2])),
             rmar = 0.8, cmar = 1.5,  max.cex=.9, halign = "center", valign = "top", row.valign="center",
             wrap.rownames=15, wrap.colnames=10, mar = c(0,0,3,0)+0.1)
    title(main="Downside Risk Statistics")


