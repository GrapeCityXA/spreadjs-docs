# SpreadJS Product Documentation

English | [中文](README.md)

This repository holds the Markdown version of the SpreadJS Chinese product documentation, so that developers and AI agents can search, cite, and read it offline. **The documentation text is in Chinese.**

It contains the complete product documentation but **no images**, and **no method-level API reference** — that part is open-sourced separately at `spreadjs-api-reference` (see Related repositories below). To look up a class, method, parameter, or return type, go there.

## Related repositories

| Repository | Contents |
| --- | --- |
| [spreadjs-docs](https://github.com/GrapeCityXA/spreadjs-docs) | Product documentation: guides, feature reference, formula functions, split by version (this repository) |
| [spreadjs-api-reference](https://github.com/GrapeCityXA/spreadjs-api-reference) | API reference: complete TypeDoc-generated symbol docs, split by version |
| [spreadjs-practice-samples](https://github.com/GrapeCityXA/spreadjs-practice-samples) | Practice samples: runnable example projects grouped by scenario |

## Version directories

| Directory | Notes |
| --- | --- |
| [`v19.1/`](v19.1/) | 1354 documents. Restructured layout, current |
| [`v19.0/`](v19.0/) | 1297 documents. Pre-restructure layout |
| [`v18.2/`](v18.2/) [`v18.1/`](v18.1/) [`v18.0/`](v18.0/) [`v17.1/`](v17.1/) [`v17.0/`](v17.0/) | Same structure as v19.0 |

### Where the two layouts split

Starting with **19.1** the product documentation was restructured: sections were redrawn and material that used to be scattered is now grouped by topic. **19.0 and earlier** (18.x, 17.x) keep the pre-restructure layout, and those versions differ from each other only slightly.

Pick the directory matching your project's version. If you just want to know where a topic lives, use this map:

| Topic | 19.1 | 19.0 and earlier |
| --- | --- | --- |
| Product overview | `0.新手入门/0.概述.md` | `0.SpreadJS 概述.md` |
| Quick start | `0.新手入门/1.快速开始/` | `1.快速开始/` |
| Framework integration | `1.开发指南/0.框架集成/` | `2.框架中开发/` |
| Performance tuning | `1.开发指南/2.平台与质量/1.性能优化/` | `3.最佳实践/` |
| Mobile and touch | `1.开发指南/2.平台与质量/2.移动端与触控.md` | `8.移动端与触控/` |
| Product features | `2.产品功能/` | `4.产品特性/` |
| Designer component | `3.设计器（工具栏）/` | `6.设计器组件/` |
| Desktop app | `3.设计器（工具栏）/11.桌面端应用/` | `5.桌面端应用/` |
| Collaboration | `4.协同编辑/` | `7.SpreadJS 协同编辑/` |
| Formulas and functions | `5.公式/` | `9.公式引用/` |
| Import and export | `2.产品功能/4.文件操作/` | `10.导入导出参考/` |
| Common events | not included in 19.1 | `11.常用事件.md` |
| API index | `7.API 与参考/0.API 索引.md` | `12.API 索引.md` |
| Release notes | `7.API 与参考/2.发布说明/` | `14.发布说明/` |
| VS Code extension | `6.VSCode 插件.md` | none |

"Common events" is a chapter the restructure dropped; in 19.1 event examples are spread across the individual feature chapters. For a concentrated view of event usage, read `v19.0/11.常用事件.md`.

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
| API reference (online) | https://demo.grapecity.com.cn/spreadjs/help/api/ |
| Online demos | https://demo.grapecity.com.cn/spreadjs/SpreadJSTutorial/ |
| NPM | [`@grapecity-software/spread-sheets`](https://www.npmjs.com/package/@grapecity-software/spread-sheets) |

## How the tree is organized

Each version directory mirrors the doc site's table of contents:

- A **top-level folder** is a first-level section; the numeric prefix is reading order, e.g. `2.产品功能`
- A **leaf document** is named `{order}.{title}.md`
- A **section's own text** (its overview page) lives in one of two places: `{order}.{title}/index.md`, or a sibling `{order}.{title}.md`. Both conventions are in use, so check both when you want a section overview
- The **first line of every file** is `# english-slug`, not the Chinese title. The worksheet doc, for instance, opens with `# work-with-worksheets`. Useful as an English search key
- **Numbers are not always contiguous.** Gaps are normal; trust the actual directories

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

## Section map (v19.0 and earlier)

19.0 is laid out as follows; 18.x and 17.x match it:

| Directory | Docs | Contents |
| --- | --- | --- |
| `0.SpreadJS 概述.md` | 1 | Product positioning, object model, use cases |
| `1.快速开始` | 13 | Scaffolding a project, runtime environment, component libraries, TypeScript, UMD support, object inheritance, third-party dependencies, accessibility, NPM package migration, trial and licensing, EULA, FAQs |
| `2.框架中开发` | 38 | Vue, React, Angular, AngularJS, Breeze, Knockout, NextJS, NuxtJS, standalone module bundling |
| `3.最佳实践` | 8 | Suspending and resuming paint, bulk formulas, bulk data, avoiding volatile functions, suspending event listeners, suspending the dirty-flag mechanism, incremental loading, simplifying complex formulas |
| `4.产品特性` | 447 | Workbook, worksheet, rows and columns, cells, data binding, DataManager, TableSheet, GanttSheet, ReportSheet, DataChart, data validation, conditional formatting, sorting, grouping, formulas, serialization, keyboard behavior, shapes, form controls, floating objects, barcodes, charts, sparklines, tables, PivotTable, slicers, printing, themes, user management, culture, AI assistant |
| `5.桌面端应用` | 3 | Launching the designer, opening and saving files |
| `6.设计器组件` | 76 | Quick start, themes, UI, JavaScript frameworks, customization, toolbar ribbon, printing, API documentation |
| `7.SpreadJS 协同编辑` | 56 | Collaboration fundamentals, the collaboration framework, performance report, glossary, authorization |
| `8.移动端与触控` | 1 | Selection |
| `9.公式引用` | 564 | Formula overview, function reference (540 pages) |
| `10.导入导出参考` | 23 | Excel import/export, PDF export, CSV, JSON, exporting a range to HTML |
| `11.常用事件` | 1 | Code samples for events (cell click, clipboard change, and others) |
| `12.API 索引.md` | 1 | Namespace-level API index |
| `14.发布说明` | 61 | Release notes for each version (19.0 back through 9.x) |

## The API documentation lives in another repository

This repository's API material is a namespace-level index only (`7.API 与参考/0.API 索引.md`). It stops at levels like `GC.Spread.Sheets.Charts` — no classes, methods, parameters, or return types.

The complete API reference is here: **https://github.com/GrapeCityXA/spreadjs-api-reference**

That documentation is generated by TypeDoc from source comments, is plain Markdown, and is likewise split into version directories covering v17.0 through v19.1 (its README also lists v16.2). Each version holds four trees — `modules/`, `classes/`, `interfaces/`, `enums/` — plus `designer/`, `excelio/`, and `collaboration/` subtrees (`collaboration/` exists from v18.0 onward). The prose is in Chinese; signatures, type names, and code examples are language-neutral.

A few usage notes:

- Don't build paths from class names. Filenames usually equal the fully qualified name, but TypeDoc appends `-1` on collisions (23 such files). Use `find` or `grep` to locate first
- For a cheap overview, start with the relevant version's entry file under `modules/`
- Every version ships a `toc.json`, which suits browsing structure rather than precise lookup: `Text` and `DisplayName` are not unique keys, and entries marked `"file"` have no corresponding file

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

These two affect citation and retrieval directly.

### 1. Every internal link is dead

Roughly 2,416 occurrences across 475 files, like this:

```markdown
您可以使用 [Workbook.addSheet](gcdocsite__documentlink?toc-item-id=8a4039d6-22a0-4e4c-81a6-dd3e37d185b0#addSheet) 方法将工作表添加到工作簿。
```

`toc-item-id` is an identifier internal to the doc site, and nothing in this repository maps it to a file, so the link goes nowhere. Two parts are still informative:

- The link text (`Workbook.addSheet`) is the target document's title — search filenames or body text for it
- The URL fragment (`#addSheet`) is the target API member name, which you can look up in [GrapeCityXA/spreadjs-api-reference](https://github.com/GrapeCityXA/spreadjs-api-reference)

### 2. Images are not in the repository

Roughly 2,214 occurrences across 535 files:

```markdown
![image](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/0f73f140-.../image-20260526.png?width=800)
```

`DOCUMENT_SITE_LINK_PREFIX_HERE` is a placeholder substituted at publish time. Code samples and prose are complete, so text-heavy sections stand on their own; sections that lean on screenshots (charts, shapes, designer UI, conditional formatting results) need the [online docs](https://demo.grapecity.com.cn/spreadjs/help/docs/).

## Notes for AI agents

### How to locate things

1. **Route by section first.** The section maps above usually narrow it to one directory — no need to search the whole corpus up front
2. **Then grep within that directory.** Chinese terms match titles and body text; English terms match the `#` slug line
3. **Formula questions**: go straight to `v19.1/5.公式/2.公式函数/{category}/{order}.{name}.md`. These are short files with a fixed structure (description / syntax / parameters / remarks), safe to read whole
4. **API signature questions go to the spreadjs-api-reference repository** — don't infer a signature from a code sample here. If the question is about an older version, use that version's directory there
5. **Cross-version questions**: 19.1 and 19.0 paths are not interchangeable. Establish which version the user is on, then pick the directory. With no version stated, prefer 19.1

### Citing

Give the **file path plus the heading**, never the `toc-item-id`:

```
Source: v19.1/2.产品功能/1.核心概念/1.工作表/0.使用工作表.md
```

### Don't

- Don't try to resolve or reverse-engineer the UUIDs in `gcdocsite__documentlink` — nothing in the repository maps them to files
- Don't assume images are available, and don't cite their contents
- Don't apply 19.1 section paths to 19.0 or earlier

### Starter prompt for an agent (copy-paste)

```text
You have the SpreadJS product documentation in a local repository at <path>, and the API
reference in another repository at <api-path>.

Product documentation rules:
- Split by version: v19.1/ (restructured layout, prefer it), v19.0/ (older layout; 18.x and
  17.x match it)
- The tree mirrors the doc TOC: {order}.{title}/ is a section, {order}.{title}.md is a leaf
  document, and a section's overview page is either {order}.{title}/index.md or a sibling
  {order}.{title}.md
- The first line of each file is an English slug (e.g. # work-with-worksheets), not the
  Chinese title
- Formula functions are one file each under v19.1/5.公式/2.公式函数/{category}/
- 19.1 has no "common events" chapter; for event samples read v19.0/11.常用事件.md

Known defects to avoid:
- Internal links like [text](gcdocsite__documentlink?toc-item-id=<uuid>) are all dead;
  don't try to open them. The link text is the target title — search for it instead
- Images like ![...](/DOCUMENT_SITE_LINK_PREFIX_HERE/...) are missing; their content is not
  visible to you
- This repository has no method-level API reference, only a namespace index. For API
  signatures, use the API repository

When citing, give the file path — not a toc-item-id.
```

## Copyright and licensing

The documentation content is copyright © Xi'an GrapeCity Software Co., Ltd. (西安葡萄城软件有限公司). No open-source license is declared for this repository; to redistribute or commercially use the documentation content, follow GrapeCity's terms.
