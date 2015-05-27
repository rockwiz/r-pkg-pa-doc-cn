table.CaptureRatios
===================

描述
    计算并显示一个捕获率（capture ratio）和相关统计量的表格（为一组收益相对一个基准创建一张捕获率表和同样的矩阵）。

用法
::

    table.CaptureRatios(Ra, Rb, digits = 4)
    table.UpDownRatios(Ra, Rb, digits = 4)

参数
    :Ra: 一个要检验的收益向量。例如，待查资产
    :Rb: 与要检验资产相比的基准的matrix、data.frame或timeSeries
    :digits: 进行四舍五入的指定位数，用于显示

说明
    该表格显示一项资产相对一组基准的统计量或一组资产相对一个基准的统计量。table.CaptureRatios仅显示捕获率，
    table.UpDownRatios显示三个：捕获率（capture ratio）、数值率（number ratio）和百分比率（percentage ratio）。

另见
    UpDownRatios, chart.CaptureRatios

范例
::

    data(managers)
    table.CaptureRatios(managers[,1:6], managers[,7,drop=FALSE])
    table.UpDownRatios(managers[,1:6], managers[,7,drop=FALSE])

    result = t(table.UpDownRatios(managers[,1:6], managers[,7,drop=FALSE]))
    colnames(result)=colnames(managers[,1:6])
    textplot(result, rmar = 0.8, cmar = 1.5,  max.cex=.9, halign = "center", valign = "top", row.valign="center",
             wrap.rownames=15, wrap.colnames=10, mar = c(0,0,3,0)+0.1)
    title(main="Capture Ratios for EDHEC LS EQ")


