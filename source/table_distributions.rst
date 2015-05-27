table.Distributions
=============================================================================

描述
    每月的标准差、偏度、样本标准差、峰度、超额峰度、样本偏度和样本超额峰度表

用法
::

    table.Distributions(R, scale = NA, digits = 4)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :scale: 一年的期数（日刻度=252，月刻度=12，季刻度=4）
    :digits: 进行四舍五入的指定位数，用于显示

参考
    Carl Bacon, Practical portfolio performance measurement and attribution, second edition 2008 p.87

另见
    StdDev.annualized skewness kurtosis

范例
::

    data(managers)
    table.Distributions(managers[,1:8])

    require("Hmisc")
    result = t(table.Distributions(managers[,1:8]))

    textplot(format.df(result, na.blank=TRUE, numeric.dollar=FALSE, cdec=c(3,3,1)),
    rmar = 0.8, cmar = 2, max.cex=.9, halign = "center", valign = "top",
    row.valign="center", wrap.rownames=20, wrap.colnames=10,
    col.rownames=c("red", rep("darkgray",5), rep("orange",2)), mar = c(0,0,3,0)+0.1)
    title(main="Portfolio Distributions statistics")