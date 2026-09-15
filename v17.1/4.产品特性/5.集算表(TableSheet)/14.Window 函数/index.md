# window-function

WINDOW 函数（v16.2）提供了一组在集算表中进行数据分析的函数。这些函数在与当前行相关的窗口（一组表格行）上进行计算，并生成一个列来显示结果。进行函数求值的行被称为当前行。
WINDOW 函数在特定窗口上执行聚合、排名和分析函数，并为每一行生成一个结果。

> **备注：**
>
> * WINDOW 函数的结果可能会对集算表的行顺序产生影响。如果集算表已经排序或分组，结果将保持不变。
> * 当集算表的层级数据中存在树形结构时，WINDOW 函数无效。
> * 集算表的筛选器在 WINDOW 函数求值后执行，并且仅筛选特定的行。

WINDOW只能与window函数一起使用。默认情况下，它将整个行视为一个窗口。
**语法**
`WINDOW(window_function, [partitionby_function], [orderby_function], [frame_function])`
**参数**
该函数具有以下参数：

| **参数** | **描述** |
| --- | --- |
| *window\_function* | [必需] 窗口函数。 |
| *[partitionby\_function]* | [可选] 将行分成分区。 |
| *[orderby\_function]* | [可选] 定义每个分区内行的逻辑顺序。 |
| *[frame\_function]* | [可选] 指定开始和结束点，将行组合到相对于当前行的分区内的窗口中。 |

## WINDOW

WINDOW函数在应用相关的窗口函数之前确定分区、排序和限制窗口。
WINDOW函数使用PARTITIONBY和ORDERBY参数改变行的顺序。
请注意，如果在视图中应用了多个WINDOW函数，则它们的PARTITIONBY和ORDERBY必须相同，因为整个行的顺序将由PARTITIONBY和ORDERBY参数重新排序。否则，整个行将显示来自最后一个应用的WINDOW的顺序。
**示例**
`WINDOW(ROWNUMBER(), PARTITIONBY([country]))`
要了解更多可用的窗口函数，请参阅[窗口函数列表](gcdocsite__documentlink?toc-item-id=15aefc42-e09a-4510-a018-2eb5fbef14fb)部分。

## PARTITIONBY

PARTITIONBY函数按升序将行分成分区，并将窗口函数分别应用于每个分区。如果未指定`PARTITIONBY`，则整个行将被视为一个窗口。`PARTITIONBY`必须具有一个或多个字段名称或公式的列表达式。
**语法**
`PARTITIONBY(field_function [, field_function [, ... ] ])`
**参数**
该函数具有以下参数：

| **参数** | **描述** |
| --- | --- |
| *field\_function* | [必需] 要进行分区的字段名称或公式。 |

**示例**
`WINDOW(SUM([Sales]), PARTITIONBY([Product], YEAR([@OrderDate])))`

## ORDERBY函数

`ORDERBY`函数定义了每个分区内行的逻辑顺序。它会影响指定的窗口和窗口函数的计算。`ORDERBY`必须具有一个或多个字段名称或公式的列表达式。
**语法**
`ORDERBY(field_function [, field_function [, ... ] ])`
**参数**
该函数具有以下参数：

| **参数** | **描述** |
| --- | --- |
| *field\_function* | [必需] 要进行排序的字段名称或公式。 |

您还可以使用`ORDERASC`和`ORDERDESC`以升序或降序方式对数据进行排序。默认情况下，排序顺序为`ORDERASC`，并且将`NULL`值视为最低值。

> **注意**：
>
> * 如果未指定 `ORDERBY`，则窗口函数将使用分区中等于 `FRAMERANGE(-1, -1)` 的所有行。
> * 如果指定了 `ORDERBY` 且未指定 `FRAMEROWS/FRAMERANGE，则FRAMERANGE(-1, [@])` 将成为计算窗口函数的默认范围表达式。

**语法**
`ORDERASC(field function)`
`ORDERDESC(field function)`
**示例**
`WINDOW(SUM([Sales]), ORDERBY([Product], ORDERDESC(QUARTER([@OrderDate]))))`

## FRAME

