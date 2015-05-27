Return.calculate
================

描述
    根据价格计算简单或复合收益

用法
::

    Return.calculate(prices, method=c("compound","simple"))
    CalculateReturns(prices, method=c("compound","simple"))

参数
    :prices: 包含排序后价格观测值的数据对象
    :method: 计算“simple”（简单）或“compound”（复合）收益，缺省为“复合”

说明
    应弄清楚两个必要条件。实现函数Return.calculate假设规则价格数据。这种情况下，我们下载了月度收盘价。价格可以为任意时间刻度，
    例如每日、每周、每月或每年，只要数据由规则观测值组成。非规则观测值需要缩放到（scaling）可比较的时期。幸运的是，
    xts包中的to.period或zoo包中的aggregate.zoo支持非规则时间序列的管理和转换。

    其次，如果要考虑公司举动（action）、分红或其它调整如时间或资金加权，这些计算必须单独进行。这是一个简单的函数，
    它假定所有输入为分调整过收盘价。以下例子中的IBM时间序列，分红与公司举动没有包含在“收盘价”序列中，因此我们以“价格收益”代替“总收益”结束。
    这会导致严重低估经过长时期的收益序列。要使用调整后收益，在get.hist.quote中指定quote="AdjClose"，它可在tseries包中找到。

参考
    Bacon, C. Practical Portfolio Performance Measurement and Attribution. Wiley. 2004. Chapter 2

另见
    Return.cumulative

范例
::

    ## Not run:
        require(tseries)
        prices = get.hist.quote("IBM", start = "1999-01-01", end = "2007-01-01", quote = "AdjClose", compression = "d")

    ## End(Not run)

    R.IBM = Return.calculate(prices, method="simple")
    R.IBM = as.xts(R.IBM)
    colnames(R.IBM)="IBM"
    chart.CumReturns(R.IBM,legend.loc="topleft", main="Cumulative Daily Returns for IBM")
    round(R.IBM,2)

