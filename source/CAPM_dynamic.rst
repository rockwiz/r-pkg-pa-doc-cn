CAPM.dynamic
============

描述
    CAPM是一种认为alpha和beta随时间而变的估计假设。它假设证券的市场价格完全反映可得到的公开信息。
    市场信息变量矩阵Z度量该信息，Z中可能的变量可以是分红收益、国债收益等等。证券和管理组合的beta值允许随市场条件改变。

用法
::

    CAPM.dynamic(Ra, Rb, Rf = 0, Z, lags = 1, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo、xts对象
    :Rb: 基准资产的收益向量
    :Rf: 与收益同时期的无风险收益率
    :Z: 一个反映公开信息的k变量的向量、矩阵、数据框、时间序列或zoo、xts对象
    :lags: alpha和beta条件下当前时期前的滞后数
    :...: 其它要传入的参数

细节
    .. math::

        \beta_p(z_t)=b_{0p}+B^{'}_{p}z_t

    其中， :math:`z_t=Z_t-E[Z]`

    - :math:`Z_t, B_p` 偏差的归一化向量
    -  和 :math:`Z_t` 维度相同的向量

    系数（原文如此，疑为截距。译者注） :math:`b_{0p}` 可被解释为“平均beta”或者所有信息变量处于中位数时的beta。
    :math:`B_p` 部分从它们的中位数测量 :math:`Z_t` 偏差的条件beta。时变（time-varying）条件alpha以同样方式建模如下：

    .. math::

        \alpha_{pt}=\alpha_{p}(z_t)=\alpha_{0p}+A^{'}_{p}z_t

    因此， 修正回归即为：

    .. math::

        \alpha_{pt+1}=\alpha_{0p}+A^{'}_{p}{z_t}+b_{0p}t_{bt+1}+B^{'}_{p}[z_{t}+r_{bt+1}]+\mu_{pt}+1

参考

* J. Christopherson, D. Carino, W. Ferson. Portfolio Performance Measurement and Benchmarking. 2009. McGraw-Hill. Chapter 12.
* Wayne E. Ferson and Rudi Schadt, "Measuring Fund Strategy and Performance in Changing Eco-
* nomic Conditions," Journal of Finance, vol. 51, 1996, pp.425-462

另见
    CAPM.beta

范例
::

    data(managers)
    CAPM.dynamic(managers[,1,drop=FALSE], managers[,8,drop=FALSE],
                 Rf=.035/12, Z=managers[, 9:10])
    CAPM.dynamic(managers[80:120,1:6], managers[80:120,7,drop=FALSE],
                 Rf=managers[80:120,10,drop=FALSE], Z=managers[80:120, 9:10])
    CAPM.dynamic(managers[80:120,1:6], managers[80:120,8:7],
                 managers[80:120,10,drop=FALSE], Z=managers[80:120, 9:10])

