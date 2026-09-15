# window-function

窗口函数为在表格工作表中进行数据分析提供了一组函数。这些函数在与当前行存在某种关联的窗口（一组表格行）上执行计算，并生成一列来显示结果。进行函数求值的行称为当前行。
窗口函数在特定的窗口上执行聚合、排名和分析函数，并为每一行生成一个结果。

> **注意事项**：
>
> * 窗口函数的结果可能会对表格工作表的行顺序产生影响。
>     如果表格工作表已经进行了排序或分组，结果将保持不变。
> * 当表格工作表的分层数据中存在树状结构时，窗口函数将不起作用。
> * 表格工作表筛选器在窗口函数求值之后执行，并且仅筛选特定的行。

WINDOW 只能与窗口函数一起使用。默认情况下，它将整行视为一个窗口。
**语法**
`WINDOW(window_function, [partitionby_function], [orderby_function], [frame_function])`
**参数**
此函数具有以下参数：

| **参数** | **描述** |
| --- | --- |
| *window\_function* | [必填] 窗口函数。 |
| *[partitionby\_function]* | [可选] 将行划分为分区。 |
| *[orderby\_function]* | [可选] 定义每个分区内行的逻辑顺序。 |
| *[frame\_function]* | [可选] 指定起点和终点，以便将行组合为分区内相对于当前行的窗口。 |

## WINDOW

WINDOW 函数在应用关联的窗口函数之前，确定分区、排序和限制窗口。
WINDOW 函数使用 PARTITIONBY 和 ORDERBY 参数更改行的顺序。
请注意，如果在一个视图中应用了多个 WINDOW 函数，那么它们的 PARTITIONBY 和 ORDERBY 必须相同，因为整行的顺序将由 PARTITIONBY 和 ORDERBY 参数重新排序。否则，整行将显示最后应用的 WINDOW 的顺序。
**示例**
`WINDOW(ROWNUMBER(), PARTITIONBY([country]))`
要了解所有可用的窗口函数的更多信息，请参阅 [窗口函数列表](gcdocsite__documentlink?toc-item-id=9297ca1e-6d1b-4430-9b92-539e060fd88e) 部分。

## PARTITIONBY

PARTITIONBY 函数按升序将行划分为分区，并且窗口函数将分别应用于每个分区。如果未指定 PARTITIONBY，则整行将被视为一个窗口。PARTITIONBY 必须包含一个或多个列表达式，这些表达式可以是字段名或公式。
**语法**
`PARTITIONBY(field_function [, field_function [, ... ] ])`
**参数**
此函数具有以下参数：

| **参数** | **描述** |
| --- | --- |
| *field\_function* | [必填] 用于分区的字段名或公式。 |

**示例**
`WINDOW(SUM([Sales]), PARTITIONBY([Product], YEAR([@OrderDate])))`

## ORDERBY

ORDERBY 定义每个分区内行的逻辑顺序。它将影响指定的窗口以及窗口函数的计算。ORDERBY 必须包含一个或多个列表达式，这些表达式可以是字段名或公式。
**语法**
`ORDERBY(field_function [, field_function [, ... ] ])`
**参数**
此函数具有以下参数：

| **参数** | **描述** |
| --- | --- |
| *field\_function* | [必填] 用于排序的字段名或公式。 |

你还可以使用 ORDERASC 和 ORDERDESC 按升序或降序对数据进行排序。默认情况下，排序顺序为 ORDERASC，并且 NULL 值被视为最小值。

> **注意**：
>
> * 如果未指定 ORDERBY，窗口函数将使用分区中所有等于 FRAMERANGE(-1, -1) 的行。
> * 如果指定了 ORDERBY 但未指定 FRAMEROWS/FRAMERANGE，则 FRAMERANGE(-1, [@]) 将是默认的范围表达式，用于限制窗口函数计算的窗口范围。

**语法**
`ORDERASC(field function)`
`ORDERDESC(field function)`
**示例**
`WINDOW(SUM([Sales]), ORDERBY([Product], ORDERDESC(QUARTER([@OrderDate]))))`

## FRAME

FRAME 函数指定起点和终点，以便将行组合为分区内相对于当前行的窗口。窗口函数将使用窗口指定的行集。一个窗口由起点行、终点行和当前行组成。FRAME 函数可以定义为 FRAMFRAMEROWS、FRAMERANGE 或 FRAMEGROUPS。

### FRAMEROWS

FRAMEROWS 函数允许你通过指定当前行之前和之后的非负整数行数来限制窗口的行。如果前面或后面的行数之一超出当前分区的边界，则使用分区的起始行或结束行。如果将前面或后面的行指定为 -1，则会得到相同的结果。但是，如果两者都超出范围，则不会返回任何行。

