chart.Boxplot
=============
描述
    一个创建箱线图的封装函数，携带对比较分布有用的缺省值。

用法
::

    chart.Boxplot(R, horizontal = TRUE, names = TRUE, as.Tufte = FALSE,
                  sort.by = c(NULL, "mean", "median", "variance"), colorset = "black", symbol.color = "red",
                  mean.symbol = 1, median.symbol = "|", outlier.symbol = 1, show.data = NULL,
                  add.mean = TRUE, sort.ascending = FALSE, xlab = "Return",
                  main = "Return Distribution Comparison", element.color = "darkgray", ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :horizontal: TRUE/FALSE，水平标绘（TRUE）或垂直标绘（FALSE）
    :names: 逻辑值。如果为TRUE，则显示每个序列的名字
    :as.Tufte: 逻辑值，缺省为FALSE。如果为TRUE， 使用Tufte 方法限制图表零碎（chart junk）
    :sort.ascending: 逻辑值。如果为TRUE，按sort.by升序对分布进行排序
    :sort.by: "NULL" 、 "mean"、 "median"、 "variance"之一
    :colorset: 调色板，缺省设为合理选择
    :symbol.color: 以指定颜色画出在mean.symbol、median.symbol、outlier.symbol中说明的符号
    :mean.symbol: 分布均值的符号
    :median.symbol: 分布中位数的符号
    :outlier.symbol: 分布异常值的符号
    :show.data: 显示在箱线图顶部的列编号的数值向量，缺省为NULL
    :add.mean: 逻辑值。如果为TRUE，为所有标绘出的分布的均值显示一条直线
    :xlab: 设置x轴标签，同在plot中一样
    :main: 设置标题文本，同在plot中一样
    :element.color: 设定图表元素的颜色，缺省为“darkgray”
    :...: 其它要传入的参数

说明
    我们也提供图表上所有符号和线型的控制。一个由as.Tufte=TRUE设置的缺省状态将去除图表上的零碎，并按照Edward Tufte的建议画出一个箱线图（Boxplot）。

    比较多个序列时，通过利用sort.by和sort.ascending=TRUE对其按“mean”、“median”、“variance”的升序和降序进行排序也很有用。

返回值
    收益箱线图

参考
    Tufte, Edward R. The Visual Display of Quantitative Information. Graphics Press. 1983. p. 124-129

另见
    boxplot

范例
::

    data(edhec)
    chart.Boxplot(edhec)
    chart.Boxplot(edhec,as.Tufte=TRUE)

