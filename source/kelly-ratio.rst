KellyRatio
==========
描述
    一个策略的计算凯利准则比率（杠杆或下注规模）。

用法
    KellyRatio(R, Rf = 0, method="half")

参数
    :R: 要求其均值的收益向量
    :Rf: 与收益同时期的无风险收益率
    :method: method=half将使用半凯（half-Kelly），此为缺省

说明
    凯利准则（Kelly criterion ）由贝尔实验室科学家提出，被Ed Thorpe 运用到扑克牌的二十一点游戏和股票策略上。

    Kelly比率可以简单地表述为：“下注大小为获利与赔率之比（bet size is the ratio of edge over odds.）”。数学上，你要最大化对数效应。
    因此，凯利准则等于策略的期望超额收益除以超额收益的期望方差，或

    .. math::

        leverage=\frac{(\overline{R}-R)}{StdDev{(R)}^2}

    作为绩效矩阵，Kelly比率是对特定投资追溯性计算，作为投资相对于无风险收益率的收益的度量。它可用来作为以与夏普比率有关的各种比率的相同方式来
    比较投资的洗牌分级方法。

参考
    1. Thorp, Edward O. (1997; revised 1998). The Kelly Criterion in Blackjack, Sports Betting, and the Stock Market. http://www.bjmath.com/bjmath/thorp/paper.htm
    2. http://en.wikipedia.org/wiki/Kelly_criterion

范例
::

    data(managers)
    KellyRatio(managers[,1,drop=FALSE], Rf=.04/12)
    KellyRatio(managers[,1,drop=FALSE], Rf=managers[,10,drop=FALSE])
    KellyRatio(managers[,1:6], Rf=managers[,10,drop=FALSE])


