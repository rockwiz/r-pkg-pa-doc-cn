Return.read
===========

描述
    简单的read.zoo封装函数，带一些针对不同日期格式和xts转换的缺省值。

用法
::

    Return.read(filename = stop("Please specify a filename"), frequency = c("d", "m", "q", "i", "o"),
                format.in =c("ISO8601", "excel", "oo", "gnumeric"), sep = ",", header = TRUE, check.names = FALSE, ...)

参数
    :filename: 要读取的文件的名字
    :frequency: - “d”设置为每日时间序列，使用as.Date
                - “m”设置为月度时间序列，使用as.yearmon
                - “q”设置为季度时间序列，使用as.yearqtr
                - “i”设置为不规则时间序列，使用as.POSIXct

    :format.in: 告知要读取的数据的格式如何。尽管缺省设置为ISO 8601 标准（也可设为“%F”），大多数电子表格在缺省状态下对日期格式不太敏感，
                参见以下内容
    :sep: 分隔符，缺省为“,”
    :header: 逻辑值，指示文件是否在其第一行包含变量名
    :check.names: 逻辑值。如果为TRUE，那么数据库中的变量名要被检查以确保它们在句法上有效。如果需要，它们将（通过make.names）被调整以使有效，
                  并且也确保没有重名。参见read.table
    :...: 传入到read.zoo 的任何其它参数

说明
    参数“format.in”可取几个值，包括：

* excel: MS-Excel电子表格csv格式的缺省日期格式，为“%m/%d/%Y”
* oo: OpenOffice电子表格csv格式的缺省日期格式，为“%m/%d/%y”，尽管可能依赖于操作系统
* gnumeric: Gnumeric 电子表格的缺省日期格式，为“%d-%b-%Y”
* ...: 另外，可传入任意指定格式，如“%M/%y”

另见
    read.zoo, read.table

范例
::

    ## Not run:
    Return.read("managers.cvs", frequency="d")
    ## End(Not run)


