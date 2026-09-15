# modules-and-load-on-demand

SpreadJS 采用模块化设计。核心包提供工作簿、工作表、单元格、公式等基础能力；导入导出、图表、PDF、打印、数据透视表等能力通过独立插件包扩展。

本章节用于说明如何按实际功能需求选择模块。普通项目建议从核心包开始，按需补充插件；只有在需要精细控制包体积、脚本依赖或历史部署方式时，才使用独立模块打包或传统子库加载方案。

## 推荐路径

| 推荐阅读 | 使用场景 |
| ---- | ---- |
| [按需加载](gcdocsite__documentlink?toc-item-id=2d8b87cd-c71e-4b3e-96b5-e09c82d215fa) | 需要了解各功能对应哪些脚本或子库 |
| [独立模块打包](gcdocsite__documentlink?toc-item-id=52d21fa1-35df-4dfb-99d5-b3191806cc53) | 使用 Webpack、Vite、Rollup、ESBuild 等工具进行独立模块打包 |

## 常用功能包

| Package | Purpose |
| ------- | ------- |
| [@grapecity-software/spread-sheets](https://www.npmjs.com/package/@grapecity-software/spread-sheets) | SpreadJS 核心模组 |
| [@grapecity-software/spread-sheets-ai-addon](https://www.npmjs.com/package/@grapecity-software/spread-sheets-ai-addon) | SpreadJS AI 插件 |
| [@grapecity-software/spread-sheets-barcode](https://www.npmjs.com/package/@grapecity-software/spread-sheets-barcode) | SpreadJS 条形码 |
| [@grapecity-software/spread-sheets-calc-worker](https://www.npmjs.com/package/@grapecity-software/spread-sheets-calc-worker) | SpreadJS Web Worker 公式计算 |
| [@grapecity-software/spread-sheets-charts](https://www.npmjs.com/package/@grapecity-software/spread-sheets-charts) | SpreadJS 图表 |
| [@grapecity-software/spread-sheets-collaboration](https://www.npmjs.com/package/@grapecity-software/spread-sheets-collaboration) | SpreadJS 协同模组 |
| [@grapecity-software/spread-sheets-collaboration-addon](https://www.npmjs.com/package/@grapecity-software/spread-sheets-collaboration-addon) | SpreadJS 协同插件 |
| [@grapecity-software/spread-sheets-collaboration-client](https://www.npmjs.com/package/@grapecity-software/spread-sheets-collaboration-client) | SpreadJS 协同客户端 |
| [@grapecity-software/spread-sheets-datacharts-addon](https://www.npmjs.com/package/@grapecity-software/spread-sheets-datacharts-addon) | SpreadJS 数据图表插件 |
| [@grapecity-software/spread-sheets-formula-panel](https://www.npmjs.com/package/@grapecity-software/spread-sheets-formula-panel) | SpreadJS 公式面板 |
| [@grapecity-software/spread-sheets-ganttsheet](https://www.npmjs.com/package/@grapecity-software/spread-sheets-ganttsheet) | SpreadJS 甘特图 |
| [@grapecity-software/spread-sheets-io](https://www.npmjs.com/package/@grapecity-software/spread-sheets-io) | SpreadJS 文件导入导出 |
| [@grapecity-software/spread-sheets-languagepackages](https://www.npmjs.com/package/@grapecity-software/spread-sheets-languagepackages) | 语言本地化资源 |
| [@grapecity-software/spread-sheets-legacy-charts](https://www.npmjs.com/package/@grapecity-software/spread-sheets-legacy-charts) | SpreadJS 老版本图表 |
| [@grapecity-software/spread-sheets-pdf](https://www.npmjs.com/package/@grapecity-software/spread-sheets-pdf) | SpreadJS 导出 PDF |
| [@grapecity-software/spread-sheets-pivot-addon](https://www.npmjs.com/package/@grapecity-software/spread-sheets-pivot-addon) | SpreadJS 数据透视表插件 |
| [@grapecity-software/spread-sheets-print](https://www.npmjs.com/package/@grapecity-software/spread-sheets-print) | SpreadJS 打印 |
| [@grapecity-software/spread-sheets-reportsheet-addon](https://www.npmjs.com/package/@grapecity-software/spread-sheets-reportsheet-addon) | SpreadJS 报表插件 |
| [@grapecity-software/spread-sheets-shapes](https://www.npmjs.com/package/@grapecity-software/spread-sheets-shapes) | SpreadJS 形状 |
| [@grapecity-software/spread-sheets-slicers](https://www.npmjs.com/package/@grapecity-software/spread-sheets-slicers) | SpreadJS 切片器 |
| [@grapecity-software/spread-sheets-tablesheet](https://www.npmjs.com/package/@grapecity-software/spread-sheets-tablesheet) | SpreadJS 集算表 |


## 使用原则

1. 新项目优先使用 `@grapecity-software/spread-sheets` 作为核心依赖。
2. 根据业务功能补充插件包，不建议默认安装全部插件。
3. 图表、切片器、PDF 等功能存在依赖顺序要求，使用前请确认对应插件已正确导入。
4. 独立模块打包属于高级用法，不应与完整核心包随意混用。

示例：

```js
import * as GC from '@grapecity-software/spread-sheets'
import '@grapecity-software/spread-sheets/styles/gc.spread.sheets.excel2013white.css'

import '@grapecity-software/spread-sheets-io'
```

上例在核心工作表能力的基础上增加了文件导入导出能力。