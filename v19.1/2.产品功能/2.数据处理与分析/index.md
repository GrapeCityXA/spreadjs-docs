# data-processing-and-analysis

本子分类介绍 SpreadJS 中用于数据组织、管理、计算与分析的功能特性。这些功能适用于需要在 Web 端构建数据密集型应用（如 ERP、CRM、BI 报表、财务系统）的场景。

### [数据管理器（DataManager）](gcdocsite__documentlink?toc-item-id=5ebdeb7f-6ee0-4c6b-86ee-3502f110b1d0)

DataManager 是 SpreadJS 数据驱动体系的核心。每个 Workbook 实例拥有一个 DataManager 实例，它负责：

* **配置数据源**：连接 REST API、OData、GraphQL、本地 JSON 等多种数据源。
* **管理数据表**：定义表结构、schema、列行为。
* **建立关系**：在多张表之间建立关联关系。
* **创建视图**：为展示组件（集算表、报表、数据图表）提供定制化的数据视图。

> 集算表、甘特表、报表、数据图表均基于 DataManager 运行，共享同一数据模型。

### 数据驱动型工作表

SpreadJS 在普通工作表之外，提供了三种数据驱动型工作表，适用于不同的业务场景：

| 工作表类型 | 适用场景 | 数据来源 |
| ----- | ---- | ---- |
| **[集算表（TableSheet）](gcdocsite__documentlink?toc-item-id=78a1fc3a-e9fa-42ca-9a9a-1a907ddaa35b)** | 面向大数据量的数据展示与编辑，支持分页加载、列定制、计算列。 | DataManager 视图 |
| **[甘特表（GanttSheet）](gcdocsite__documentlink?toc-item-id=1ced61ab-d7e7-47d9-86ba-c30ea995df44)** | 项目管理中的甘特图展示，支持任务依赖、关键路径。 | DataManager 视图 |
| **[报表（ReportSheet）](gcdocsite__documentlink?toc-item-id=cea037a9-3660-4d7a-98e4-57363fb4ea43)** | 复杂格式的报表设计与数据填充，支持模板化布局。 | DataManager 表 |

### 数据交互与分析能力

除数据驱动型工作表外，SpreadJS 还提供了丰富的数据交互与分析功能：

| 主题 | 说明 |
| --- | --- |
| **[数据验证](gcdocsite__documentlink?toc-item-id=1342cf86-5473-4687-b68e-359a0f5d5e19)** | 限制单元格输入内容的类型、范围、格式，保证数据质量。 |
| **[排序](gcdocsite__documentlink?toc-item-id=29d57dab-6d98-4f89-9e10-b9ba160a5734)** | 按值、颜色、自定义规则对数据进行排序。 |
| **[分组](gcdocsite__documentlink?toc-item-id=f55c9774-206a-43a5-b8d5-6d70f5477c58)** | 区域分组、分级显示列、自定义区域分组，实现数据的层级展示。 |
| **[表格](gcdocsite__documentlink?toc-item-id=972d7e3d-e0d7-44d6-ba5f-98a21837b63f)** | 将普通区域转换为结构化表格，支持筛选、汇总行、样式套用。 |
| **[数据透视表（PivotTable）](gcdocsite__documentlink?toc-item-id=e92957b1-ad81-459d-89c1-7c638af239aa)** | 对大量数据进行多维度的交叉分析与汇总。 |
| **[切片器](gcdocsite__documentlink?toc-item-id=3283074a-d1c1-4dd4-a9f3-4c8fa61173bb)** | 为表格和透视表提供可视化的筛选交互。 |

### 选型建议

* **普通数据展示与编辑**：优先使用普通工作表 + 表格（Table）。
* **大数据量、需要远程分页**：使用集算表（TableSheet）。
* **需要多维分析**：使用数据透视表（PivotTable）。
* **项目管理场景**：使用甘特表（GanttSheet）。
* **复杂格式报表**：使用报表（ReportSheet）。

> 注意：集算表、甘特表、报表属于高级特性，普通表格编辑场景无需引入，优先从核心工作表能力出发。