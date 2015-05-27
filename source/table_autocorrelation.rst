table.Autocorrelation
=====================

描述
    计算前六个自相关系数和显著性的表格。在R中，为每列生成自相关系数rho和相应Q统计量（Q(6)-statistic）的数据表格。

用法
::

    table.Autocorrelation(R, digits = 4)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :digits: 进行四舍五入的指定位数，用于显示

备注
    要检验自相关，Lo (2001)建议使用Ljung-Box 检验，一种自相关系数的显著性检验。Ljung和Box(1978)
    提供一种Q统计量（由Box和Pierce (1970)提出）的改进，可以较好地针对小样本卡方（ :math:`\chi^2` ）检验进行拟合。 Box.test提供两者。

参考
    Lo, Andrew W. 2001. Risk Management for Hedge Funds: Introduction and Overview. SSRN eLibrary.

另见
    Box.test, acf

范例
::

    data(managers)
    t(table.Autocorrelation(managers))

    result = t(table.Autocorrelation(managers[,1:8]))
    textplot(result, rmar = 0.8, cmar = 2,  max.cex=.9, halign = "center", valign = "top", row.valign="center",
             wrap.rownames=15, wrap.colnames=10, mar = c(0,0,3,0)+0.1)
    title(main="Autocorrelation")


