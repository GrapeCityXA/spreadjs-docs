# core-concept

本子分类介绍 SpreadJS 的基础对象模型与核心机制。这些概念是使用 SpreadJS 任何功能的基础，建议所有开发人员在开始开发前通读本章节。

### 对象模型概览

SpreadJS 的核心对象遵循层级关系：

```auto
Workbook（工作簿）
  └── Worksheet（工作表）
        ├── Range / Cell（区域 / 单元格）
        ├── Row / Column（行 / 列）
        ├── Table（表格）
        └── Shape / Chart（形状 / 图表等浮动对象）
```

### 本章节内容

| 主题 | 说明 |
| --- | --- |
| **[工作簿](gcdocsite__documentlink?toc-item-id=380cf576-9e06-44be-a23e-26d7d7c8d96c)** | Workbook 是 SpreadJS 的顶层对象，管理工作表、计算引擎、数据管理器等核心组件。 |
| **[工作表](gcdocsite__documentlink?toc-item-id=f6e37085-16df-4985-b8e9-8c79291171c8)** | Worksheet 是数据承载的主体，支持普通工作表、集算表、甘特表、报表等多种类型。 |
| **[行与列](gcdocsite__documentlink?toc-item-id=cd0919be-2a88-4c9e-9f2d-fd186db10722)** | 行列的增删、调整大小、冻结、筛选、拖动等操作。 |
| **[单元格](gcdocsite__documentlink?toc-item-id=0b7317a8-0f07-4b11-afdf-8f412c65fa6d)** | 单元格的值、样式、公式、数据类型、合并等设置。 |
| **[单元格标题](gcdocsite__documentlink?toc-item-id=64fe4446-b037-4f10-81a2-791fec44f42e)** | 行头列头的自定义与配置。 |
| **[数据绑定](gcdocsite__documentlink?toc-item-id=331fdd70-0ac5-48dd-8a69-c3c63ea1aa16)** | 将工作表与数据源绑定，实现数据的自动填充与回写。 |
| **[用户管理](gcdocsite__documentlink?toc-item-id=77980a93-928a-41d1-b000-7390d237371f)** | 可用于协同插件、单元格评论的用户信息管理机制。 |
| **[序列化](gcdocsite__documentlink?toc-item-id=adbb66e6-dd64-4a18-ad11-2b4a8bb62c76)** | 将工作簿状态序列化为 JSON，用于持久化存储与传输。 |
| **[键盘行为](gcdocsite__documentlink?toc-item-id=0cecceee-e737-416d-a808-e6e967c4c3b5)** | SpreadJS 内置的快捷键与键盘交互逻辑，以及自定义方式。 |
| **[表单控件](gcdocsite__documentlink?toc-item-id=f62ba467-b778-4053-84e3-f2eacebe04bc)** | 兼容 Excel 的表单空间，如按钮、调节器、单选框等。 |
| **[文化](gcdocsite__documentlink?toc-item-id=56cf04e7-0208-4270-b0f3-45fc1cc34424)** | 多语言、区域设置（日期格式、数字格式）的本地化支持。 |

### 学习路径

建议按照 **工作簿 → 工作表 → 行与列 → 单元格** 的顺序阅读，建立从整体到局部的对象模型认知。之后再根据实际需要阅读数据绑定、序列化、文化等进阶主题。