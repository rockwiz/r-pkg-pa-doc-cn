table.AnnualizedReturns
=======================

描述
    年化收益、年化标准差和年化夏普的表格

用法
::

    table.AnnualizedReturns(R, scale = NA, Rf = 0, geometric = TRUE, digits = 4)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :geometric: 生成几何（TRUE）或简单（FALSE）收益，缺省为TRUE
    :scale: 一年的期数（日刻度=252，月刻度=12，季刻度=4）
    :Rf: 与收益同时期的无风险收益率
    :digits: 进行四舍五入的指定位数

另见
    Return.annualized StdDev.annualized SharpeRatio.annualized

范例
::

    data(managers)
    table.AnnualizedReturns(managers[,1:8])

    require("Hmisc")
    result = t(table.AnnualizedReturns(managers[,1:8], Rf=.04/12))

    textplot(format.df(result, na.blank=TRUE, numeric.dollar=FALSE, cdec=c(3,3,1)), rmar = 0.8,
             cmar = 2,  max.cex=.9, halign = "center", valign = "top", row.valign="center",
             wrap.rownames=20, wrap.colnames=10, col.rownames=c("red", rep("darkgray",5), rep("orange",2)),
             mar = c(0,0,3,0)+0.1)
    title(main="Annualized Performance")

