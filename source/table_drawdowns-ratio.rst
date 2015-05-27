table.DrawdownsRatio
====================

描述
    Calmar比率、Sterling比率、Burke比率、痛苦指数、Ulcer指数、痛苦比率和Martin比率

用法
::

    table.DrawdownsRatio(R, Rf = 0, scale = NA, digits = 4)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rf: 与收益同时期的无风险收益率
    :scale: 一年的期数（日刻度=252，月刻度=12，季刻度=4）
    :digits: 进行四舍五入的指定位数

参考
    Bacon, C. Practical Portfolio Performance Measurement and Attribution. Wiley. 2004. p. 88

另见
    CalmarRatio BurkeRatio PainIndex UlcerIndex PainRatio MartinRatio

范例
::

    data(managers)
    table.DrawdownsRatio(managers[,1:8])

    require("Hmisc")
    result = t(table.DrawdownsRatio(managers[,1:8], Rf=.04/12))

    textplot(format.df(result, na.blank=TRUE, numeric.dollar=FALSE, cdec=c(3,3,1)),
    rmar = 0.8, cmar = 2, max.cex=.9, halign = "center", valign = "top",
    row.valign="center", wrap.rownames=20, wrap.colnames=10,
    col.rownames=c("red", rep("darkgray",5), rep("orange",2)), mar = c(0,0,3,0)+0.1)
    title(main="Drawdowns ratio statistics")

