portfolio_bacon
===============

描述
    一个包含组合实例及其基准月度收益列的xts对象

用法
::

    portfolio_bacon

格式
    有月度观测值的符合xts对象的CSV

范例
::

    data(portfolio_bacon)

    #preview the data
    head(portfolio_bacon)

    #summary period statistics
    summary(portfolio_bacon)

    #cumulative returns
    tail(cumprod(1+portfolio_bacon),1)

