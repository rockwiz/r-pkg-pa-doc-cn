Omega
=====

描述
    计算一个收益序列的Omega。Keating和 Shadwick (2002)提出用Omega（在他们的原始论文中引用为Gamma）作为一种捕获收益分布高阶矩的方法

用法
::

    Omega(R, L = 0, method = c("simple", "interp", "binomial", "blackscholes"),
          output = c("point", "full"), Rf = 0, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :L: L是一个损失阈值，能被设定为零、基准指数收益或绝对收益率-任何指定水平
    :method: simple、interp、binomial、 blackscholes之一
    :output: point （in time）或 full （distribution of Omega） 之一
    :Rf: 无风险收益率，与收益期间相同
    :...: 其它要传入的参数

说明
    数学上，Omega为

    .. math::

        \frac{\int_{L}^b{(1-F(r))dr}}{\int_a^{L}F(r)dr}

    其中，累积分布F定义在(a,b)区间。L是一个可设定为零、基准指数收益或者绝对收益率等任何指定水平的损失阈值。当用Omega来比较可替代性时，
    L应该比较常用。

    输入数据在计算前可被转换，它有助于引入风险排斥。

    该函数返回一个对绘图有用的Omega向量，越陡峭，风险性越小。在它的均值之上，一个陡峭斜率的Omega也暗示未来获利潜力非常有限。

    Omega在分布均值处的值为1。

    Omega是次加性的（sub-additive），其比率无量纲。

    Kazemi、 Schneeweis和Gupta (2003), 在"Omega as a Performance Measure" 中指出Omega 可以写成：Omega(L) = C(L)/P(L)，
    其中C(L)本质上是写在投资上的欧洲认购期权，而P(L) 本质上是写在投资上的欧洲认售期权。两者期权的到期是同一时期（例如，1个月），
    而L是两种期权的敲定价格。

    分子和分母可以表达为exp(-Rf=0) * E[max(x - L, 0)]、exp(-Rf=0) * E[max(L - x, 0)]，exp(-Rf=0)计算两者的现值。
    其中 :math:`r_f` 是每期（per-period）无风险收益率。

    此处实现的前三个方法专注于观测值。第一种方法取以上描述的简单性，第二种用Black-Scholes期权定价作为fOptions中的实现，
    第三种fOptions中的二项式定价模型。第二和第三种方法这里没有实现。

    第四种方法，“interp”，创建一个收益cdf（累积密度函数）的线性插值，将Omega作为向量计算，最终将Omeg 函数作为L的函数插入
    。该方法需要库Hmisc，它可在CRAN中找到。

参考
    Keating, J. and Shadwick, W.F. The Omega Function. working paper. Finance Development Center, London. 2002. Kazemi, Schneeweis, and Gupta. Omega as a Performance Measure. 2003.

另见
    Ecdf

范例
::

    data(edhec)
    Omega(edhec)
    Omega(edhec[,13],method="interp",output="point")
    Omega(edhec[,13],method="interp",output="full")

