ETL
===

描述
    用各种分析方法计算单变量或成分期望差损（或条件在险价值）

用法
::

    ETL(R = NULL, p = 0.95, ..., method = c("modified", "gaussian","historical"), clean = c("none", "boudt", "geltner"),
        portfolio_method = c("single", "component"), weights = NULL, mu = NULL,
        sigma = NULL, m3 = NULL, m4 = NULL, invert = TRUE,
        operational = TRUE)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo、xts对象
    :p: 用于计算的置信水平，缺省p=.95
    :method: “modified”、“gaussian”、“historical”、“kernel”之一，参见说明部分
    :clean: 经由Return.clean的数据清洗方法。目前选项为“none”、“boudt”或“geltner”
    :portfolio_method: “single”、“component”、“marginal”之一，定义是做单变量、成分还是边际计算，参见说明部分
    :weights: 组合权重向量，缺省为NULL，参见说明部分
    :mu: 如果为单变量，mu是序列均值。否则，mu是收益序列均值向量，缺省为NULL，参见说明部分
    :sigma: 如果为单变量，sigma 是序列方差。否则，sigma是收益序列协方差矩阵，缺省为NULL，参见说明部分
    :m3: 如果为单变量，m3是序列偏度。否则，m3是收益序列协偏度矩阵，缺省为NULL，参见说明部分
    :m4: 如果为单变量，m4是序列超量峰度。否则，m4是收益序列协峰度矩阵，缺省为NULL，参见说明部分
    :invert: TRUE/FALSE，是否反转VaR度量。参见说明部分
    :operational: TRUE/FALSE，缺省为TRUE。参见说明部分
    :...: 其它要传入的参数

