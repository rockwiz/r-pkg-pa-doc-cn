Return.clean
============

描述
    一个提供多种方法清洗收益数据中异常值的函数，清洗时间序列中的收益以提供更稳健的风险估计。

用法
::

    Return.clean(R, method = c("none", "boudt", "geltner"), alpha = .01, ...)

参数
    :R: 一个资产收益的向量、矩阵、数据框、时间序列或zoo, xts对象
    :method: “none”、“boudt”和“geltner”之一。“boudt”将函数clean.boudtor应用到R上，“geltner”将函数Return.Geltner应用到R上
    :alpha: 要清洗的异常值的百分比
    :...: 传进清洗函数的附加参数

说明
    这是一个为包含收益的数据对象提供多种数据清洗方法的封装函数（wrapper）。

    数据清洗的主要价值在于创建一个更健壮（robust）和平稳（stable）的分布估计，以生成绝大多数收益数据。
    使用清洗后数据在估计矩上提升的健壮性和稳定性将用于投资组合构造。如果投资者希望有一个更保守的风险估计，清洗也许没有指示风险监控。

    在具体实践中，最好将清洗后和未清洗序列都进行回溯检验，看哪个更适合考虑中的资产组合。

    该版本中，仅支持一种方法。有关详情，参见clean.boudt。

另见
    clean.boudt Return.Geltner

范例
::

    data(managers)
    head(Return.clean(managers[,1:4]),n=20)
    chart.BarVaR(managers[,1,drop=FALSE], show.clean=TRUE, clean="boudt", lwd=2, methods="ModifiedVaR")


