table.DownsideRiskRatio
=======================

描述
    下方风险、年化下方风险、下方潜力、Omega、Sortino比率、上方潜力、上方潜力比率和Omega-Sharpe比率

用法
::

    table.DownsideRiskRatio(R, MAR = 0, scale = NA, digits = 4)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :MAR: 最小可接受收益，与收益的周期性相同
    :scale: 一年的期数（日刻度=252，月刻度=12，季刻度=4）
    :digits: 进行四舍五入的指定位数

参考
    Carl Bacon, Practical portfolio performance measurement and attribution, second edition 2008 p.98

另见
    CalmarRatio BurkeRatio PainIndex UlcerIndex PainRatio MartinRatio

范例
::

    data(managers)
    table.DownsideRiskRatio(managers[,1:8])

    require("Hmisc")
    result = t(table.DownsideRiskRatio(managers[,1:8]))

    textplot(format.df(result, na.blank=TRUE, numeric.dollar=FALSE, cdec=c(3,3,1)),rmar = 0.8, cmar = 2,
             max.cex=.9, halign = "center", valign = "top", row.valign="center", wrap.rownames=20, wrap.colnames=10,
             col.rownames=c("red", rep("darkgray",5), rep("orange",2)), mar = c(0,0,3,0)+0.1)
    title(main="Downside risk statistics")


