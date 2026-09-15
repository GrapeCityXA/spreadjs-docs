# develop-guide

本章节面向准备在项目中集成、配置和优化 SpreadJS 的开发人员，内容涵盖框架集成、工程化配置、平台适配、性能优化以及开发参考资料。

阅读本章节前，建议先完成“新手入门”中的快速开始内容，并确认已经可以在本地运行一个最小 SpreadJS 示例。

## 基础集成

SpreadJS 的核心对象模型为 `Workbook -> Worksheet -> Range/Cell`。在现代前端项目中，建议优先使用 NPM 包和 ES Module 方式集成。

```bash
npm install @grapecity-software/spread-sheets
```

```js
import * as GC from '@grapecity-software/spread-sheets'
import '@grapecity-software/spread-sheets/styles/gc.spread.sheets.excel2013white.css'

const spread = new GC.Spread.Sheets.Workbook(document.getElementById('ss'))
spread.getActiveSheet().setValue(0, 0, 'Hello SpreadJS')
```

## 本章节内容

| 目录 | 说明 |
| --- | --- |
| [框架集成](gcdocsite__documentlink?toc-item-id=94da5d60-da19-4b25-b2a0-5451a909910b) | 在 Vue、React、Angular、NextJS、NuxtJS 等项目中使用 SpreadJS。 |
| [工程化](gcdocsite__documentlink?toc-item-id=f0289506-981c-4e06-9d66-8d5e5c052672) | TypeScript、模块与按需加载、UMD 支持、NPM 包迁移等工程配置主题。 |
| [平台与质量](gcdocsite__documentlink?toc-item-id=ff8a46a1-0124-4965-8805-6cae02c80f41) | 性能优化、移动端与触控、无障碍支持等运行质量主题。 |
| [开发参考](gcdocsite__documentlink?toc-item-id=84109c8f-e3a6-48fa-bf91-8b4465e07d8a) | 第三方依赖、样式继承与优先级等参考资料。 |

## 阅读建议

如果您正在接入具体框架，请先阅读“框架集成”中对应的框架文档。

如果您需要控制包体积、迁移旧包名、使用 TypeScript 或传统脚本方式，请阅读“工程化”。

如果您的项目涉及大数据量、移动端访问、辅助技术访问或上线前性能验证，请阅读“平台与质量”。

如果您需要准备开源合规材料，或需要理解样式继承规则，请阅读“开发参考”。