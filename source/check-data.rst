checkData
=========

描述
    检查输入数据类型并格式化和强制转换为输出类型。该函数用来使不同类型的数据至少似乎更可互换。它允许用户传递数据对象，
    而不用担心函数需要一个matrix（矩阵）、data.frame （数据框）还是timeSeries（时间序列）对象。通过使用这个，
    该函数“知道”它要处理的是什么数据格式。

用法
::

    checkData(x, method = c("xts", "zoo", "data.frame", "matrix","vector"), na.rm = TRUE, quiet = TRUE, ...)

参数
    :x: 要检查并可强制转换的vector、matrix、data.frame、xts、timeSeries 或zoo对象
    :na.rm: TRUE/FALSE。是否从数据中剔除NA？仅和vector一起使用
    :quiet: TRUE/FALSE。如果为FALSE，错误发生时不会给出警告。缺省为TRUE
    :method: 返回的数据对象类型，c("zoo", "matrix", "vector")之一。缺省为“zoo”
    :...: 其它要传入的参数

范例
::

    data(edhec)
    x = checkData(edhec)
    class(x)
    head(x)
    tail(x)
    # Note that passing in a single column loses the row and column names
    x = checkData(edhec[,1])
    class(x)
    head(x)
    # Include the "drop" attribute to keep row and column names
    x = checkData(edhec[,1,drop=FALSE])
    class(x)
    head(x)
    x = checkData(edhec, method = "matrix")
    class(x)
    head(x)
    x = checkData(edhec[,1], method = "vector")
    class(x)
    head(x)

