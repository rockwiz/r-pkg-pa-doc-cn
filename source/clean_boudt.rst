clean.boudt
===========

描述
    清洗时间序列中的极端观测值以提供更稳健的风险估计。稳健地清洗时间序列以降低超过 1-α% 风险阈值的观测值的放大倍数，
    但不会影响这些观测值的数目和方向。

用法
::

    clean.boudt(R, alpha = 0.01, trim = 0.001)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :alpha: 在1-α 处过滤的概率，缺省为.01 (99%)
    :trim: 何处设置马氏距离（Mahalanobis distance）的极端值

说明
    许多风险度量是用资产或资产组合收益分布的二（四）阶矩来计算。组合的矩对数据峰值极其敏感，这种敏感性在多元环境中只会被加剧。
    由于这个缘故，考虑估计对与高斯分布偏差极大的收益观测值稳健的多元矩是恰当的。

    相比通过它们的样本均值估算多元矩，有两种主要方式来定义稳健的替代方案。一种方式是考虑一个比样本均值更稳健的估计量（estimator），
    另一种是首先（以一种稳健方式）清洗数据，然后再采用样本均值和清洗后数据的矩。

    我们的清洗方法遵循第二种方式。它以这样的方式设计，如果要估算带损失概率α 的下方风险，它永远不会清洗属于(1-α )最小极端观测值的观测值。
    假设我们有一个长度为的n-维向量时间序列，我们按以下三步清洗时间序列：

    1. 在它们的极值函数中给观测值划分等级。指定μ和Σ代表大容量数据的均值和协方差矩阵，让 :math:`\lfloor . \rfloor` 作为取其参数整数部分的
       算子。 :math:`r_t` 作为收益观测值极端性测度，我们用它的马氏（Mahalanobis）距离
       平方 :math:`d^2_t={(r_t-\mu)}\sum^{(-1)}{(r_t-\mu)}` 。依照Rousseeuw(1985)的做法，将μ和Σ估计为子集的均值向量和协方差矩
       阵（修正过以确保一致），该子集的大小为 :math:`\lfloor{(1-2)}\rfloor` 、其中元素的协方差矩阵的行列式最小的子集的均值向量和
       协方差矩阵。 这些估计将对α最极端收益稳健。 :math:`d^2_{(1)},\dots,d^2_{(T)}` 是估计马氏距离平方的有序序列，
       即 :math:`d^2_{(i)}\leq{d^2_{(i+1)}}` 。
    2. 异常值标识。收益观测值被认定为异常值，如果它们的估计马氏距离平方大于实证1-α分位数  :math:`d^2_{(\lfloor(1-\alpha)\rfloor{T})}` ，
       并且超过n自由度卡方（ :math:`\chi^2` ）分布―当收益为正态分布时，它是的分布函数―的一个非常极端分位数。在本应用中，
       我们取99.9%分位数，代表 :math:`\chi^2_{n,0.999}` 。
    3. 数据清洗。与Khan(2007) 相同，我们仅清洗那些在第二步被标识为异常值的收益，通过将这些收益 :math:`r_t` 替换为：

       .. math::

            r_t\sqrt{\frac{max(d^2_{(\lfloor{(1-\alpha)}\rfloor{T})}, \chi^2_{n,0.999})}{d^2_t}}

    清洗后的收益向量与原始收益向量同样的特性，但是它的量值较小。Khan(2007) 将这种把的值限制为分布的一个分位数的过程称为
    “multivariate Winsorization”。

    注意，数据清洗的主要价值在于创建一个有关生成绝大多数收益数据分布的更健壮（robust）和平稳（stable）的估计。
    采用清洗后数据估计出的矩所提升的健壮性和平稳性将用于投资组合构造。如果组合经理希望有一个更保守的风险估计，清洗也许没有指明风险监控。
    这里提出的稳健方法并不从序列中剔除数据，只是仅仅降低极端事件的量值，这一点也很重要。实践中，
    用经理希望考虑的VaR阈值以外的某种清洗阈值也可能是恰当的。实际上，最好是将清洗过和未清洗序列都进行回溯检验，
    看哪个最适合考虑中的特定组合。

返回值
    清洗后的数据矩阵

备注
    This function and much of this text was originally written for Boudt, et. al, 2008

参考
    1. Boudt, K., Peterson, B. G., Croux, C., 2008. Estimation and Decomposition of Downside Risk for Portfolios with Non-Normal Returns. Journal of Risk, forthcoming.
    2. Khan, J. A., S. Van Aelst, and R. H. Zamar (2007). Robust linear model selection based on least angle regression. Journal of the American Statistical Association 102.
    3. Maronna, R. A., D. R. Martin, and V. J. Yohai (2006). Robust Statistics: Theory and Methods. Wiley.
    4. Rousseeuw, P. J. (1985). Multivariate estimation with high breakdown point. In W. Grossmann, G. Pflug, I. Vincze, and W. Wertz (Eds.), Mathematical Statistics and Its Applications, Volume B, pp. 283?297. Dordrecht-Reidel.

另见
    Return.clean