FRAME 函数指定开始和结束点，将行组合到相对于当前行的分区内的窗口中。窗口函数将使用由窗口指定的行集。窗口以开始、结束和当前行关闭。FRAME函数可以定义为FRAMEROWS或FRAMERANGE。

### FRAMEROWS

FRAMEROWS 允许您通过指定当前行之前和之后的非负整数行数来限制窗口的行集。如果前面或后面的行数中有一个超出了当前分区的边界，将使用分区的起始或结束行。如果两者都在外部，将不返回任何行。

| **参数** | **接受的值** | **描述** |
| --- | ---- | --- |
| 第一个参数<br>指示当前行之前的行数。 | -1, [@-n] 或 [@] | @rows=2:-1: 指示当前分区的边界。<br>n: 接受非负整数，表示行数。<br>\[@\]: 表示当前行的位置。 |
| 第二个参数<br>指示当前行之后的行数。 | -1, [@+n] 或 [@ |

> **注意**：如果FRAMEROWS函数中缺少第二个参数，则默认值为[@]。

**语法**
`FRAMEROWS(preceding_function [, following_function ])`
**参数**
该函数具有以下参数：

| **参数** | **描述** |
| --- | --- |
| *preceding\_function* | [必需] 当前行之前的行数。 |
| *[following\_function]* | [可选] 当前行之后的行数。 |

**示例**
`WINDOW(SUM([Sales]), PARTITIONBY([Product], YEAR([@OrderDate])), ORDERBY(QUARTER([@OrderDate])), FRAMEROWS([@-1], [@]))`

### FRAMERANGE

FRAMERANGE通过指定非负数作为当前行由ORDERBY列组成的对等行周围的相同值的距离，来限制窗口的范围。FRAMERANGE函数有两个主要参数，每个参数表示当前行的对等行之前和之后的距离。

| **参数** | **接受的值** | **描述** |
| --- | ---- | --- |
| 第一个参数<br>指示当前行的对等行之前的距离。 | -1, [@-n]<br>如果顺序是降序，则应使用[@+n]，或[@]。 | @rows=2:-1: 指示当前分区的边界。<br>n: 接受非负整数，表示距离。<br>\[@\]: 表示与当前行具有相同值的对等行。 |
| 第二个参数<br>指示当前行的对等行之后的距离。 | -1, [@+n]<br>如果顺序是降序，则应使用[@-n]，或[@]。 |

> 该框架范围是一个完全闭合的区间。它要求ORDERBY提供具有数值数据类型的第一列。但是，如果有多个排序列，只接受-1和[@]。

#### 带 ORDERBY 的 FRAMERANGE

* FRAMERANGE要求ORDERBY只提供一个具有数值数据类型的列，以检索当前行中的值，以找到[@]所对应的绑定行。
* 如果删除ORDERBY，则默认帧表达式为FRAMERANGE(-1, -1)，即使指定了FRAMERANGE。
* 如果ORDERBY包含多列，则只能在FRAMERANGE中使用-1和[@]，而[@-/+n]将默认为-1。当前捆绑行可以由组合列值定义。

#### 带 NULL 的 FRAMERANGE

* 如果排序列中的某些值为NULL，则具有NULL值的行将在分区内的顶部/底部并列排列。
* 如果当前捆绑行的值为空，[@+/-n]将类似于[@+/-0]，它等于[@]。
* 如果当前捆绑行的值不为空，[@+/-n]的检索将停止到具有NULL值的行。

**语法**
`FRAMERANGE(preceding_function [, following_function ])`
**参数**
该函数具有以下参数：

| **参数** | **描述** |
| --- | --- |
| *preceding\_function* | [必需] 当前行之前的距离。 |
| *[following\_function]* | [可选] 当前行之后的距离。 |

**示例**
`WINDOW(SUM([Sales]), PARTITIONBY([Product], YEAR([@OrderDate])), ORDERBY(QUARTER([@OrderDate])), FRAMERANGE([@-1], [@]))`
以下图片展示了如何使用聚合窗口函数获取每个产品的移动平均销售额和销售额趋势。
![WindowFunctions.bf5731](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/b33c4f64-6b99-4132-a675-8dc7b59765f1/WindowFunctions.bf5731.774588.png)