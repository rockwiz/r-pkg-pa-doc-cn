chart.CaptureRatios
===================

描述
    相对基准，上升捕捉相比下降捕捉的散点图。

用法
::

    chart.CaptureRatios(Ra, Rb, main = "Capture Ratio", add.names = TRUE,
                        xlab = "Downside Capture", ylab = "Upside Capture", colorset = 1, symbolset = 1,
                        legend.loc = NULL, xlim = NULL, ylim = NULL, cex.legend = 1, cex.axis = 0.8, cex.main = 1,
                        cex.lab = 1, element.color = "darkgray", benchmark.color = "darkgray", ...)

参数
    :Ra: 待检验的收益，例如要考察的资产
    :Rb: 与资产进行比较的基准的收益
    :main: 设置图表标题，同在plot中一样
    :add.names: 用数据点标绘行名字，缺省为TRUE。可通过将其设为NULL清除
    :xlab: 设置x轴标签，同在plot中一样
    :ylab: 设置y轴标签，同在plot中一样
    :colorset: 调色板，缺省设为“black”
    :symbolset: 提交的数据集
    :legend.loc: 把图例放置在图表上9个位置之一：bottomright、bottom、bottomleft、left、topleft、top、topright、right或center
    :xlim: 设置x轴界限，同在plot中一样
    :ylim: 设置y轴界限，同在plot中一样
    :cex.axis: 轴标注相对当前“cex”设置的放大倍率，同在plot中一样
    :cex.legend: 图例大小相对当前“cex”设置的放大倍率
    :cex.main: 标题大小相对当前“cex”设置的放大倍率
    :cex.lab: x和y轴标签相对当前“cex”设置的放大倍率
    :element.color: 设定箱体、轴和其它图表元素的颜色，缺省为“darkgray”
    :benchmark.color: 设定基准参考和十字线的颜色，缺省为“darkgray”
    :...: 任何其它传入plot的参数

说明
    散点图显示每组收益相对基准上升和下降捕捉的坐标。基准值根据定义用连续十字线画在(1,1) 处。一个斜率为1的虚线将绘图分为两个区域：
    在那条线之上，UpCapture超过DownCapture；反之亦然。

另见
    plot par UpDownRatios table.UpDownRatios

范例
::

    data(managers)
    chart.CaptureRatios(managers[,1:6], managers[,7,drop=FALSE])

