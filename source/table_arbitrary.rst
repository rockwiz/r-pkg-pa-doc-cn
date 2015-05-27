table.Arbitrary
===============

描述
    该函数从传入的函数与标签向量创建一个表格。由此产生的表格其格式为：为数据对象中的每列收益单独计算的矩阵。

    假设输入一个期间收益。Scale参数用来设定1年内的观测数（例如，12=月度收益）。

用法
::

    table.Arbitrary(R, metrics = c("mean", "sd"), metricsNames = c("Average Return", "Standard Deviation"), ...)
    statsTable(R, metrics = c("mean", "sd"), metricsNames = c("Average Return", "Standard Deviation"), ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :metrics: 应用的函数列表
    :metricsNames: 每个函数的列名字
    :...: 其它要传入的参数

说明
    此处的想法是能够传入一组矩阵和值，如::

        metrics = c(DownsideDeviation(x,MAR=mean(x)), sd(subset(x,x>0)), sd(subset(x,x<0)),
                    DownsideDeviation(x,MAR=MAR), DownsideDeviation(x,MAR=Rf=0), DownsideDeviation(x,MAR=0),maxDrawdown(x))

        metricsNames = c("Semi Deviation", "Gain Deviation", "Loss Deviation",
                         paste("Downside Deviation (MAR=",MAR*scale*100,"%)", sep=""),
                         paste("Downside Deviation (rf=",rf*scale*100,"%)", sep=""),
                         paste("Downside Deviation (0%)", sep=""),
                         "Maximum Drawdown" )

现在，它如何工作？
::

    > table.Arbitrary(monthlyReturns.ts,metrics=c("VaR","mean"), metricsNames=c("modVaR","mean"),p=.95)

======= =========== ===========
\          Actual   S&P500TR
======= =========== ===========
modVaR  0.04186461  0.06261451
mean    0.00945000  0.01013684
======= =========== ===========

    给相同函数传入两组不同属性现在还不行。问题出现在::

    > table.Arbitrary(edhec,metrics=c("VaR", "VaR"), metricsNames=c("Modified VaR","Traditional VaR"), modified=c(TRUE,FALSE))

================ ====================== =================== =======================
\                Convertible.Arbitrage  CTA.Global          Distressed.Securities
================ ====================== =================== =======================
Modified VaR     0.04081599             0.0456767           0.1074683
Traditional VaR  0.04081599             0.0456767           0.1074683
================ ====================== =================== =======================

================ ================= ======================== =======================
\                Emerging.Markets  Equity.Market.Neutral    Event.Driven
================ ================= ======================== =======================
Modified VaR     0.1858624         0.01680917               0.1162714
Traditional VaR  0.1858624         0.01680917               0.1162714
================ ================= ======================== =======================

================ ====================== =================== =======================
\                Fixed.Income.Arbitrage Global.Macro        Long.Short.Equity
================ ====================== =================== =======================
Modified VaR     0.2380379              0.03700478          0.04661244
Traditional VaR  0.2380379              0.03700478          0.04661244
================ ====================== =================== =======================

================ ================= =============== ============= ===================
\                Merger.Arbitrage  Relative.Value  Short.Selling Funds.of.Funds
================ ================= =============== ============= ===================
Modified VaR     0.07510643        0.04123920      0.1071894     0.04525633
Traditional VaR  0.07510643        0.04123920      0.1071894     0.04525633
================ ================= =============== ============= ===================

范例中情况下，应该仅仅将VaR作为第二个函数调用，像这样::

    > table.Arbitrary(edhec,metrics=c("VaR", "VaR"),metricsNames=c("Modified VaR","Traditional VaR"))

================ ====================== =================== =======================
\                Convertible.Arbitrage  CTA.Global          Distressed.Securities
================ ====================== =================== =======================
Modified VaR     0.04081599             0.04567670          0.10746831
Traditional VaR  0.02635371             0.04913361          0.03517855
================ ====================== =================== =======================

================ ================= ======================== =======================
\                Emerging.Markets  Equity.Market.Neutral    Event.Driven
================ ================= ======================== =======================
Modified VaR     0.18586240        0.01680917               0.11627142
Traditional VaR  0.07057278        0.01746554               0.03563019
================ ================= ======================== =======================

================ ====================== =================== =======================
\                Fixed.Income.Arbitrage Global.Macro        Long.Short.Equity
================ ====================== =================== =======================
Modified VaR     0.23803787             0.03700478          0.04661244
Traditional VaR  0.02231236             0.03692096          0.04318713
================ ====================== =================== =======================

================ ================= =============== ============= ==================
\                Merger.Arbitrage  Relative.Value  Short.Selling Funds.of.Funds
================ ================= =============== ============= ==================
Modified VaR     0.07510643        0.04123920      0.1071894     0.04525633
Traditional VaR  0.02510709        0.02354012      0.0994635     0.03502065
================ ================= =============== ============= ==================

但是我们不知道以不同参数比较相同函数的方法。欢迎建议。

范例
::

    data(edhec)
    table.Arbitrary(edhec,metrics=c("VaR", "ES"),metricsNames=c("Modified VaR","Modified Expected Shortfall"))


