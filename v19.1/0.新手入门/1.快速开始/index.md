# getstarted

本页介绍如何使用 NPM 创建并运行一个最小 SpreadJS 示例。完成后，您将在浏览器中看到一个可编辑的表格，并向第一个单元格写入文本。

## 前提条件

开始前，请确认本机已安装 Node.js 和 npm。浏览器、操作系统和框架兼容性请参考 [兼容性与运行环境](gcdocsite__documentlink?toc-item-id=74533757-90f5-455d-8a9d-7ad676b1c83d)。

## 创建项目

使用 Vite 创建一个基础 JavaScript 项目：

```bash
npm create vite@latest spreadjs-quick-start -- --template vanilla
cd spreadjs-quick-start
npm install
```

## 安装 SpreadJS

安装 SpreadJS 核心包：

```bash
npm install @grapecity-software/spread-sheets
```

## 添加页面容器

清空 `src/main.js` 中的内容，并添加 SpreadJS 容器，初始化工作簿：

```js
import * as GC from '@grapecity-software/spread-sheets'
import '@grapecity-software/spread-sheets/styles/gc.spread.sheets.excel2013white.css'
import './style.css'

document.querySelector('#app').innerHTML = '<div id="ss"></div>'

const spread = new GC.Spread.Sheets.Workbook(document.getElementById('ss'), {
  sheetCount: 1
})

const sheet = spread.getActiveSheet()
sheet.setValue(0, 0, 'Hello SpreadJS')
```

在 `src/style.css` 中设置容器尺寸：

```css
html,
body,
#app {
  width: 100%;
  height: 100%;
  margin: 0;
}

#ss {
  width: 100%;
  height: 600px;
}
```

>type=note
> SpreadJS 需要挂载到具有明确尺寸的容器中。如果容器高度为 0，页面中将无法正常显示表格。

## 运行项目

执行以下命令启动开发服务器：

```bash
npm run dev
```

打开终端中提示的本地地址，即可看到 SpreadJS 表格。第一个工作表的 `A1` 单元格中会显示 `Hello SpreadJS`。
![image](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/e25f3d46-838d-46f9-98f2-67923a84186b/image-20260706.4eb668.png?width=400)

## 下一步

如果您希望通过官方脚手架创建示例工程，也可以继续阅读本章节下的“脚手架创建工程”。

如果您需要在 Vue、React、Angular、NextJS 或 NuxtJS 中集成 SpreadJS，请继续阅读 [框架集成](gcdocsite__documentlink?toc-item-id=94da5d60-da19-4b25-b2a0-5451a909910b)。

如果您需要导入导出、图表、PDF、数据透视表等能力，请阅读 [模块与按需加载](gcdocsite__documentlink?toc-item-id=9c1e1946-dd34-49fa-a3ff-b78f676ace18)。