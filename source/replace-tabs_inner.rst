replaceTabs.inner
=================

描述
    该函数在一个图形窗口显示文本输出。等同于 ``print`` 函数，除了输出是以绘图方式显示

用法
::

    replaceTabs.inner(text, width = 8)

    replaceTabs(text, width = 8)

    textplot(object, halign = "center", valign = "center", cex, max.cex = 1,
             cmar = 2, rmar = 0.5, show.rownames = TRUE, show.colnames = TRUE,
             hadj = 1, vadj = NULL, row.valign = "center",
             heading.valign = "bottom", mar = c(0, 0, 0, 0) + 0.1,
             col.data = par("col"), col.rownames = par("col"),
             col.colnames = par("col"), wrap = TRUE, wrap.colnames = 10,
             wrap.rownames = 10, ...)

    ## Default S3 method:
    textplot(object, halign = c("center", "left", "right"),
             valign = c("center", "top", "bottom"), cex, max.cex, cmar, rmar,
             show.rownames, show.colnames, hadj, vadj, row.valign, heading.valign, mar,
             col.data, col.rownames, col.colnames, wrap, wrap.colnames, wrap.rownames, ...)

    ## S3 method for class data.frame
    textplot(object, halign = c("center", "left", "right"),
             valign = c("center", "top", "bottom"), cex, max.cex = 1, cmar = 2,
             rmar = 0.5, show.rownames = TRUE, show.colnames = TRUE, hadj = 1,
             vadj = NULL, row.valign = "center", heading.valign = "bottom",
             mar = c(0, 0, 0, 0) + 0.1, col.data = par("col"),
             col.rownames = par("col"), col.colnames = par("col"), wrap = TRUE,
             wrap.colnames = 10, wrap.rownames = 10, ...)

    ## S3 method for class matrix
    textplot(object, halign = c("center", "left", "right"),
             valign = c("center", "top", "bottom"), cex, max.cex = 1, cmar = 2,
             rmar = 0.5, show.rownames = TRUE, show.colnames = TRUE, hadj = 1,
             vadj = NULL, row.valign = "center", heading.valign = "bottom",
             mar = c(0, 0, 0, 0) + 0.1, col.data = par("col"),
             col.rownames = par("col"), col.colnames = par("col"), wrap = TRUE,
             wrap.colnames = 10, wrap.rownames = 10, ...)

    ## S3 method for class character
    textplot(object, halign = c("center", "left", "right"),
             valign = c("center", "top", "bottom"), cex, max.cex = 1, cmar = 2,
             rmar = 0.5, show.rownames = TRUE, show.colnames = TRUE, hadj = 1,
             vadj = NULL, row.valign = "center", heading.valign = "bottom",
             mar = c(0, 0, 3, 0) + 0.1, col.data = par("col"),
             col.rownames = par("col"), col.colnames = par("col"), wrap = TRUE,
             wrap.colnames = 10, wrap.rownames = 10, fixed.width = TRUE,
             cspace = 1, lspace = 1, tab.width = 8, ...)

参数
    :text: 函数replaceTabs中, 要处理的文本字符串
    :width: 函数replaceTabs中, 要替换的空格数
    :object: 要显示的对象
    :halign: x方向对齐，"center"、"left"或"right"
    :valign: x方向对齐，"center"、"top"或"bottom"
    :cex: 字符大小，细节参见par。如果未设置，将用能够显示所有对象的最大值
    :max.cex: 设置文本大小的最大值
    :rmar,cmar: 行列间的空格，以字母“M”大小为最小单位
    :show.rownames,show.colnames: 行名字或列名字是否显示的罗辑值
    :hadj,vadj: 矩阵单元中元素的垂直和水平位置。和adj图形参数意义一样（参见par）
    :row.valign: 将行的垂直对齐设置为"top"、"bottom"或者（缺省）"center".
    :heading.valign: 将页面标题设为"top"、（缺省）"bottom"或"center".
    :mar: 图形边缘，参见par文档
    :col.data: 数据元素颜色。如果只提供一个值，则所有元素使用相同颜色。如果提供和数据维度匹配的矩阵，则每个数据元素都得到指定颜色
    :col.rownames,col.colnames: 列名和行名的颜色。可被指定为合适长度的标量或向量
    :wrap: 如果为TRUE（缺省），将列名字和行名字换行
    :wrap.colnames: 之后列标签换行的字符数。缺省为10
    :wrap.rownames: 之后行的标题换行的字符数。缺省为10
    :fixed.width: 缺省为TRUE
    :cspace: 缺省为1
    :lspace: 缺省为1
    :tab.width: 缺省为8
    :...: 传递给文本绘制命令或专门对象方法的可选参数

说明
    创建一个新图，对象用匹配绘图区域的最大字符显示。对矩阵和向量而言，有一个专门单独绘制每个单元的textplot函数可用，
    其列宽按列元素的大小设置。如果行和列存在的化，以粗体字显示。
    textplot也使用replaceTabs函数，该函数将字符串中所有tab替换成合适数量的空格，包含在gplots包中。

另见
    plot, text, capture.output, textplot

范例
::

    # Also see the examples in the original gplots textplot function
    data(managers)
    textplot(table.AnnualizedReturns(managers[,1:6]))

    # This was really nice before Hmisc messed up format from R-base
    # prettify with format.df in hmisc package
    # require("Hmisc")
    # result = t(table.CalendarReturns(managers[,1:8]))[-1:-12,]
    # textplot(Hmisc::format.df(result, na.blank=TRUE, numeric.dollar=FALSE,
    # cdec=rep(1,dim(result)[2])), rmar = 0.8, cmar = 1, max.cex=.9,
    # halign = "center", valign = "top", row.valign="center", wrap.rownames=20,
    # wrap.colnames=10, col.rownames=c("red", rep("darkgray",5),
    # rep("orange",2)), mar = c(0,0,4,0)+0.1)
    #
    # title(main="Calendar Returns")
