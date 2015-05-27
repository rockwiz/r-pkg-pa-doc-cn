DrawdownDeviation
=================

描述
    .. math::

        DD=\sqrt{\Sigma_{j=1,2...,d}{D_j}^{2/n}}

    其中， :math:`D_j` 是整个期间的第j个回撤，d是整个期间的所有回撤，n是观测样本数

用法
::

    DrawdownDeviation(R, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :...: 其它要传入的参数
