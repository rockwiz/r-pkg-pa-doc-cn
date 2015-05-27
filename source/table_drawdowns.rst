table.Drawdowns
===============

描述
    最坏回撤概要：统计量和样式化事实。创建用于显示最恶劣回撤的统计量的表格。

用法
::

    table.Drawdowns(R, top= 5, digits = 4)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :top: 包括的回撤数
    :digits: 进行四舍五入的指定位数

参考
    Bacon, C. Practical Portfolio Performance Measurement and Attribution. Wiley. 2004. p. 88

另见
    DownsideDeviation maxDrawdown findDrawdowns sortDrawdowns chart.Drawdown table.DownsideRisk

范例
::

    data(edhec)
    table.Drawdowns(edhec[,1,drop=FALSE])
    table.Drawdowns(edhec[,12,drop=FALSE])
    data(managers)
    table.Drawdowns(managers[,8,drop=FALSE])

    result=table.Drawdowns(managers[,1,drop=FALSE])

    # This was really nice before Hmisc messed up 'format' from R-base
    # require("Hmisc")
    # textplot(Hmisc::format.df(result, na.blank=TRUE, numeric.dollar=FALSE, cdec=c(rep(3,4), rep(0,3))),
    #          rmar = 0.8, cmar = 1.5,  max.cex=.9, halign = "center", valign = "top", row.valign="center",
    #          wrap.rownames=5, wrap.colnames=10, mar = c(0,0,3,0)+0.1)
    # title(main="Largest Drawdowns for HAM1")

