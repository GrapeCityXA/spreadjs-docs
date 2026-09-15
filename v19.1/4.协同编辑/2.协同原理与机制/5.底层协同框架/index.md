# framework

>type=note
> 📌 **何时阅读本章节**：这是**高级参考**，面向需要**脱离 SpreadJS 默认协同实现、自定义通信协议、或在非 SpreadJS 场景（如富文本编辑器、代码编辑器）复用底层协同框架**的开发者。如果你只是用 SpreadJS 工作簿做协同，按需完成「快速开始」和「能力选配」中的教程即可，通常**不需要**阅读本章节。

**协同框架**是一个 JavaScript 框架，通过双向通信和核心同步功能实现实时多用户协同。它包含以下模块：

* `js-collaboration`：核心通信框架，提供实时数据同步和消息广播能力。
* `js-collaboration-ot`：操作转换（OT）附加模块，支持多用户协同编辑和冲突解决。
* `js-collaboration-presence`：用户状态附加模块，支持实时用户状态共享。

## 应用场景

* 多用户协同文档编辑（富文本、电子表格、代码）
* 实时聊天同步
* 协同白板与设计工具
* 需实时多用户交互的应用

## 架构

如以下架构图所示，协同框架采用标准的 **客户端-服务器** 架构。该设计遵循实时协同系统模式，通过消息传递机制协调组件操作。
![architecture1](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/1f04de1b-0add-4f88-889e-295f2a2e218b/architecture1.f096bb.ade726.png?width=800)

此框架可扩展为特定功能的协同框架，例如 `spread-sheets-collaboration` 和 `quillis-collaboration`。
![architecture2](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/1f04de1b-0add-4f88-889e-295f2a2e218b/architecture2.b53467.b2aaed.png?width=800)

### js-collaboration

[js-collaboration](gcdocsite__documentlink?toc-item-id=aa6197b8-ca65-405d-84a9-3015b2906d14) 通过 WebSocket 提供实时数据同步，实现客户端与服务器的双向通信。**核心功能**

* **双向通信**：支持客户端与服务器间的双向消息传输。
* **房间管理**：通过隔离的房间实现多用户协同。
* **消息广播**：在同一房间内广播消息以实现实时通知。
* **自动重连**：提供心跳检测和断开后的自动重连功能。
* **中间件与钩子**：支持在连接和消息处理流程中插入自定义逻辑。

**Npm 包**`js-collaboration` 已封装为标准 Npm 包，支持客户端-服务器环境的解耦部署：

* 服务端：`@grapecity-software/js-collaboration`
* 客户端：`@grapecity-software/js-collaboration-client`

### js-collaboration-ot

[js-collaboration-ot](gcdocsite__documentlink?toc-item-id=513b7d54-8720-4e10-982a-08fb0afc8d7f) 基于 **操作转换（OT）** 技术，支持多用户同时编辑同一模型。**核心功能**

* **自定义 OT 类型**：允许开发者定义自定义操作类型以满足多样化业务需求。
* **数据持久化**：提供适配器接口以集成数据库存储。
* **分片机制**：提升大型文档的同步性能。
* **冲突解决**：通过 OT 算法确保数据一致性。
* **中间件与钩子**：支持在协同流程中插入验证、日志等逻辑。

**Npm 包**`js-collaboration-ot` 已封装为标准 Npm 包，支持客户端-服务器环境的解耦部署：

* 服务端：`@grapecity-software/js-collaboration-ot`
* 客户端：`@grapecity-software/js-collaboration-ot-client`

提供两种标准化数据库适配器实现：

* PostgreSQL：`@grapecity-software/js-collaboration-ot-postgres`
* Sqlite3：`@grapecity-software/js-collaboration-ot-sqlite`

### js-collaboration-presence

[js-collaboration-presence](gcdocsite__documentlink?toc-item-id=a3fd6db5-ad9f-40da-934d-0e5c06045ee2) 支持在实时协同环境中共享用户状态（如光标位置、选中区域等）。
**核心功能**

* **实时用户状态共享**：支持同步光标位置、选中区域等信息。
* **事件监听**：可监听用户加入、离开及其他状态更新事件。

**应用场景**

* 在多用户文档编辑中实时显示光标位置。
* 在电子表格协同中展示其他用户选中的单元格。
* 在代码编辑器中高亮协同者的编辑区域。

**Npm 包**
`js-collaboration-presence` 已封装为标准 Npm 包，支持客户端-服务器环境的解耦部署：

* 服务端：`@grapecity-software/js-collaboration-presence`
* 客户端：`@grapecity-software/js-collaboration-presence-client`

## 内容导航

三个模块的依赖关系：`js-collaboration` 是基础通信层；`js-collaboration-ot` 与 `js-collaboration-presence` 在其之上分别提供 OT 协同编辑能力与用户状态共享能力，两者相互独立、可按需组合。

* [js-collaboration](gcdocsite__documentlink?toc-item-id=aa6197b8-ca65-405d-84a9-3015b2906d14) — 客户端/服务器双向通信、房间机制、消息广播、心跳重连、中间件与钩子。
* [js-collaboration-ot](gcdocsite__documentlink?toc-item-id=513b7d54-8720-4e10-982a-08fb0afc8d7f) — OT 类型、SharedDoc、DocumentServices、数据库适配器、片段机制、OT 中间件。
* [js-collaboration-presence](gcdocsite__documentlink?toc-item-id=a3fd6db5-ad9f-40da-934d-0e5c06045ee2) — Presence 客户端与服务器、用户状态共享。