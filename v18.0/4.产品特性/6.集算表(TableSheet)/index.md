# tablesheet

集算表是一个快速的、数据绑定的表格视图，它具有类似网格的行为，以及电子表格用户界面和计算引擎，它使用数据管理器从服务器中提取数据，与之交互，然后创建一个获取数据的视图绑定到集算表。

![](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/041236cd-4159-4f89-9e42-7be2bb789d22/images/ts-create-flowchart.png)
使用集算表的主要好处如下：

* 更好的表格绑定方式,因此排序和筛选的性能更好。
* 支持组块，具有组级计算和切片器。
* 运行时面板允许调整列和组。
* 条件格式和规则基于绑定数据而非电子表格单元格值。

集算表可以使用 [GC.Spread.Sheets.TableSheet.TableSheet](gcdocsite__documentlink?toc-item-id=8dc0b7a4-ace7-4c61-b4a7-00790d5584fe) 和 [GC.Data.DataManager](gcdocsite__documentlink?toc-item-id=d168d582-7001-4e98-a184-2aafa89215e1) 类来创建。数据管理器是一个强大的本地数据引擎，它与数据库交互以提取数据、管理数据并将实时数据同步回数据库，然后创建获取数据的视图以将其绑定到集算表。
下图展示了一个为货物进口商和分销商创建的集算表。
![](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/041236cd-4159-4f89-9e42-7be2bb789d22/images/ts-basic.png)

## 集算表特性

要使用集算表的各种功能，请参阅以下主题：

