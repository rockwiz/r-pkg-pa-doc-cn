chart.ACF
=========

描述
    创建一个ACF图，或设为某指定缺省选项的ACF和PACF两面板图。

用法
::

    chart.ACF(R, maxlag = NULL, elementcolor = "gray", main = NULL, ...)
    chart.ACFplus(R, maxlag = NULL, elementcolor = "gray", main = NULL, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :maxlag: 要计算的滞后数，可选
    :elementcolor: 图表元素颜色，缺省为"gray"
    :main: 标绘图（plot）标题，缺省用列名
    :...: 其它要传入的参数

备注
    受网站http://www.stat.pitt.edu/stoffer/tsa2/Rcode/acf2启发。

    R“...此处是一个以相同时间刻度绘制一个时间序列在相同时刻的ACF和PACF图的R函数，它忽略ACF中的零滞后：acf2.R。
    如果时间序列在x中，而要x的ACF和PACF滞后50，函数的调用为acf2(x,50)。 滞后数是可选的，因此acf2(x)将用lags[sqrt(n) + 10],
    其中n是观测值的数量的缺省值”

    该描述非常有意义，因此在这里单独的ACF和带PACF的ACF都实现了。

另见
    plot

范例
::

    data(edhec)
    chart.ACFplus(edhec[,1,drop=FALSE])

