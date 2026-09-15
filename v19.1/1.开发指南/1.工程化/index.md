# engineering

本章节介绍在工程化项目中使用 SpreadJS 时常见的配置主题，包括 TypeScript 支持、模块与按需加载、传统脚本集成以及 NPM 包迁移。

对于大多数现代前端项目，建议优先使用 NPM 包和 ES Module 方式集成 SpreadJS。只有在无构建工具、历史项目维护或需要精细控制打包产物时，再参考 UMD、独立模块打包等主题。

## 本章节内容

| 主题 | 说明 |
| --- | --- |
| [使用 TypeScript](gcdocsite__documentlink?toc-item-id=f6ba0c08-0072-4754-80bc-b41ba2c081d2) | 在 TypeScript 项目中使用 SpreadJS，并获得类型提示和编译期检查。 |
| [模块与按需加载](gcdocsite__documentlink?toc-item-id=9c1e1946-dd34-49fa-a3ff-b78f676ace18) | 了解核心包、功能插件、资源包以及高级独立模块打包方式。 |
| [UMD 支持](gcdocsite__documentlink?toc-item-id=765c68fa-90be-41dc-98f7-c4ef04968e6b) | 在无构建工具或传统 `<script>` 引入场景中使用 SpreadJS。 |
| [NPM 包迁移指南](gcdocsite__documentlink?toc-item-id=b37b6fc0-f5cc-4850-87bc-ba22876fd346) | 将旧命名空间下的包迁移到 `@grapecity-software` 命名空间。 |

## 选择建议

如果您正在创建新的 React、Vue、Angular、NextJS 或 NuxtJS 项目，请优先阅读对应的[框架集成](gcdocsite__documentlink?toc-item-id=94da5d60-da19-4b25-b2a0-5451a909910b)文档，再根据需要阅读本章节。

如果项目只需要基础工作表能力，通常只需安装核心包：

```bash
npm install @grapecity-software/spread-sheets
```

如果需要导入导出、图表、PDF、数据透视表等能力，再按功能补充对应插件包。不要在需求不明确时一次性引入所有插件。