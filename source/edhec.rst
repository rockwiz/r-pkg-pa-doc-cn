edhec
=====

描述
    EDHEC综合对称基金风格指数收益。

用法
::

    edhec

格式
    CSV，符合有月度观测值的xts对象

说明
    用于PerformanceAnalytics和相关出版物的EDHEC数据，获得了EDHEC风险和资产管理研究中心的许可。

    PerformanceAnalytics 中的“edhec”数据集将定期更新（典型地，每年）以包括进补充的观测值。如果你想要在自动测试中使用该数据集，
    请确保抽取数据子集，例如用edhec[1:120,]来使用头十年的观测值。

    From the EDHEC website: “The EDHEC Risk and Asset Management Research Centre plays a noted role in furthering applied
    financial research and systematically highlighting its practical uses. As part of its philosophy, the centre maintains
    a dialogue with professionals which benefits the industry as a whole. At the same time, its proprietary R&D provides
    sponsors with an edge over competition and joint ventures allow selected partners to develop new business opportunities.

    To further assist financial institutions and investors implement the latest research advances in order to meet the
    challenges of the changing asset management landscape, the centre has spawned two consultancies and an executive
    education arm. Clients of these derivative activities include many of the leading organisations throughout Europe.”

    参见 http://www.edhec-risk.com/about_us

参考
    1. About EDHEC Alternative Indexes. December 16, 2003. EDHEC-Risk.
    2. http://www.edhec-risk.com/indexes/pure_style/about
    3. Vaissie Mathieu. A Detailed Analysis of the Construction Methods and Management Principles of Hedge Fund Indices. October 2003. EDHEC.
    4. http://www.edhec-risk.com/site_edhecrisk/public/indexes/EDHEC_Publications/RISKReview1072705188065793513

源
    http://www.edhec-risk.com/indexes/pure_style

范例
::

    data(edhec)

    #preview the data
    head(edhec)

    #summary period statistics
    summary(edhec)

    #cumulative index returns
    tail(cumprod(1+edhec),1)

