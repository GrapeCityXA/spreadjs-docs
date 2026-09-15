# reportsheet

生成报告对于制定营销策略、旅行报告、销售跟踪报告、员工报告、财务报告、订单报告等都非常重要。这是任何业务领域的常见需求，并且通常会消耗大量的时间、人力和精力。报表工作表（ReportSheet）是一种简单灵活的方式，可轻松创建复杂的报告。它支持数据录入、分页、数据筛选、排序、条件格式设置等诸多功能。
在 SpreadJS 中，创建报表工作表有两个重要的设置部分：[模板工作表](gcdocsite__documentlink?toc-item-id=51cc63cb-b943-4b2a-9757-6a1db73fec4e)和[报表工作表](gcdocsite__documentlink?toc-item-id=1c38288f-6e37-4a72-b4b7-2106262c569e)。模板工作表包含与报告相关的设置，如布局、格式设置以及其他任何规格，而报表工作表则有加载模板工作表并将其与数据管理器中的数据相结合以生成相应报告的设置。报表工作表还提供了数据录入的 API。
下图展示了报表工作表的核心流程，以及如何从服务器获取数据、将其加载到数据管理器中、为报告创建带有相关报告设置的模板工作表，然后将模板与数据管理器中的数据相结合以生成相应的报表工作表。
![rs-create-flowchart.e4eee4](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/5fefd5d8-238b-4c13-893b-6f22fcc5b9dd/rs-create-flowchart.e4eee4.01014b.png)
你还可以在 [Spread 设计器中插入报表工作表](gcdocsite__documentlink?toc-item-id=d1addfc5-f03a-4608-b423-590e545137ea)，方法是选择“插入”选项卡，然后在“工作表”组中选择“报表工作表”。
![ReportSheetUI.6b1854](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/5fefd5d8-238b-4c13-893b-6f22fcc5b9dd/ReportSheetUI.6b1854.df6751.png)
使用报表工作表的主要好处如下：

* **集成模板和数据管理**：通过报表工作表和模板工作表的结合，实现报告设置和数据的无缝集成。模板工作表包含各种与报告相关的设置，报表工作表利用这些设置以及数据管理器中的数据，高效地生成相应的报告。
* **增强的灵活性**：提供高度灵活的语法和 API 来绑定源数据。它遵循简单的数据填充规则，并且还提供数据录入 API。
* **易于定制**：确保所有生成的报告具有标准化的格式和外观，在各种数据集之间保持一致性。
* **全面的数据处理功能**：以用户友好的方式管理和呈现数据。报表工作表不仅仅是用于生成报告，它还是一个全面的工具，支持数据录入、分页、数据筛选、排序和条件格式设置。

让我们来看看报表工作表的不同用例。

#### 用例 1：财务报告

此示例展示了不同国家不同季度的预算统计情况。
首先，在数据管理器中定义“Bud”（预算）和“Act”（实际情况）表。然后，为你的报告模板设置样式。下图展示了一个模板工作表，其中单元格 A1 和 D1 在标题单元格中包含静态数据。数据列显示了报告中记录财务数据的国家名称、年份和时间段。然后，国家字段会水平扩展以添加其他国家，垂直扩展以添加季度详细信息。使用 SUM() 函数来计算“Bud”和“Act”列的总计。
![FinalcialReport-TemplateSheet.056437](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/5fefd5d8-238b-4c13-893b-6f22fcc5b9dd/FinalcialReport-TemplateSheet.056437.a2ed2d.png)
进一步地，将数据与创建的模板进行绑定，并使用“分组”单元格类型、筛选、固定、垂直和水平方向扩展等规格，以提高生成报告的可读性并为其提供清晰的结构。
从上述模板工作表生成的财务报告如下所示。
![FinalcialReport-ReportSheet.f4ccf7](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/5fefd5d8-238b-4c13-893b-6f22fcc5b9dd/FinalcialReport-ReportSheet.f4ccf7.faaa7c.png)

#### 用例 2：销售报告

此示例展示了每个销售人员的区域销售报告，以及每个区域多种产品的销售情况。
在这种情况下，首先在数据管理器中定义销售表。然后，为你的报告模板设置样式。下图展示了一个模板工作表，其中数据列显示了报告中记录数据的区域、销售人员姓名、产品和销售详细信息。使用 SUM() 函数计算“销售”列的总销售额。
![SalesReport _TemplateSheet.9e677d](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/5fefd5d8-238b-4c13-893b-6f22fcc5b9dd/SalesReport%20_TemplateSheet.9e677d.1afee1.png)
现在，将数据列绑定到模板，并使用“分组”和“汇总”单元格类型。
从上述模板工作表生成的销售报告如下所示。
![SalesReport_ReportSheet.5d2b6b](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/5fefd5d8-238b-4c13-893b-6f22fcc5b9dd/SalesReport_ReportSheet.5d2b6b.ec596c.png)