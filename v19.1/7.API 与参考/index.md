# api-and-references

本章节是 SpreadJS 的参考文档汇总，包含 API 索引以及版本发布说明。当您需要查阅某个具体 API 的签名、参数、返回值，或了解版本间的变更时，请访问本章节。

### 本章节内容

| 主题 | 说明 |
| --- | --- |
| **[API 索引](gcdocsite__documentlink?toc-item-id=07f95b5a-8468-4a7a-9ab0-259047aa14d6)** | SpreadJS 全部 API 的完整索引，按命名空间与类组织，是查阅 API 细节的入口。 |
| **[发布说明](gcdocsite__documentlink?toc-item-id=e143cd9f-5775-4216-9598-b96e51aa7cdf)** | 各版本的新增功能、改进与缺陷修复记录。 |

### 使用建议

* **查阅 API**：优先使用「API 索引」，按 `GC.Spread.Sheets.*` 命名空间定位目标类与方法。
* **理解样式行为**：当样式设置不符合预期时，请查阅「对象继承」了解优先级规则。
* **处理用户交互**：响应用户操作时，在「常用事件」中查找对应事件及其参数。
* **跟进版本变化**：升级 SpreadJS 版本前，请先阅读「发布说明」中的变更项，评估对现有项目的影响。

### 搜索技巧

SpreadJS 内部存在许多同名能力，查 API 时请带上宿主类型以提高准确性：

* 错误示例：`addRow`
* 正确示例：`addRow Worksheet`

查阅框架接入时，优先使用以下固定查询：

* React：`Using SpreadJS with React`
* Vue：`Using SpreadJS with Vue`
* Angular：`add SpreadJS to Angular CLI app`

查阅设计器集成时：

* `add SpreadJS designer to React app`
* `add SpreadJS designer to Vue app`
* `add SpreadJS designer to Angular app`