# reportsheet

报表的设计和生成，对于创建销售跟踪报告、员工报告、财务报告、订单报告等场景非常重要。
这是任何企业应用领域的常见需求，通常需要消耗大量的时间、人力和努力。

* 报表是一种创建复杂报表的简单灵活方式。它支持数据输入、分页、数据过滤、排序、条件格式化等多种功能。
* 要创建报表，SpreadJS 中有两个重要的设置部分；报表模板(TemplateSheet) 和报表表格(ReportSheet)。
* 报表模板(TemplateSheet)包含与报表相关的设置，如布局、格式化和任何其他配置，而报表表格(ReportSheet)的设置用于加载报表模板并将其与数据管理器中的数据结合，生成相应的报表。
* 报表还提供了数据录入 API。

下图显示了报表插件的核心流程，以及如何从服务器获取数据，将其加载到 DataManager 中，为报表创建一个具有相关设置的 报表模板，然后将模板与 DataManager 中的数据结合，生成相应的报表表格。
![image](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/ca82939a-5d1a-4838-9f3f-69a0f7ebeeb5/image.356e03.png)
您还可以在 Spread Designer 中插入报表，方法是选择“插入”标签页，然后在“表”组中选择报表。
![image](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/ca82939a-5d1a-4838-9f3f-69a0f7ebeeb5/image.dcaeeb.png)
使用报表的主要价值有：

* 整合的模板和数据管理：允许报表表格和模板的组合无缝整合报告设置和数据。报表模板包含各种与报告相关的设置，报表利用这些设置以及 DataManager 中的数据高效生成相应的报告。
* 增强的灵活性：提供高度灵活的语法和 API 来绑定源数据。它遵循简单的数据填充规则，并提供数据输入 API。
* 定制的便利性：确保所有生成的报告具有标准化的格式和外观，保持各种数据集之间的一致性。
* 全面的数据处理功能：以用户友好的方式管理和展示数据。报表不仅仅是关于报告生成；它是一个全面的工具，支持数据输入、分页、数据过滤、排序和条件格式化。

让我们看看报表的不同示例。
**示例 1：财务报告**
这个例子展示了不同国家不同季度的预算统计。
首先，在 DataManager 中定义 'Bud'（预算）和 'Act'（实际）表。然后，设置报告模板的样式。下图展示了一个 TemplateSheet，其中单元格 A1 和 D1 包含标题单元格中的静态数据。数据列显示了记录在报告中的国家名称、年份和时间段。然后将国家字段水平扩展以添加其他国家，垂直扩展以添加季度详情。SUM() 函数用于获取 Bud 和 Act 列的总计。
![image](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/ca82939a-5d1a-4838-9f3f-69a0f7ebeeb5/image.2d8693.png?width=600)
进一步，将数据与创建的模板绑定，并使用诸如 ‘Group' 单元格类型、过滤器、固定、垂直和水平方向溢出等规范来增强生成报告的可读性，并为其提供清晰的结构。
从上述报表模板生成的财务报告如下所示。
![image](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/ca82939a-5d1a-4838-9f3f-69a0f7ebeeb5/image.dc8e55.png)
**示例 2：销售报告**
这个例子展示了单个销售人员在各个地区的多个产品的区域销售报告。
在这种情况下，首先在 DataManager 中定义销售表。然后，设置报告模板的样式。下图显示了一个报表模板，其中数据列显示了记录在报告中的地区、销售人员姓名、产品和销售详情。
SUM() 函数计算 Sales 列中的总销售额。
![image](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/ca82939a-5d1a-4838-9f3f-69a0f7ebeeb5/image.10cd2a.png)
现在，将数据列绑定到模板，并使用 ‘Group' 和 'Summary’ 单元格类型。
从上述模板生成的销售报告如下所示。
![image](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/ca82939a-5d1a-4838-9f3f-69a0f7ebeeb5/image.a20976.png?width=400)