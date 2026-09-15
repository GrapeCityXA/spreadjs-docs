# visualization

本子分类介绍 SpreadJS 中将数据以图形化方式直观呈现的功能，包括图表、迷你图、形状、条件格式、主题等。这些功能帮助用户快速洞察数据规律、突出关键信息，并打造美观的表格界面。

### 图表类功能

| 功能 | 说明 |
| --- | --- |
| **[图表（Chart）](gcdocsite__documentlink?toc-item-id=a6f67d69-f79a-4bbb-94ad-4e98e90fb131)** | 基于工作表数据的柱状图、折线图、饼图、散点图等完整图表体系，与 Excel 图表高度兼容。 |
| **[迷你图（Sparkline）](gcdocsite__documentlink?toc-item-id=cb868062-f015-4990-95ff-fe45869b1c95)** | 嵌入单个单元格内的微型图表，适合在行数据旁快速展示趋势。 |
| **[数据图表（DataChart）](gcdocsite__documentlink?toc-item-id=8a01b66f-3b2c-4ef1-997a-0fcce372b466)** | 基于 DataManager 数据的图表，区别于普通工作表图表，适用于数据驱动场景。 |

### 图形与对象

| 功能 | 说明 |
| --- | --- |
| **[形状（Shape）](gcdocsite__documentlink?toc-item-id=084f2f1b-fd62-4580-b940-7205e6cc01ba)** | 矩形、箭头、流程图等内置形状，支持自定义绘制。 |
| **[浮动对象（Floating Object）](gcdocsite__documentlink?toc-item-id=24300fdc-eb2c-415f-9613-e74e13ec8a03)** | 图片、自定义 DOM 元素等浮动在工作表上的对象。 |
| **[条形码（Barcode）](gcdocsite__documentlink?toc-item-id=df415171-6213-4973-a307-ed986b8b0ad2)** | 生成各类一维条码与二维码（二维码依赖条形码插件）。 |

### 格式与样式增强

| 功能 | 说明 |
| --- | --- |
| **[条件格式](gcdocsite__documentlink?toc-item-id=20b6493c-9018-4894-b54f-5315b31ad436)** | 根据单元格的值或公式自动应用格式（如数据条、色阶、图标集），直观展示数据分布。 |
| **[主题](gcdocsite__documentlink?toc-item-id=69ff341a-6352-4a7c-b82e-8ee092aedf98)** | SpreadJS 提供多种预设主题，并支持基于 ThemeRoller 创建自定义主题，统一控制整个工作簿的配色与字体。 |

### 依赖关系提示

以下功能依赖 `shapes` 插件，引入时请注意加载顺序：

* 图表（依赖 `charts` 插件，`charts` 依赖 `shapes`）
* 切片器（依赖 `slicers` 插件，`slicers` 依赖 `shapes`）
* 形状本身（`shapes` 插件）

```js
// 正确的导入顺序：先 shapes，再 charts 和 slicers
import '@grapecity-software/spread-sheets-shapes'
import '@grapecity-software/spread-sheets-charts'
import '@grapecity-software/spread-sheets-slicers'
```