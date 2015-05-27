SortinoRatio
============

描述
    计算绩效于下方风险的Sortino比率。Sortino在夏普比率基础上提出一项改进，通过仅使用下方（downside）半方差作为风险度量来考虑技能和超额绩效。

用法
::

    SortinoRatio(R, MAR = 0)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :MAR: 最小可接受收益，与收益的周期性相同

说明
    Sortino主张风险应该根据没有达到投资目标来度量。这产生了“最小可接受收益”（Minimum Acceptable Return，MAR）的概念。
    所有Sortino提出的度量，包括MAR，对下方风险或极端风险的度量都比使用波动性（收益的标准差）更敏感。

    谨慎地选择MAR非常重要，尤其在比较完全不同的投资选择时。如果MAR过低，它不会恰当地捕捉到使投资者忧虑的风险；而如果MAR过高，它会
    不适宜地描绘那些安全可靠的投资。当比较多项投资时，一些论文建议使用无风险收益率作为MAR。实践工作者也许希望为一致性选择一个MAR，
    为一系列方案选择几个标准化的MAR，为投资者客户化定制的一个MAR。

    .. math::

        SortinoRatio=\frac{\overline{(R_\alpha-MAR)}}{\delta_{MAR}}

    其中，:math:`\delta_{MAR}` 是DownsideDeviation

参考
    Sortino, F. and Price, L. Performance Measurement in a Downside Risk Framework. Journal of Investing. Fall 1994, 59-65.

另见
    SharpeRatio DownsideDeviation SemiVariance SemiDeviation InformationRatio

范例
::

    data(managers)
    round(SortinoRatio(managers[, 1]),4)
    round(SortinoRatio(managers[, 1:8]),4)