| **参数** | **可接受的值** | **描述** |
| --- | ----- | --- |
| 第一个参数表示当前行之前的行数。 | -1, [@-n] 或 [@] | @rows=2:-1: 表示当前分区的边界。n: 接受一个非负整数，表示行数。[@]: 表示当前行的位置。 |
| 第二个参数表示当前行之后的行数。 | -1, [@+n] 或 [@] |

> **注意**：如果 FRAMEROWS 函数中缺少第二个参数，则默认值为 [@]。

**语法**
`FRAMEROWS(preceding_function [, following_function ])`
**参数**
此函数具有以下参数：

| **参数** | **描述** |
| --- | --- |
| *preceding\_function* | [必填] 当前行之前的行数。 |
| *[following\_function]* | [可选] 当前行之后的行数。 |

**示例**
`WINDOW(SUM([Sales]), PARTITIONBY([Product], YEAR([@OrderDate])), ORDERBY(QUARTER([@OrderDate])), FRAMEROWS([@-1], [@]))`

### FRAMERANGE

FRAMERANGE 函数通过指定一个非负数字作为与当前行在由 ORDERBY 列组成的值相同的对等行周围的距离，来限制窗口的范围。
FRAMERANGE 函数有两个主要参数，每个参数表示当前行的对等行之前和之后的距离。

| **参数** | **可接受的值** | **描述** |
| --- | ----- | --- |
| 第一个参数表示当前行的对等行之前的距离。 | -1, [@-n]如果顺序为降序，则应为 [@+n]），或 [@]。 | @rows=2:-1: 表示当前分区的边界。n: 接受一个非负整数，表示距离。[@]: 表示与当前行具有相同值的对等行。 |
| 第二个参数表示当前行的对等行之后的距离。 | -1, [@+n]如果顺序为降序，则应为 [@-n]），或 [@]。 |

帧范围是一个完全封闭的区间。它要求 ORDERBY 提供的第一列具有数字数据类型。但是，如果有多个排序列，则仅接受 -1 和 [@]。

#### 与 ORDERBY 一起使用的 FRAMERANGE

* FRAMERANGE 要求 ORDERBY 仅提供一个具有数字数据类型的列，以检索当前行中的值，从而找到与 [@] 相等的行。
* 如果删除了 ORDERBY，即使指定了 FRAMERANGE，默认的帧表达式也是 FRAMERANGE(-1, -1)。
* 如果 ORDERBY 包含多个列，则在 FRAMERANGE 中只能使用 -1 和 [@]，并且 [@-/+n] 将默认为 -1。当前相等的行可能由组合的列值定义。

#### 与 NULL 一起使用的 FRAMERANGE

* 如果排序列中的某些值为 NULL，则具有 NULL 值的行将在分区内的顶部/底部并排排列。
* 如果当前相等行的值为 NULL，[@+/-n] 将类似于 [@+/-0]，即等于 [@]。
* 如果当前相等行的值不为 NULL，则对 [@+/-n] 的检索将在具有 NULL 值的行处停止。

**语法**
`FRAMERANGE(preceding_function [, following_function ])`
**参数**
此函数具有以下参数：

| **参数** | **描述** |
| --- | --- |
| *preceding\_function* | [必填] 当前行之前的距离。 |
| *[following\_function]* | [可选] 当前行之后的距离。 |

**示例**
`WINDOW(SUM([Sales]), PARTITIONBY([Product], YEAR([@OrderDate])), ORDERBY(QUARTER([@OrderDate])), FRAMERANGE([@-1], [@]))`
以下图片展示了如何使用聚合窗口函数获取每个产品的移动平均收入和收入趋势。
![窗口函数](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/5fefd5d8-238b-4c13-893b-6f22fcc5b9dd/WindowFunctions.bf5731.fb1609.png)

### FRAMEGROUPS

FRAMEGROUPS 函数根据相对于当前组的“组”数指定起始和结束边界，其中“组”是指从窗口 ORDERBY 派生的具有相等值的行集。
如果组计数超出分区的边界，则会退回到起始/结束组，并且如果前面/后面的组计数均为 -1，则会指定该组计数，但如果两者都超出范围，则不会返回任何内容。

| **参数** | **可接受的值** | **描述** |
| --- | ----- | --- |
| 第一个参数表示相对于当前组的起始组计数。 | -1, [@-n], [@+n], 或 [@] | @rows=2:-1: 表示分区的无边界（起始或结束）。[@-n] 或 [@+n]: 表示当前组旁边的组计数，并且‘n’接受一个非负整数。[@]: 表示当前组的位置。 |
| 第二个参数表示相对于当前组的结束组计数。 | -1, [@-n], [@+n] 或 [@] |

