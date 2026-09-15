# js-collaboration-ot

`js-collaboration-ot` 是基于操作转换（Operational Transformation, OT）技术的协同库，旨在增强 `js-collaboration` 的实时同步能力。通过 OT 技术，它支持多用户同时编辑同一数据，分为客户端（[js-collaboration-ot-client](gcdocsite__documentlink?toc-item-id=20ebbac7-053a-467a-b7fb-482ff47522b4)）和服务端（[js-collaboration-ot](gcdocsite__documentlink?toc-item-id=ccdcfeef-021d-4f3c-994b-206a0b8f86bd)）。

> 💡 本模块已由 [SpreadJS 协同框架](gcdocsite__documentlink?toc-item-id=ff57ad15-7dbe-41fc-bfdc-79696d5f540e) 封装为 SpreadJS 工作簿的协同 OT 底层（含专属 OT 类型实现）。若仅使用 SpreadJS 协同，通常无需直接调用本模块 API。

## 适用场景

适用于需要实时协同编辑的应用场景，包括：

* 协同电子表格编辑
* 富文本共同创作
* 交互式图表协同

## 核心功能

* **自定义 OT 类型**：支持开发者定义自定义操作类型，满足多样化业务需求。
* **数据持久化**：提供适配器接口，可集成数据库存储。
* **片段机制（Fragments）**：提升大型文档的同步性能。
* **冲突解决**：通过 OT 算法确保数据一致性。
* **中间件与钩子**：支持在协同流程中插入验证、日志等逻辑。

## 内容导航

### API 参考

本模块涵盖以下核心概念与 API：

* [操作（Op）](gcdocsite__documentlink?toc-item-id=8591d2bd-6e7b-4b61-92fe-718850819d2f)
* [冲突与转换](gcdocsite__documentlink?toc-item-id=efb3b075-eaa9-4c17-ad09-6964c1a972b9)
* [OT 类型](gcdocsite__documentlink?toc-item-id=89953b53-e259-4a92-a91d-aa7805748d7e)
    * [片段机制](gcdocsite__documentlink?toc-item-id=f77f5781-0bee-4524-b771-c133764d53fa) — OT 类型的服务器端扩展，通过拆分快照提升大型文档性能
* [SharedDoc 类](gcdocsite__documentlink?toc-item-id=40dbf33e-c534-46a6-b189-df7097710fb1)
* [构建并使用 DocumentServices](gcdocsite__documentlink?toc-item-id=638ff607-bdb3-42d9-b428-d44323fa6445)
* [数据库适配器](gcdocsite__documentlink?toc-item-id=460f30b1-fd3f-4fc1-accf-9255b20329ce)
    * [里程碑数据库适配器](gcdocsite__documentlink?toc-item-id=55308147-258f-4ddf-bf05-4698f2341ead) — 定期保存快照以优化历史查询性能
* [OT（操作转换）中间件](gcdocsite__documentlink?toc-item-id=30c52940-d409-4620-8041-ff3009dbe278)

### 教程

通过以下分步教程，使用 `js-collaboration` 和 `js-collaboration-ot` 构建基于操作转换（OT）的实时协同文本编辑器：

* [教程：实时文本编辑器](gcdocsite__documentlink?toc-item-id=586c843b-82b8-4fd4-8bc5-276ac583ce1b)
* [教程：添加历史功能](gcdocsite__documentlink?toc-item-id=efb3b075-eaa9-4c17-ad09-6964c1a972b9)
* [教程：配置数据库适配器](gcdocsite__documentlink?toc-item-id=3504ed47-ebde-4083-9f9a-69bf748179b4)