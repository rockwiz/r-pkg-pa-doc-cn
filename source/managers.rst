managers
========

描述
    假想的另类资产经理和基准。一个包含以下列的xts对象：6个假想的资产经理（从HAM1到HAM6）的月度收益、EDHEC多头-空头证券对冲基金指数、
    S&P500总收益和美国10年期国债与3月期票据的总收益序列。所有序列月度收益始于1996年开始的不同时期，止于2006年12月。
    注意，所有EDHEC指数在edhec中都可获得。

用法
::

    managers

格式
    CSV，符合有月度观测值的xts对象

说明
    请注意，PerformanceAnalytics 中的“managers”数据集将用新的managers和信息定期更新。如果想要将该数据集用于自动测试，
    请确保从数据中抽取子集，例如用managers[1:120,1:6]来使用HAM1-HAM6头十年的观测值。

范例
::

    data(managers)

    #preview the data
    head(managers)

    #summary period statistics
    summary(managers)

    #cumulative returns
    tail(cumprod(1+managers),1)

