# getstarted

## 浏览器要求

运行 SpreadJS 需要以下浏览器：

* Microsoft IE Edge
* Mozilla FireFox
* Safari
* Google Chrome

浏览器必须完全支持HTML5。

## 安装

### 下载 SpreadJS

* [产品下载地址](https://www.grapecity.com.cn/developer/spreadjs/download) （下载页面会自动选择系统版本，支持 Windows / Mac / Linux）

#### 不同版本下载包文件说明

* Windows ：如 SpreadJS.Release.V16.1(for windows).zip

    | **名称** | **类型** | **说明** |
    | --- | --- | --- |
    | **产品入门必读.pdf** | PDF 文件 | 本文档 |
    | **新手训练营.png** | PNG 图片 | 扫描二维码，参加免费的产品新手训练营，快速入门 |
    | **SpreadJS 安装程序（运行库+示例+桌面设计器）.msi** | Msi 安装程序 | 一键安装 SpreadJS 运行库、桌面设计器及示例，并创建开始菜单 |
    | **SpreadJS 组件运行库** | 文件夹 | 包含SpreadJS 组件运行库文件及产品示例：js / css / ts |
* MacOS ：如 SpreadJS.Release.V16.1(for mac).zip

    | **名称** | **类型** | **说明** |
    | --- | --- | --- |
    | **产品入门必读.pdf** | PDF 文件 | 本文档 |
    | **新手训练营.png** | PNG 图片 | 扫描二维码，参加免费的产品新手训练营，快速入门 |
    | **表格编辑器（桌面端）Designer** | 文件夹 | 针对 MacOS 的桌面端设计器应用 |
    | **SpreadJS 组件运行库** | 文件夹 | 包含SpreadJS 组件运行库文件及产品示例：js / css / ts |
* Linux：如 SpreadJS.Release.V16.1(for linux).zip

    | **名称** | **类型** | **说明** |
    | --- | --- | --- |
    | **产品入门必读.pdf** | PDF 文件 | 本文档 |
    | **新手训练营.png** | PNG 图片 | 扫描二维码，参加免费的产品新手训练营，快速入门 |
    | **表格编辑器（桌面端）Designer** | 文件夹 | 针对 Linux 的桌面端设计器应用 |
    | **SpreadJS 组件运行库** | 文件夹 | 包含SpreadJS 组件运行库文件及产品示例：js / css / ts |

### 安装 SpreadJS 桌面端设计器

* 将下载的产品包保存到系统上的临时目录，然后将文件解压缩到目录。
* 运行适合您的环境的安装文件。
* 运行设计器，选择锁定图标，然后输入许可证密钥以解锁 SpreadJS 设计器，或者申请试用授权。

| **系统** | **安装** |
| --- | --- |
| Windows | SpreadJS 安装程序（运行库+示例+桌面设计器）.msi |
| Mac | SpreadJS-Designer.x.x.x.dmg |
| Linux | SpreadJS-Designer.x.x.x.AppImage |

参考[试用版和许可信息](gcdocsite__documentlink?toc-item-id=f9e48ba0-5b2d-425a-aeec-127a486ab4fe)有关许可信息。

### 内容安全策略 （CSP）

CSP 是通过头部或元标签实施的安全策略，用以规范和授权在您的网站上加载的内容。
要建立一个 CSP 指令参考，您可以选择在服务器上配置 HTTP 响应头，或者在 HTML 头元素中设置元标签。
通过这样做，您可以创建一套规则，以决定哪些内容是被允许或禁止的。这些规则增强了您网站对内容注入和跨站脚本（XSS）攻击的安全性。
作为一个嵌入式控件，SpreadJS 必须遵守 CSP 指南，确保代码远离任何潜在的攻击点。因此，包括一些特定规则来增加 SpreadJS 的安全性，如下所述。

```javascript
// No Eval rule in TSLINT
eval("alert('XSS!')");

// No Implied Eval rule in TSLINT
setTimeout("alert('Hi!');", 100);
setInterval("alert('Hi!');", 100);
execScript("alert('Hi!')");
window.setTimeout("count = 5", 10);
window.setInterval("foo = bar", 10);

// No New Function rule in TSLINT
new Function("alert('XSS!')")();
```

请注意，导入和导出 API 使用 Web Worker 来压缩或解压文件，用户必须设置正确的 CSP 规则以避免错误。
例如，考虑以下 CSP 规则：

```javascript
<meta http-equiv="Content-Security-Policy" content="worker-src 'self' blob: 'unsafe-inline' 'unsafe-eval' data:">
```

这个 CSP 规则允许从相同的源加载 Web Worker，并使用 blob URIs 用于 Web Worker，其中：

* worker-src 'self': 限制web workers的加载，只能来自于文档相同的源
* blob:: 允许使用blob URIs用于web workers
* 'unsafe-inline': 允许执行内联脚本
* 'unsafe-eval': 允许使用eval()及类似的JavaScript函数，这些函数执行作为字符串传递的代码
* data:: 允许使用数据URIs