说明
    **背景**

    该函数提供若干估算收益序列期望差损（Expected Shortfall，ES。也称条件在险价值，Conditional Value at Risk，CVaR）和
    一个投资组合成分ES（Component ES）的方法。在一个预先设定的概率水平上，指定c，它典型地处于1%~5%之间，当收益小于它的c-分位数时，
    收益序列的ES是期望收益的负值。不像在险价值，条件在险价值有风险度量应该连贯一致的所有属性，并且是组合权重的凸性函数（Pflug, 2000）。
    对足够大的数据集，可以选择用c经验分位数以下的所有收益的样本平均来估算ES。如果作出了收益分布的（正确）假设，如正态分布，
    可以获得更高效的VaR估计。如果收益序列是有偏度的，并且/或者有过量峰度，ES的Cornish-Fisher估计可能更合适。对投资组合的ES，
    将总的组合ES分解为每个组合成分的风险贡献，也很有趣；对上述ES估计量，这样的分解在金融意义上是可能的。

    **一元收益序列的ES估计**

    在一个概率水平p（如95%）上的ES是当收益小于它的c=1-p分位数时，收益期望值的负值。在一组存在足够长历史的收益中，
    每期（per-period）ES可通过低于分位数的所有收益的样本平均的负值估算，该方法有时也称为“历史ES”（historical ES），
    因为它是根据收益分布的事后（ex post）分析，并可通过设置method="historical"来存取。

    当没有用于非参或历史ES的足够长的收益，或者希望建立一个更接近理想分布的模型，通常用基于分布的参数估计。
    通过更精确地估计风险分位数分布的尾部形状，参数ES在刻画分布尾部方面做得更好。最常用的估计是收益序列的正态（或高斯）分布 :math:`R\sim{N(\mu, \sigma)}` 。
    这种情况下，ES估计需要均值收益 :math:`\overline{R}` ，收益分布和分布方差σ。最常见情况下，参数ES计算如下：

    .. math::

        \sigma=variance(R)\\

        ES=-\overline{R}+\sqrt{\sigma}\frac{1}{c}\cdot\phi{(Z_c)}

    其中 :math:`z_c` 是标准正态分布的c-分位数。在R中以qnorm(c)表示，并可通过设置method="gaussian"存取。函数dnorm是高斯密度函数。

    高斯ES的局限在许多文献中都有提及，因为大多数收益序列是非正态的。Boudt、 Peterson和Croux (2008)利用Cornish-Fisher扩展考虑进
    非正态分布（偏度和峰度）的高阶矩，提供一种改进ES（modified ES）计算，而如果收益流服从标准分布，则退化为标准（传统的）高斯ES。
    更精确地，对损失概率c，改进ES定义为低于c- Cornish-Fisher分位数的所有收益的期望值的负数，
    其中期望值在真实分布的二阶Edgeworth扩展下计算。

    改进期望差损应该总是高于改进在险价值。由于估计的问题，情况也许并不总是如此。设置Operational=TRUE，在改进ES小于改进VaR的异常情况下，
    用改进VaR替换改进ES。

    **成分ES（Component ES）**

    通过设置portfolio_method="component" ，可以计算投资组合中每个元素的ES贡献。这种情况下，函数的返回值将是一个带三个分量的列表：
    单变量组合ES，每个成分相对组合ES的标量贡献（它们的总和为组合ES），百分比风险贡献（它们总和为100%）。

    对ES的数值型和百分比贡献都可以为正和为负。对成分ES的负贡献表明是一个组合的风险分散者。提高该头寸的权重将减少总的组合ES。

    如果没有通过weights传递一个加权向量，函数将假设一个等权重（中性）投资组合。

    文献中提出多个风险分解方式。一个“质朴”（naive）方式是将风险贡献设为等同于它们的孤立（stand-alone）风险。这种方式过度简单，
    忽略了对相关风险因子有不同影响的单元的重要分散效应。一个替代方式是用头寸在组合中的权重乘以组合ES关于成分权重的偏导数来度量ES贡献。

    .. math::

        C_i{ES}=\mathit{w}_i{\frac{\partial{ES}}{\partial{\mathit{w}_i}}}

    由于组合ES与组合的规模成线性关系，根据Euler 定理，组合VaR是这些风险贡献之和。Scaillet (2002) 显示了对ES，
    组合风险的数学分解具有金融含义。当投资组合的收益小于或等于负的组合VaR时，它等于资产相对组合收益期望贡献的负值：

    .. math::

        C_t{ES}=-E[\mathit{w}_i\mathit{r}_i|\mathit{r}_p\leq{-VaR}]

    对高斯ES的分解，需要估计的均值和协方差矩阵。对改进ES的分解，也需要估计协偏度和协峰度矩阵。如果r为Nx1维收益向量，μ为均值向量，
    那么 :math:`N\times{N^2}` 协偏度矩阵是：

    .. math::

        m3=E[(r-\mu){(r-\mu)}^{'}\otimes{(r-\mu)}^{'}]

    :math:`N\times{N^2}` 协峰度是：

    .. math::

        m4=E[(r-\mu){(r-\mu)}^{'}\otimes{(r-\mu)}^{'}\otimes{(r-\mu)}^{'}]

    其中，:math:`\otimes` 代表Kronecker积。该矩阵可通过函数skewness.MM 和kurtosis.MM 估计。Martellini and Ziemann (2007)
    提出了更高效的估计量（estimators），会在将来实现。

    如Cont、Deguest和Scandolo (2007)讨论过的，ES度量估计对单个异常值稳健相当重要。尤其在改进VaR/ES和它的成分分解情况下，
    因为它们使用高阶矩。缺省地，组合矩根据它们的样本对应部分估计。如果clean="boudt"，那么当1-p最极端观测值被检测为异常值，
    它们会被温莎化（winsorized6）。有关详情，参见Boudt、 Peterson和Croux (2008) 和Return.clean。如果你的数据由高非流动性资产组成，
    那么clean="geltner"也许在缩减自相关带来的扭曲方面更合适，参见Return.Geltner。

备注
    ES度量的invert（反转）选项将调和理论和实践工作者。ES作为极端损失的负值的数学定义常常会产生一个正数。实践工作者争辩说，ES意味损失，
    应该内在的与分位数（一个负数）保持一致。对图表而言，不同偏好选项也许应用于清晰和紧凑。有鉴于此，我们提供该选项，
    并将缺省值设为TRUE以让收益与PerformanceAnalytics 之前版本保持一致。哪种方式更好，我们不做判断。

参考
    1. Boudt, Kris, Peterson, Brian, and Christophe Croux. 2008. Estimation and decomposition of downside risk for portfolios with non-normal returns. 2008. The Journal of Risk, vol. 11, 79-103.
    2. Cont, Rama, Deguest, Romain and Giacomo Scandolo. Robustness and sensitivity analysis of risk measurement procedures. Financial Engineering Report No. 2007-06, Columbia University Center for Financial Engineering.
    3. Laurent Favre and Jose-Antonio Galeano. Mean-Modified Value-at-Risk Optimization with Hedge Funds. Journal of Alternative Investment, Fall 2002, v 5.
    4. Martellini, Lionel, and Volker Ziemann. Improved Forecasts of Higher-Order Comoments and Implications for Portfolio Selection. 2007. EDHEC Risk and Asset Management Research Centre working paper.
    5. Pflug, G. Ch. Some remarks on the value-at-risk and the conditional value-at-risk. In S. Uryasev, ed., Probabilistic Constrained Optimization: Methodology and Applications, Dordrecht: Kluwer, 2000, 272-281.
    6. Scaillet, Olivier. Nonparametric estimation and sensitivity analysis of expected shortfall. Mathematical Finance, 2002, vol. 14, 74-86.

另见
    VaR SharpeRatio.modified chart.VaRSensitivity Return.clean

范例
::

    data(edhec)

    # first do normal ES calc
    ES(edhec, p=.95, method="historical")

    # now use Gaussian
    ES(edhec, p=.95, method="gaussian")

    # now use modified Cornish Fisher calc to take non-normal distribution into account
    ES(edhec, p=.95, method="modified")

    # now use p=.99
    ES(edhec, p=.99)
    # or the equivalent alpha=.01
    ES(edhec, p=.01)

    # now with outliers squished
    ES(edhec, clean="boudt")

    # add Component ES for the equal weighted portfolio
    ES(edhec, clean="boudt", portfolio_method="component")

