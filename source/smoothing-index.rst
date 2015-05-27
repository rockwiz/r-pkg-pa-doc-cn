SmoothingIndex
==============

描述
    计算标准化Getmansky平滑指数。

用法
::

    SmoothingIndex(R, neg.thetas = FALSE, MAorder = 2, verbose=FALSE, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :neg.thetas: 如果为FALSE，计算指数时，函数剔除负系数（thetas）,
    :MAorder: 设定用于计算移动平均的期数，缺省为2
    :verbose: 如果为TRUE，返回平滑指数以及一个包含Thetas 的列表
    :...: 其它要传入的参数

说明
    要度量平滑效果，Getmansky, Lo, et al (2004)将“平滑概况”（smoothing profile）定义为一个用两期移动平均过程MLE拟合收益的系数向量。

    在系数之和等于1 的约束下，阶数k=2 （由MAorder设定）的移动平均过程给定。在R中，arima函数允许用“ARIMA(p,d,q)”模型创建一个MA(2)模型，
    其中，p为自回归项(AR)的数值，d为差分阶数，q是在预测方程中的预测误差滞后期数(MA)。order参数允许我们指定三个分量作为一个参数，
    例如，order = c(0, 0, 2)。该方法指定如何拟合模型，这种情况下，用与标准移动平均时间序列的估计相似的最大似然估计（MLE），用::

        arima(ra, order=c(0,0,2), method="ML", transform.pars=TRUE, include.mean=FALSE)

    :include.mean: Getmansky, et al. (2004) p 555 "By applying the above procedure to observed de-meaned returns...",
                   因此，我们将该参数设为FALSE。
    :transform.pars: ibid, "we impose the additional restriction that the estimated MA(k) process be invertible,"
                     因此，我们将该参数设为TRUE。

    系数 :math:`\theta_j` 然后被归一求和，解释为一个“经过包括当前时期在内的最近k+1期，基金真实收益的加权平均”。

    如果这些权重在少量滞后中被不成比例地中心化，可导出系列相关性相对较小。而如果权重在许多滞后中均匀分布，那显示出较高的序列相关。

    论文提到，由于 :math:`\theta_{j}\in[0,1]` ，ξ也限制在单位区间内并且在所有 :math:`\theta_j` 一样时最小化。意味ξ取值为1/(k+1)，
    而当一个系数为1，其它系数为零时，ξ=1。在平滑后收益的场合，较小的ξ值意味更平滑，上边界1说明没有平滑。

    平滑指数（smoothing index）表示为ξ，与Herfindahl指数计算方法一样。Herfindal度量在工业领域作为给定行业公司集中度的度量众所周知。

    该方法（和论文中实现的一样）不强制 :math:`\theta_{j}\in[0,1]` ，所以ξ也不局限在那个范围。我们只能说较低的值说明“较少流动性”，
    而较高的值说明“较多流动性”。该函数设定参数neg.thetas=FALSE不强制界限，从计算中消除负的自相关系数（然而，
    以下论文没有从经济的角度列出消除负自相关的理由）。

    很难解释由此产生的值。我们只能说较小的值似乎有自相关结构，就像我们希望的“较少流动性”的证券；较高的值显现出“较多流动性”或拟合不够或不当设定。

参考

1.Chan, Nicholas, Mila Getmansky, Shane M. Haas, and Andrew W. Lo. 2005. Systemic Risk and Hedge Funds. NBER Working Paper Series (11200).
2.Getmansky, Mila, Andrew W. Lo, and Igor Makarov. 2004. An Econometric Model of Serial Correlation and Illiquidity in Hedge Fund Returns. Journal of Financial Economics (74): 529-609.

范例
::

    data(managers)
    data(edhec)
    SmoothingIndex(managers[,1,drop=FALSE])
    SmoothingIndex(managers[,1:8])
    SmoothingIndex(edhec)

