table.Correlation
=================


描述
    一个计算所提供每列数据的相关性和显著性的封装函数，计算多列数据的相关性

用法
::

    table.Correlation(Ra, Rb, ...)

参数
    :Ra: 一个要检验的收益向量。例如，待查资产
    :Rb: 与要检验资产相比的基准的matrix、data.frame或timeSeries
    :...: 任何其它传入cor.test的参数

另见
    cor.test

范例
::

    # First we load the data
    data(managers)
    table.Correlation(managers[,1:6],managers[,7:8])

    result=table.Correlation(managers[,1:6],managers[,8])
    rownames(result)=colnames(managers[,1:6])

    require("Hmisc")

    textplot(format.df(result, na.blank=TRUE, numeric.dollar=FALSE, cdec=rep(3,dim(result)[2])),
             rmar = 0.8, cmar = 1.5,  max.cex=.9, halign = "center", valign = "top", row.valign="center",
             wrap.rownames=20, wrap.colnames=10, mar = c(0,0,3,0)+0.1)
    title(main="Correlations to SP500 TR")
    ctable = table.Correlation(managers[,1:6],managers[,8,drop=FALSE], conf.level=.99)
    dotchart(ctable[,1],labels=rownames(ctable),xlim=c(-1,1))