| 特性 | 描述 |
| --- | --- |
| [集算表组件](gcdocsite__documentlink?toc-item-id=f58b8103-d578-42b7-9a3a-0603567c1be9) | 描述集算表结构及其组件。 |
| [数据管理器](gcdocsite__documentlink?toc-item-id=cfb05236-844a-4e41-b194-cd49c6122e38) | 描述数据管理器的工作及其方法。 |
| [创建集算表](gcdocsite__documentlink?toc-item-id=d082a118-73ea-4ae2-ae60-b387513d285e) | 通过代码在电子表格中创建集算表。 |
| [集算表视图](gcdocsite__documentlink?toc-item-id=ff337370-d76e-4bb2-a59f-47f72bf4e615) | 控制和自定义表格列的显示：<ul><li>[列标题样式](gcdocsite__documentlink?toc-item-id=ff337370-d76e-4bb2-a59f-47f72bf4e615#%E5%88%97%E6%A0%87%E9%A2%98%E6%A0%B7%E5%BC%8F)</li><li>[列标题自适应模式](gcdocsite__documentlink?toc-item-id=ff337370-d76e-4bb2-a59f-47f72bf4e615#%E5%88%97%E6%A0%87%E9%A2%98%E8%87%AA%E9%80%82%E5%BA%94%E6%A8%A1%E5%BC%8F)</li><li>[单元格类型和下拉列表](gcdocsite__documentlink?toc-item-id=ff337370-d76e-4bb2-a59f-47f72bf4e615#%E5%8D%95%E5%85%83%E6%A0%BC%E7%B1%BB%E5%9E%8B%E5%92%8C%E4%B8%8B%E6%8B%89%E5%88%97%E8%A1%A8)</li></ul> |
| [数据操作](gcdocsite__documentlink?toc-item-id=5a3b78b9-c9ab-4445-88ae-11a8fbe3a10e) | 以不同的同步模式高效地编辑数据源。 |
| [集算表关系](gcdocsite__documentlink?toc-item-id=a3ac9305-daec-4a7f-a586-97a962080057) | 使用数据管理器定义和创建表和字段的关系。 |
| [集算表操作](gcdocsite__documentlink?toc-item-id=e79fd996-ee54-4b53-9f49-8114963a93a3) | 在集算表上执行不同类型的操作：<ul><li>[锚定/取消锚定](gcdocsite__documentlink?toc-item-id=0b681e51-8c90-43c2-bb49-bc2e7d71b768)</li><li>[排序和筛选](gcdocsite__documentlink?toc-item-id=2276aff6-b5d6-47ec-81f1-6cafe2386676)</li><li>[行操作](gcdocsite__documentlink?toc-item-id=e9df7972-64f6-4063-a91d-fbd41322f6ac)</li><li>[分组](gcdocsite__documentlink?toc-item-id=91cdc22b-1a69-43e1-935b-b1ddee4cfe37)</li></ul> |
| [规则](gcdocsite__documentlink?toc-item-id=f0b2bf14-d1f4-4595-b26f-48b63d62eb78) | 管理表格中的条件格式和样式规则等规则。 |
| [外观](gcdocsite__documentlink?toc-item-id=a6e879d4-0b79-41bd-90d8-a9283a2d382e) | 自定义集算表的外观：<ul><li>[交替行样式](gcdocsite__documentlink?toc-item-id=a6e879d4-0b79-41bd-90d8-a9283a2d382e#%E4%BA%A4%E6%9B%BF%E8%A1%8C%E6%A0%B7%E5%BC%8F)</li><li>[图标](gcdocsite__documentlink?toc-item-id=a6e879d4-0b79-41bd-90d8-a9283a2d382e#%E5%9B%BE%E6%A0%87)</li><li>[主题](gcdocsite__documentlink?toc-item-id=a6e879d4-0b79-41bd-90d8-a9283a2d382e#%E4%B8%BB%E9%A2%98)</li></ul> |
| [计算](gcdocsite__documentlink?toc-item-id=1eebd4e9-c439-4928-ab22-57b36f4a9240) | 利用增强的计算引擎在工作表中添加计算列和参考集算表。 |
| [交互行为](gcdocsite__documentlink?toc-item-id=8866f8c5-a731-4482-b6ac-96f04b6c5935) | 与集算表的交互操作：<ul><li>[放大和缩小](gcdocsite__documentlink?toc-item-id=8866f8c5-a731-4482-b6ac-96f04b6c5935#%E6%94%BE%E5%A4%A7%E5%92%8C%E7%BC%A9%E5%B0%8F)</li><li>[调整列大小](gcdocsite__documentlink?toc-item-id=8866f8c5-a731-4482-b6ac-96f04b6c5935#%E8%B0%83%E6%95%B4%E5%88%97%E5%A4%A7%E5%B0%8F)</li><li>[剪切、复制和粘贴](gcdocsite__documentlink?toc-item-id=8866f8c5-a731-4482-b6ac-96f04b6c5935#%E5%89%AA%E5%88%87%E5%A4%8D%E5%88%B6%E5%92%8C%E7%B2%98%E8%B4%B4)</li><li>[拖拽操作](gcdocsite__documentlink?toc-item-id=8866f8c5-a731-4482-b6ac-96f04b6c5935#%E6%8B%96%E6%8B%BD%E6%93%8D%E4%BD%9C)</li><li>[快捷键](gcdocsite__documentlink?toc-item-id=8866f8c5-a731-4482-b6ac-96f04b6c5935#%E5%BF%AB%E6%8D%B7%E9%94%AE)</li></ul> |
| [集算表 IO](gcdocsite__documentlink?toc-item-id=800261ca-4d68-47ca-b924-042c08a92853) | 将集算表导出到不同的文件格式：<ul><li>[json序列化](gcdocsite__documentlink?toc-item-id=800261ca-4d68-47ca-b924-042c08a92853#json%E5%BA%8F%E5%88%97%E5%8C%96)</li><li>[导出Excel文件](gcdocsite__documentlink?toc-item-id=800261ca-4d68-47ca-b924-042c08a92853#%E5%AF%BC%E5%87%BAexcel%E6%96%87%E4%BB%B6)</li><li>[导出PDF](gcdocsite__documentlink?toc-item-id=800261ca-4d68-47ca-b924-042c08a92853#%E5%AF%BC%E5%87%BApdf)</li><li>[打印 Tablesheet](gcdocsite__documentlink?toc-item-id=800261ca-4d68-47ca-b924-042c08a92853#%E6%89%93%E5%8D%B0-tablesheet)</li></ul> |
