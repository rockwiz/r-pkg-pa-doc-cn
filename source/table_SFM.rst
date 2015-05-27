table.SFM
=========

描述
    取一组收益并将其与基准收益关联起来。提供一组超额收益单因子模型或CAPM相关的测度

用法
::

    table.SFM(Ra, Rb, scale = NA, Rf = 0, digits = 4)

参数
    :Ra: 待检验收益的向量
    :Rb: 基准资产的收益矩阵、数据框或时间序列
    :scale: 一年的期数（日刻度=252，月刻度=12，季刻度=4）
    :Rf: 与收益同时期的无风险收益率
    :digits: 进行四舍五入的指定位数

说明
    该表显示一个或一组资产相对于基准的统计信息

另见
    CAPM.alpha CAPM.beta TrackingError ActivePremium InformationRatio TreynorRatio

范例
::

    data(managers)
    table.SFM(managers[,1:3], managers[,8], Rf = managers[,10])

    result = table.SFM(managers[,1:3], managers[,8], Rf = managers[,10])

    textplot(result, rmar = 0.8, cmar = 1.5, max.cex=.9, halign = "center", valign = "top", row.valign="center",
             wrap.rownames=15, wrap.colnames=10, mar = c(0,0,3,0)+0.1)

    title(main="Single Factor Model Related Statistics")

