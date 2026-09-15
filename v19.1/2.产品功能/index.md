# features

本章节系统性地介绍 SpreadJS 提供的全部功能特性，是您在开发过程中最常查阅的参考章节。

SpreadJS 提供了对 Excel 中几乎所有主要功能的支持，并在数据驱动表格、报表设计、协同编辑等方面进行了扩展。为方便查阅，本章节按功能域划分为四个子分类：

| 子分类 | 定位 |
| --- | --- |
| **[核心概念](gcdocsite__documentlink?toc-item-id=2a0cdd49-7f8c-43fc-8bc2-9da943af866d)** | 工作簿、工作表、单元格、行列等构成 SpreadJS 的基础对象模型，是理解其他功能的前提。 |
| **[数据处理与分析](gcdocsite__documentlink?toc-item-id=5696a13e-6125-45dd-9ddb-504be46503da)** | 数据管理器、集算表、甘特表、报表、数据验证、排序、分组、透视表等数据处理能力。 |
| **[可视化](gcdocsite__documentlink?toc-item-id=8d55950f-5f5a-44dd-a74d-7a97964b7fbd)** | 图表、迷你图、形状、条件格式、主题等将数据直观呈现的能力。 |
| **[文件操作](gcdocsite__documentlink?toc-item-id=7372e5a6-4773-4868-8aea-7fe01c15add6)** | Excel、PDF、CSV、JSON 等格式的导入导出能力。 |

此外，本章节还包含 **[AI 助手](gcdocsite__documentlink?toc-item-id=bd497cc2-8c3e-43fc-b7c0-48eb450a9347)** 的介绍——它是 SpreadJS 提供的智能化扩展能力，支持 AI 公式生成与解释、数据透视表生成等场景。

### 阅读建议

1. **先读核心概念**：无论您要使用哪项功能，理解 Workbook → Worksheet → Cell 的对象模型都是基础。
2. **按需查阅**：数据处理与可视化章节的各个功能相对独立，您可以根据实际需求选择性阅读。
3. **关注依赖关系**：部分高级功能（如图表、切片器）依赖 `shapes` 插件，引入时请注意插件加载顺序。