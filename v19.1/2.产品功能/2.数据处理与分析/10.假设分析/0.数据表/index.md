# data-table

数据表提供了一种结构化的方式，可通过多组输入值验算公式来开展假设分析。
无需手动修改输入单元格并记录结果，数据表会针对每一组输入组合自动重新计算同一公式，并将所有结果整合输出为一个动态数组。
在SpreadJS中，数据表功能通过`SJS.TABLE`函数实现。和Excel传统数据表不同，`SJS.TABLE`属于标准工作表公式，支持编辑、复制、嵌套在其他函数中使用，还可突破双输入变量的使用限制。
数据表尤其适用于以下场景：

* 敏感性分析
* 方案对比
* 多变量模拟运算
* 探究假设条件变动对计算结果造成的影响

依据设定的输入变量数量，数据表可实现：

* 单变量分析
* 双变量分析
* 多变量分析（不受Excel传统数量限制）

如需了解详细语法与使用方法，可查看[SJS.TABLE函数](gcdocsite__documentlink?toc-item-id=e07b0db6-00e9-4484-aaa0-11be694597a9)。
如需知晓输入组合与结果展示形式相关规则，可查看[输入与结果规则](gcdocsite__documentlink?toc-item-id=7016ce8a-58cf-48b5-912f-52a445bd89dc)。
如需了解性能相关注意事项，可查看[性能与计算](gcdocsite__documentlink?toc-item-id=8d8f5bbb-ad10-45fe-ad09-003c73992b67)。
如需查阅与Excel的兼容适配相关详情，可查看[Excel兼容性](gcdocsite__documentlink?toc-item-id=93cecc8d-7332-4c3e-b717-a4d1b7326139)。