table.CAPM
==========

描述
    资产定价模型概要：统计和样式化事实。取一组收益将它们与市场基准联系起来。提供一系列与超额收益单指数模型或CAPM有关的度量。

用法
::

    table.CAPM(Ra, Rb, scale = NA, Rf = 0, digits = 4)

参数
    :Ra: 一个要检验的收益向量。例如，待查资产
    :Rb: 与要检验资产相比的基准的matrix、data.frame或timeSeries
    :scale: 一年的期数（日刻度=252，月刻度=12，季刻度=4）
    :Rf: 与收益同时期的无风险收益率
    :digits: 进行四舍五入的指定位数

说明
    该表格显示一项资产相对一组基准的统计量或一组资产相对一个基准的统计量。

另见
    CAPM.alpha CAPM.beta TrackingError ActivePremium InformationRatio TreynorRatio

范例
::

    data(managers)
    table.CAPM(managers[,1:3,drop=FALSE], managers[,8,drop=FALSE], Rf = managers[,10,drop=FALSE])

    result = table.CAPM(managers[,1:3,drop=FALSE], managers[,8,drop=FALSE], Rf = managers[,10,drop=FALSE])
    textplot(result, rmar = 0.8, cmar = 1.5,  max.cex=.9, halign = "center", valign = "top", row.valign="center",
             wrap.rownames=15, wrap.colnames=10, mar = c(0,0,3,0)+0.1)
    title(main="CAPM-Related Statistics")


