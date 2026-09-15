# js-collaboration-ot

`js-collaboration-ot` 是基于操作转换（Operational Transformation, OT）技术的协同库，旨在增强 `js-collaboration` 的实时同步能力。通过 OT 技术，它支持多用户同时编辑同一数据，分为客户端（[js-collaboration-ot-client](gcdocsite__documentlink?toc-item-id=20ebbac7-053a-467a-b7fb-482ff47522b4)）和服务端（[js-collaboration-ot](gcdocsite__documentlink?toc-item-id=ccdcfeef-021d-4f3c-994b-206a0b8f86bd)）。

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

## 设计优势

* **模块化**：OT 类型、中间件和适配器独立设计，便于定制与扩展。
* **高效性**：片段机制减少大型文档的 I/O 开销。
* **灵活性**：支持异步中间件和多种数据库，适配复杂业务场景。

## 后续步骤

通过以下分步教程，使用 `js-collaboration` 和 `js-collaboration-ot` 构建基于操作转换（OT）的实时协同文本编辑器：

* [教程：实时文本编辑器](gcdocsite__documentlink?toc-item-id=586c843b-82b8-4fd4-8bc5-276ac583ce1b)
* [教程：添加历史功能](gcdocsite__documentlink?toc-item-id=efb3b075-eaa9-4c17-ad09-6964c1a972b9)
* [教程：配置数据库适配器](gcdocsite__documentlink?toc-item-id=3504ed47-ebde-4083-9f9a-69bf748179b4)

掌握 `js-collaboration-ot` 的核心概念和 API，涵盖：

* [操作（Op）](gcdocsite__documentlink?toc-item-id=8591d2bd-6e7b-4b61-92fe-718850819d2f)
* [冲突与转换](gcdocsite__documentlink?toc-item-id=efb3b075-eaa9-4c17-ad09-6964c1a972b9)
* [OT 类型](gcdocsite__documentlink?toc-item-id=89953b53-e259-4a92-a91d-aa7805748d7e)
* [SharedDoc 类](gcdocsite__documentlink?toc-item-id=40dbf33e-c534-46a6-b189-df7097710fb1)
* [构建并使用 DocumentServices](gcdocsite__documentlink?toc-item-id=638ff607-bdb3-42d9-b428-d44323fa6445)
* [数据库适配器](gcdocsite__documentlink?toc-item-id=460f30b1-fd3f-4fc1-accf-9255b20329ce)
* [OT（操作转换）中间件](gcdocsite__documentlink?toc-item-id=30c52940-d409-4620-8041-ff3009dbe278)
* [片段机制](gcdocsite__documentlink?toc-item-id=f77f5781-0bee-4524-b771-c133764d53fa)

每个模块将通过代码示例演示实际用法，建议按左侧导航栏的教程路径逐步实践。