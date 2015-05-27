table.CalendarReturns
=====================


描述
    月度和日历年收益表。返回一个年度为行、月度为列并且最后一列为总和的收益表格。对R中的补充列，年收益将作为列追加。

用法
::

    table.CalendarReturns(R, digits = 1, as.perc = TRUE, geometric = TRUE)
    table.Returns(R, digits = 1, as.perc = TRUE, geometric = TRUE)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :digits: 进行四舍五入的指定位数，用于显示
    :as.perc: TRUE/FALSE。如果为TRUE，将简单收益乘以100，获得百分数（% ）
    :geometric: 生成几何（TRUE）或简单（FALSE）收益，缺省为TRUE

备注
* 该函数假设月收益，目前不能其它刻度。
* 该函数缺省将第一列作为要格式化的月收益。

范例
::

    data(managers)
    t(table.CalendarReturns(managers[,c(1,7,8)]))

    # prettify with format.df in hmisc package
    require("Hmisc")
    result = t(table.CalendarReturns(managers[,c(1,8)]))
    textplot(format.df(result, na.blank=TRUE, numeric.dollar=FALSE, cdec=rep(1,dim(result)[2])),
             rmar = 0.8, cmar = 1,  max.cex=.9, halign = "center", valign = "top", row.valign="center",
             wrap.rownames=20, wrap.colnames=10, col.rownames=c( rep("darkgray",12), "black", "blue"), mar = c(0,0,3,0)+0.1)
    title(main="Calendar Returns")

