SharpeRatio.annualized
======================

描述
    计算年化夏普比率。夏普比率是用标准差表示风险的收益风险调整度量。

用法
::

    SharpeRatio.annualized(R, Rf = 0, scale = NA, geometric=TRUE)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :Rf: 与收益同时期的无风险收益率
    :scale: 一年的期数（日刻度=252，月刻度=12，季刻度=4）
    :geometric: 生成几何（TRUE）或简单（FALSE）收益，缺省为TRUE

说明
    夏普比率（Sharpe ratio）仅仅是每个风险单位（表示为波动性）的收益。夏普比率越高，“风险”和收益的连结绩效越好。

    该函数年化基于scale 参数的数字。

    .. math::

        \frac{\sqrt{prod{(1+R_\alpha)}^{scale}}-1}{\sqrt{scale}\centerdot\sqrt{\sigma}}

    使用年化夏普比率有助于多个收益流的比较。年化夏普比率通过将月度超额收益的年化均值除以年化的月度超额收益标准差计算而来。

    William Sharpe现在建议InformationRatio的使用优先于原始的夏普比率。

参考
    Sharpe, W.F. The Sharpe Ratio,Journal of Portfolio Management,Fall 1994, 49-58.

另见
    SharpeRatio InformationRatio TrackingError ActivePremium SortinoRatio

范例
::

    data(managers)
    SharpeRatio.annualized(managers[,1,drop=FALSE], Rf=.035/12)
    SharpeRatio.annualized(managers[,1,drop=FALSE], Rf = managers[,10,drop=FALSE])
    SharpeRatio.annualized(managers[,1:6], Rf=.035/12)
    SharpeRatio.annualized(managers[,1:6], Rf = managers[,10,drop=FALSE])
    SharpeRatio.annualized(managers[,1:6], Rf = managers[,10,drop=FALSE],geometric=FALSE)


