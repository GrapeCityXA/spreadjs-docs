# SpreadJS 产品文档

这个仓库是 SpreadJS 中文产品文档的 Markdown 版本，方便开发者和 AI Agent 直接检索、引用和离线阅读。

| 目录 | 文档数 | 说明 |
| --- | --- | --- |
| [`v19.1/`](v19.1/) | 1354 篇 | 19.1 版本，当前最新 |
| [`v19.0/`](v19.0/) | 1297 篇 | 19.0 版本 |

正文为中文。仓库**不含图片资源**，也**不含方法级 API 文档**，这两点的原因写在[「已知限制」](#已知限制)里。

[English ↓](#english)

---

## SpreadJS 是什么

SpreadJS 是运行在浏览器端的类 Excel 电子表格控件。把它嵌进 Web 应用，用户就获得了表格编辑、数据录入、公式计算、样式设置、Excel 导入导出和数据可视化这些能力。

核心对象模型只有三层：

```text
Workbook -> Worksheet -> Range / Cell
```

一个页面创建一个 `Workbook`，工作簿里包含多个 `Worksheet`，绝大多数数据、公式和样式操作都落在单元格或区域上。

| | |
| --- | --- |
| 产品主页 | https://www.grapecity.com.cn/developer/spreadjs |
| 在线文档 | https://demo.grapecity.com.cn/spreadjs/help/docs/ |
| API 参考 | https://demo.grapecity.com.cn/spreadjs/help/api/ |
| 在线示例 | https://demo.grapecity.com.cn/spreadjs/SpreadJSTutorial/ |
| NPM | [`@grapecity-software/spread-sheets`](https://www.npmjs.com/package/@grapecity-software/spread-sheets) |

## 目录怎么组织的

两个版本文件夹的内部结构直接对应文档站的目录树：

- **顶层文件夹**是一级章节，前缀数字是阅读顺序，例如 `2.产品功能`
- **叶子文档**命名为 `{顺序}.{标题}.md`
- **章节自身的正文**（章节概述页）有两个位置：`{顺序}.{标题}/index.md`，或者与文件夹同级的 `{顺序}.{标题}.md`。两种写法都在用，找某一章的概述页时两处都看一眼
- **每篇文档的第一行**是 `# 英文-slug`，不是它的中文标题。例如工作表那篇的开头是 `# work-with-worksheets`。这个 slug 可以当英文关键词用

单篇平均 3 KB 左右，最长的（报表模板的基本函数）约 130 KB。

## 各章节速查（v19.1）

| 目录 | 篇数 | 里面有什么 |
| --- | --- | --- |
| `0.新手入门` | 7 | 产品概述与适用场景、快速开始（Vite + NPM）、试用与许可、最终用户许可协议、FAQs |
| `1.开发指南` | 38 | Vue / React / Angular / NextJS / NuxtJS 集成、TypeScript、按需加载、独立模块打包（Webpack / Vite / Rollup / ESBuild 等）、兼容性与运行环境、性能优化、移动端与触控、无障碍、CSP |
| `2.产品功能` | 492 | 核心概念（工作簿、工作表、行列、单元格、数据绑定、键盘行为、文化）；数据处理与分析（数据管理器、集算表、甘特表、报表、数据透视表、排序、筛选、分组、假设分析）；可视化（图表、迷你图、数据图表、形状、浮动对象、条件格式、主题）；文件操作（导入导出 Excel / CSV / JSON、导出 PDF、打印、JSON Schema）；AI 助手 |
| `3.设计器（工具栏）` | 94 | 设计器组件：主题、界面、定制、工具栏功能区、打印、JavaScript 框架、桌面端应用 |
| `4.协同编辑` | 65 | 协同快速开始、功能配置、协同原理与机制（js-collaboration 系列底层框架）、开发参考、附录 |
| `5.公式` | 589 | 公式概述、公式使用（增量计算、语言包、工作表之外计算公式）；**公式函数 542 篇**，一个函数一篇，按类别分目录（数学与三角函数、查找与引用、财务、统计、日期和时间、文本、工程、信息、逻辑、正则、Web、条形码等） |
| `6.VSCode 插件.md` | 1 | 在 VSCode 里直接编辑 `.sjs` / `.xlsx` / `.csv` 等文件的插件 |
| `7.API 与参考` | 68 | API 索引（命名空间级）、各版本发布说明（19.x 回溯到 10.x） |

`v19.0/` 是上一代目录结构，章节划分不同（`4.产品特性`、`9.公式引用`、`6.设计器组件`、`10.导入导出参考`、`14.发布说明` 等），内容大体对应。**19.1 的项目看 `v19.1/`，19.0 的项目看 `v19.0/`**；两边的发布说明都能覆盖到 19.0。

## 怎么读

第一次上手，按这个顺序：

1. [`v19.1/0.新手入门/0.概述.md`](v19.1/0.新手入门/0.概述.md) — 弄清楚产品边界，哪些场景不适合用
2. [`v19.1/0.新手入门/1.快速开始/index.md`](v19.1/0.新手入门/1.快速开始/index.md) — 跑起来一个最小示例
3. [`v19.1/1.开发指南/0.框架集成/`](v19.1/1.开发指南/0.框架集成/) — 按你用的框架进对应的一篇
4. 之后按需查 `2.产品功能` 或 `5.公式`

想全量搜索的话，clone 下来用 ripgrep 比在 GitHub 网页上点更快：

```bash
git clone <repo-url>
rg "工作表保护" v19.1/           # 按中文标题找
rg "work-with-worksheets" v19.1/  # 按英文 slug 找
rg "SUMIF" v19.1/5.公式/          # 找某个函数
```

## 已知限制

这三条会直接影响引用和检索，用之前先知道。

### 1. 站内链接全部失效

约 2416 处，分布在 475 个文件里，形如：

```markdown
您可以使用 [Workbook.addSheet](gcdocsite__documentlink?toc-item-id=8a4039d6-22a0-4e4c-81a6-dd3e37d185b0#addSheet) 方法将工作表添加到工作簿。
```

`toc-item-id` 是文档站的内部标识，仓库里没有对应的映射文件，链接点不开。但链接的两部分仍然有信息量：

- 链接文字 `Workbook.addSheet` 是目标文档的标题，拿它反查文件名或正文能定位到目标
- URL 片段 `#addSheet` 是目标 API 成员名

### 2. 图片不在仓库里

约 2214 处，分布在 535 个文件里，形如：

```markdown
![image](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/0f73f140-.../image-20260526.png?width=800)
```

`DOCUMENT_SITE_LINK_PREFIX_HERE` 是发布时替换的占位符。代码示例和文字说明都完整，纯文字章节不受影响；依赖截图或示意图的章节（图表、形状、设计器界面、条件格式效果）需要对照[在线文档](https://demo.grapecity.com.cn/spreadjs/help/docs/)看。

### 3. 没有方法级 API 文档

[`v19.1/7.API 与参考/0.API 索引.md`](v19.1/7.API%20与参考/0.API%20索引.md) 只列到命名空间一级，比如 `GC.Spread.Sheets.Charts`，后面就没有类、方法、参数和返回值了。

查具体 API 签名，用在线 API 参考：https://demo.grapecity.com.cn/spreadjs/help/api/

## 给 AI Agent 的检索说明

### 定位顺序

1. **先按章节路由**，别一上来就全库满量搜索。上面的[各章节速查](#各章节速查v191)表基本能直接定位到目录
2. **再在目录里搜关键词**。中文标题和正文用中文词搜，`#` 开头的英文 slug 用英文词搜
3. **公式问题**请直接定位到 `v19.1/5.公式/2.公式函数/{类别}/{序号}.{函数名}.md`。这些文件很短，每篇是固定的「说明 / 语法 / 参数 / 注释」结构，适合整篇读
4. **API 签名问题仓库里答不了**，指给用户在线 API 参考，不要根据正文的代码示例反推签名

### 引用格式

引用时给**文件路径 + 标题**，不要给 `toc-item-id`：

```
来源：v19.1/2.产品功能/1.核心概念/1.工作表/0.使用工作表.md
```

### 别做的事

- 不要试着解析或还原 `gcdocsite__documentlink` 里的 UUID，仓库内没有任何东西能把它映射到文件
- 不要假设图片存在，也不要在回答里引用图片内容
- 这三个版本文件夹的结构不一样，跨版本引用时不要套用同一套路径

### 给 Agent 的开场说明（可复制）

```text
你可以在本地仓库 <path> 里查 SpreadJS 产品文档。规则：

- 文档按版本分目录：v19.1/（最新，优先用）、v19.0/（旧版结构）
- 目录结构对应文档树：{序号}.{标题}/ 是章节，{序号}.{标题}.md 是叶子文档，
  章节概述页在 {序号}.{标题}/index.md 或同级的 {序号}.{标题}.md
- 每篇第一行是英文 slug（如 # work-with-worksheets），不是中文标题
- 公式函数一篇一个文件，在 v19.1/5.公式/2.公式函数/{类别}/ 下

已知缺陷，注意避开：
- 站内链接形如 [文字](gcdocsite__documentlink?toc-item-id=<uuid>) 全部失效，
  不要尝试打开。链接文字是目标标题，可用它反查文件
- 图片形如 ![...](/DOCUMENT_SITE_LINK_PREFIX_HERE/...) 缺失，内容不可见
- 没有方法级 API 文档，只有命名空间索引。API 签名问题请回答"仓库内无此信息"

引用时给出文件路径，不要给 toc-item-id。
```

## 版权与许可

文档内容的版权归西安葡萄城软件有限公司所有。仓库中不含开源许可证声明；如需转载或商用文档内容，请遵循葡萄城的许可条款。

SpreadJS 是商业控件，使用需购买许可。评估版会在右下角显示水印，授权的配置方式见 [`v19.1/0.新手入门/2.试用版和许可信息.md`](v19.1/0.新手入门/2.试用版和许可信息.md)，完整条款见 [`v19.1/0.新手入门/3.最终用户许可协议.md`](v19.1/0.新手入门/3.最终用户许可协议.md)。

---

<a id="english"></a>

# SpreadJS Product Documentation

This repository holds the Markdown source of the SpreadJS Chinese product documentation, so that developers and AI agents can search, cite, and read it offline.

| Directory | Documents | Notes |
| --- | --- | --- |
| [`v19.1/`](v19.1/) | 1354 | Version 19.1, current |
| [`v19.0/`](v19.0/) | 1297 | Version 19.0 |

**The documentation text is in Chinese.** The repository contains **no images** and **no method-level API reference** — see [Known limitations](#known-limitations) for why.

## What SpreadJS is

SpreadJS is a browser-based, Excel-like spreadsheet component. Embed it in a web application and your users get grid editing, data entry, formula calculation, styling, Excel import/export, and data visualization.

The core object model has three levels:

```text
Workbook -> Worksheet -> Range / Cell
```

One `Workbook` per page, multiple `Worksheet`s inside it, and nearly all data, formula, and style operations happen on cells or ranges.

| | |
| --- | --- |
| Product home | https://www.grapecity.com.cn/developer/spreadjs |
| Online docs | https://demo.grapecity.com.cn/spreadjs/help/docs/ |
| API reference | https://demo.grapecity.com.cn/spreadjs/help/api/ |
| Online demos | https://demo.grapecity.com.cn/spreadjs/SpreadJSTutorial/ |
| NPM | [`@grapecity-software/spread-sheets`](https://www.npmjs.com/package/@grapecity-software/spread-sheets) |

## How the tree is organized

Each version directory mirrors the doc site's table of contents:

- A **top-level folder** is a first-level section; the numeric prefix is reading order, e.g. `2.产品功能`
- A **leaf document** is named `{order}.{title}.md`
- A **section's own text** (its overview page) lives in one of two places: `{order}.{title}/index.md`, or a sibling `{order}.{title}.md`. Both conventions are in use, so check both when you want a section overview
- The **first line of every file** is `# english-slug`, not the Chinese title. The worksheet doc, for instance, opens with `# work-with-worksheets`. Useful as an English search key

Documents average about 3 KB; the largest single file (report template functions) is around 130 KB.

## Section map (v19.1)

| Directory | Docs | Contents |
| --- | --- | --- |
| `0.新手入门` | 7 | Product overview and scope, quick start (Vite + NPM), trial and licensing, EULA, FAQs |
| `1.开发指南` | 38 | Vue / React / Angular / NextJS / NuxtJS integration, TypeScript, on-demand loading, standalone module bundling (Webpack / Vite / Rollup / ESBuild), environment compatibility, performance tuning, mobile and touch, accessibility, CSP |
| `2.产品功能` | 492 | Core concepts (workbook, worksheet, rows and columns, cells, data binding, keyboard behavior, culture); data processing and analysis (DataManager, TableSheet, GanttSheet, ReportSheet, PivotTable, sorting, filtering, grouping, what-if analysis); visualization (charts, sparklines, DataChart, shapes, floating objects, conditional formatting, themes); file operations (Excel / CSV / JSON import and export, PDF export, printing, JSON Schema); AI assistant |
| `3.设计器（工具栏）` | 94 | Designer component: themes, UI, customization, toolbar ribbon, printing, JavaScript frameworks, desktop app |
| `4.协同编辑` | 65 | Collaboration quick start, configuration, mechanics (the js-collaboration stack), development reference, appendix |
| `5.公式` | 589 | Formula overview and usage (incremental calculation, language packages, calculating outside a worksheet); **542 individual function pages**, one per function, grouped by category (math and trig, lookup and reference, financial, statistical, date and time, text, engineering, information, logical, regex, web, barcode, and more) |
| `6.VSCode 插件.md` | 1 | Editing `.sjs` / `.xlsx` / `.csv` files inside VS Code |
| `7.API 与参考` | 68 | API index (namespace level) and release notes for 19.x back through 10.x |

`v19.0/` uses the previous IA, with different section names (`4.产品特性`, `9.公式引用`, `6.设计器组件`, `10.导入导出参考`, `14.发布说明`, …) covering roughly the same ground. **For a 19.1 project read `v19.1/`; for a 19.0 project read `v19.0/`.** Release notes on either side cover 19.0.

## Reading it

For a first pass:

1. [`v19.1/0.新手入门/0.概述.md`](v19.1/0.新手入门/0.概述.md) — what the product does and, just as usefully, what it doesn't
2. [`v19.1/0.新手入门/1.快速开始/index.md`](v19.1/0.新手入门/1.快速开始/index.md) — a minimal working example
3. [`v19.1/1.开发指南/0.框架集成/`](v19.1/1.开发指南/0.框架集成/) — the page for your framework
4. Then `2.产品功能` or `5.公式` as needed

To search the whole corpus, clone and use ripgrep — faster than clicking around on GitHub:

```bash
git clone <repo-url>
rg "工作表保护" v19.1/           # by Chinese title
rg "work-with-worksheets" v19.1/  # by English slug
rg "SUMIF" v19.1/5.公式/          # a specific function
```

## Known limitations

These three affect citation and retrieval directly.

### 1. Every internal link is dead

Roughly 2,416 occurrences across 475 files, like this:

```markdown
您可以使用 [Workbook.addSheet](gcdocsite__documentlink?toc-item-id=8a4039d6-22a0-4e4c-81a6-dd3e37d185b0#addSheet) 方法将工作表添加到工作簿。
```

`toc-item-id` is an identifier internal to the doc site, and nothing in this repository maps it to a file, so the link goes nowhere. Two parts are still informative:

- The link text (`Workbook.addSheet`) is the target document's title — search filenames or body text for it
- The URL fragment (`#addSheet`) is the target API member name

### 2. Images are not in the repository

Roughly 2,214 occurrences across 535 files:

```markdown
![image](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/0f73f140-.../image-20260526.png?width=800)
```

`DOCUMENT_SITE_LINK_PREFIX_HERE` is a placeholder substituted at publish time. Code samples and prose are complete, so text-heavy sections stand on their own; sections that lean on screenshots (charts, shapes, designer UI, conditional formatting results) need the [online docs](https://demo.grapecity.com.cn/spreadjs/help/docs/).

### 3. No method-level API reference

[`v19.1/7.API 与参考/0.API 索引.md`](v19.1/7.API%20与参考/0.API%20索引.md) stops at the namespace level — `GC.Spread.Sheets.Charts` and similar — with no classes, methods, parameters, or return types.

For actual API signatures, use the online API reference: https://demo.grapecity.com.cn/spreadjs/help/api/

## Notes for AI agents

### How to locate things

1. **Route by section first.** The [section map](#section-map-v191) above usually narrows it to one directory — no need to search the whole corpus up front
2. **Then grep within that directory.** Chinese terms match titles and body text; English terms match the `#` slug line
3. **Formula questions**: go straight to `v19.1/5.公式/2.公式函数/{category}/{order}.{name}.md`. These are short files with a fixed structure (description / syntax / parameters / remarks), safe to read whole
4. **API signature questions cannot be answered from this repository.** Point the user at the online API reference rather than inferring a signature from a code sample

### Citing

Give the **file path plus the heading**, never the `toc-item-id`:

```
Source: v19.1/2.产品功能/1.核心概念/1.工作表/0.使用工作表.md
```

### Don't

- Don't try to resolve or reverse-engineer the UUIDs in `gcdocsite__documentlink` — nothing in the repository maps them to files
- Don't assume images are available, and don't cite their contents
- The two version directories have different structures — don't reuse one version's paths for the other

### Starter prompt for an agent (copy-paste)

```text
You have the SpreadJS product documentation in a local repository at <path>. Rules:

- Docs are split by version: v19.1/ (current, prefer it), v19.0/ (older IA)
- The tree mirrors the doc TOC: {order}.{title}/ is a section, {order}.{title}.md is a
  leaf document, and a section's overview page is either {order}.{title}/index.md or a
  sibling {order}.{title}.md
- The first line of each file is an English slug (e.g. # work-with-worksheets), not the
  Chinese title
- Formula functions are one file each under v19.1/5.公式/2.公式函数/{category}/

Known defects to avoid:
- Internal links like [text](gcdocsite__documentlink?toc-item-id=<uuid>) are all dead;
  don't try to open them. The link text is the target title — search for it instead
- Images like ![...](/DOCUMENT_SITE_LINK_PREFIX_HERE/...) are missing; their content is
  not visible to you
- There is no method-level API reference, only a namespace index. For API signatures,
  answer that the information is not in the repository

When citing, give the file path — not a toc-item-id.
```

## Copyright and licensing

The documentation content is copyright © Xi'an GrapeCity Software Co., Ltd. (西安葡萄城软件有限公司). No open-source license is declared for this repository; to redistribute or commercially use the documentation content, follow GrapeCity's terms.

SpreadJS itself is a commercial component and requires a purchased license. The evaluation build shows a watermark in the bottom-right corner. See [`v19.1/0.新手入门/2.试用版和许可信息.md`](v19.1/0.新手入门/2.试用版和许可信息.md) for license configuration and [`v19.1/0.新手入门/3.最终用户许可协议.md`](v19.1/0.新手入门/3.最终用户许可协议.md) for the full terms.
