AppraisalRatio
==============

描述
    估价比率，也称绩效评估比率，是詹森alpha针对特定风险的调整。分子除以一个特定风险而不是总风险。

用法
::

    AppraisalRatio(Ra, Rb, Rf = 0, method = c("appraisal", "modified", "alternative"), ...)

参数
    :Ra: 一个资产收益的向量、矩阵、数据框、时间序列或zoo、xts对象
    :Rb: 基准资产的收益向量
    :Rf: 和收益同时期的无风险收益率
    :method: 三者之一："appraisal"计算估价比率，"modified"计算修正詹森alpha，"alternative"计算替代詹森alpha
    :...: 其它要传入的参数

细节
    修正詹森Alpha是詹森Alpha除以beta，替代詹森Alpha是詹森Alpha除以系统风险。

.. math::

    Appraisalratio=\frac{\alpha}{\sigma_\epsilon}

    ModifiedJensen's alpha=\frac{\alpha}{\beta}

    AlternativeJensen's alpha=\frac{\alpha}{\sigma_S}

其中，alpha是詹森Alpha， :math:`\sigma_epsilon` 是指定风险， :math:`\sigma_S` 是系统风险

参考
    Carl Bacon, Practical portfolio performance measurement and attribution, second edition 2008 p.77

范例
::

    data(portfolio_bacon)
    print(AppraisalRatio(portfolio_bacon[,1], portfolio_bacon[,2], method="appraisal")) #expected -0.430
    print(AppraisalRatio(portfolio_bacon[,1], portfolio_bacon[,2], method="modified"))
    print(AppraisalRatio(portfolio_bacon[,1], portfolio_bacon[,2], method="alternative"))
    data(managers)
    print(AppraisalRatio(managers[ 1996 ,1], managers[ 1996 ,8]))
    print(AppraisalRatio(managers[ 1996 ,1:5], managers[ 1996 ,8]))