> **注意**：如果 FRAMEGROUPS 函数中缺少第二个参数，则默认值为 [@]。

**语法**
`FRAMEGROUPS(BeginningExpression, [EndingExpression], [ExcludeMode])`
**参数**
此函数具有以下参数：

| **参数** | **描述** |
| --- | --- |
| *Beginning\_Expression* | [必填] 当前组之前的组计数。 |
| *[EndingExpression]* | [可选] 当前组之后的组计数。 |

**示例**
`WINDOW(SUM([Sales]), PARTITIONBY([Product], YEAR([@OrderDate])), ORDERBY(DATEPART([@OrderDate], \"Q\")), FRAMEGROUPS([@-1], [@]))`

#### 与 ORDERBY 一起使用的 FRAMEGROUPS

* FRAMEGROUPS 要求 ORDERBY 提供列以检索当前行中的值，从而找到与 [@] 相等的行。
* 如果删除了 ORDERBY，即使指定了 FRAME GROUPS，默认的帧表达式也是 FRAMEGROUPS(-1, -1)。
* 如果 ORDERBY 有多个列，则当前相等的行是根据组合的列值定义的。例如，如果你按年、季度和月份进行排序，则当前相等的行是由这些相同的列标识的。

### 带排除模式的 FRAME

带排除模式的帧是 FRAME 表达式中的最后一个参数。它是一个可选参数，有四种类型。

#### EXCLUDE NO OTHERS

表示“不排除任何行”，用 0 表示。
**示例**
`WINDOW(SUM([Sales]), PARTITIONBY([Product], YEAR([@OrderDate])), ORDERBY(DATEPART([@OrderDate], \"Q\")), FRAMEGROUPS([@-1], [@], 1))`
以下图片展示了如何使用带排除模式的聚合窗口函数获取每个产品的月平均收入、近期平均收入和收入趋势。
![不排除其他行](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/5fefd5d8-238b-4c13-893b-6f22fcc5b9dd/exclude-no-other.c0df2b.7d39ca.png)

#### EXCLUDE CURRENT ROW

表示排除当前行，但是对于 FRAMEGROUPS 和 FRAMERANGE，当前行的其他对等行仍然保留，用 1 表示。
**示例**
`WINDOW(SUM([Sales]), PARTITIONBY([Product], YEAR([@OrderDate])), ORDERBY(DATEPART([@OrderDate], \"Q\")), FRAMEGROUPS([@-1], [@], 1))`
以下图片展示了如何使用带排除模式的聚合窗口函数获取每个产品的月平均收入、近期平均收入和收入趋势。
![排除当前行](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/5fefd5d8-238b-4c13-893b-6f22fcc5b9dd/exclude-currentrow.bc12da.3cf1d4.png)

#### EXCLUDE GROUP

表示排除当前行及其对等行，即使是在 FRAMEROWS 中，用 2 表示。
**示例**
`WINDOW(SUM([Sales]), PARTITIONBY([Product], YEAR([@OrderDate])), ORDERBY(DATEPART([@OrderDate], \"Q\")), FRAMEGROUPS([@-1], [@], 2))`
以下图片展示了如何使用带排除模式的聚合窗口函数获取每个产品的月平均收入、近期平均收入和收入趋势。
![排除组](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/5fefd5d8-238b-4c13-893b-6f22fcc5b9dd/exclude-group.921965.b6fc2a.png)

#### EXCLUDE TIES

表示当前行保留，但是其他对等行被排除，用 3 表示。
**示例**
`WINDOW(SUM([Sales]), PARTITIONBY([Product], YEAR([@OrderDate])), ORDERBY(DATEPART([@OrderDate], \"Q\")), FRAMEGROUPS([@-1], [@], 3))`
以下图片展示了如何使用带排除模式的聚合窗口函数获取每个产品的月平均收入、近期平均收入和收入趋势。
![排除相等行](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/5fefd5d8-238b-4c13-893b-6f22fcc5b9dd/exclude-ties.29ba9a.c0f73e.png)

### 窗口链接

窗口链接允许你先定义一个窗口，然后重用新窗口，新窗口隐式指定了 PARTITYIONBY、ORDERBY 或窗口帧。
在预定义的窗口中，PARTITIONBY、ORDERBY 和窗口帧会被新窗口的表达式覆盖。
**示例**
`WINDOWDEF(PARTITIONBY([Product], YEAR([@OrderDate])), ORDERBY(DATEPART([@OrderDate], \"Q\")), FRAMEROWS([@-2], [@], 3))`
以下图片展示了如何使用窗口函数获取每个产品的平均收入/收入质量和收入趋势。
![窗口链接公式](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/5fefd5d8-238b-4c13-893b-6f22fcc5b9dd/window-chaining-formula.a9343f.abb806.png)