# collaboration-server

SpreadJS 协同编辑支持多名用户同时编辑同一份工作簿，所有修改实时同步，并保证数据一致性。本章节文档分为四类：教程（Tutorial）、指南（How-to）、解释（Explanation）、参考（Reference），左侧导航可看到清晰的类型边界。

## 快速开始（教程）

* **[快速开始：搭建一个支持实时协同的 SpreadJS 设计器](gcdocsite__documentlink?toc-item-id=52b398f1-8d89-43e2-a3a2-30a0f018b725)** — 通过完整步骤搭建一个最小可用的实时协同示例，作为后续扩展的基础。

## 功能配置指南（How-to）

以上快速开始示例可独立运行。以下指南基于各自的实际需求，按需选用，相互独立。

* **[数据库适配器](gcdocsite__documentlink?toc-item-id=55d4f510-ebad-477b-8c99-bfbd012ce0fb)** — 将协同数据持久化到数据库，支持内建的 SQLite3、PostgreSQL 以及自定义适配器。
* **[用户活动状态](gcdocsite__documentlink?toc-item-id=bd88e0d5-e751-40ca-9d96-d38b2c7a9d70)** — 在协同过程中实时显示其他用户的光标、选区与在线状态。
* **[用户权限](gcdocsite__documentlink?toc-item-id=ca8075f5-efed-4e02-af35-a3889e4a32d8)** — 区分编辑权限与只读权限，控制不同用户的操作范围。
* **[独立部署协同客户端和服务器](gcdocsite__documentlink?toc-item-id=98318684-e967-49b0-b524-1ed91770d50a)** — 将前端与协同服务端分别部署，适用于前后端分离的工程结构。
* **[扩展包安装与绑定](gcdocsite__documentlink?toc-item-id=2a6237c4-455d-4c03-ae02-257f0c5e84eb)** — 安装 `spread-sheets-collaboration` 扩展包，注册 OT 类型并完成工作簿与文档的绑定。

## 协同原理与机制（Explanation）

理解协同系统的运作机制、组件分工与冲突处理方式，便于排查异常与做架构决策。

* **[协同原理速览](gcdocsite__documentlink?toc-item-id=05e7aa9f-dd38-49da-b8f1-b00b11794e31)** — 简要介绍协同编辑的整体架构、操作流转过程与冲突处理机制。
* **[协同框架架构](gcdocsite__documentlink?toc-item-id=ff57ad15-7dbe-41fc-bfdc-79696d5f540e)** — SpreadJS 产品层协同封装的组件架构、工作机制与功能概览。
* **[协同模式](gcdocsite__documentlink?toc-item-id=5c43018b-87c1-4032-a706-593af4654507)** — 不同 SpreadJS 模型如何接入协同。下分两种模式：
    * 工作表模式 — 默认协作模式，基于工作簿快照同步。
    * [基于数据管理器的协作模式](gcdocsite__documentlink?toc-item-id=0123e95e-783d-475c-9caa-f8ae72cc8459) — 集算表协作，详见 [集算表](gcdocsite__documentlink?toc-item-id=1d277aa3-6942-4b04-962e-d288cd982a16)。
* **[冲突处理行为](gcdocsite__documentlink?toc-item-id=568d0215-7f9a-4ba8-ac7c-686a4ccd5054)** — 多人编辑时冲突操作（插入/删除行列、隐藏、排序等）的内置处理行为。
* **[协同撤销机制](gcdocsite__documentlink?toc-item-id=386ef288-dac1-4aea-b859-67c8ccb4a8d9)** — 协同场景下的撤销行为、OT 转换后的撤销结果、四个协同撤销事件。
* **[底层协同框架](gcdocsite__documentlink?toc-item-id=3e2d95c7-cc76-430c-a676-ad9aefea8594)** — 通信（js-collaboration）、OT（js-collaboration-ot）与状态（js-collaboration-presence）三个模块的完整 API。仅在自定义通信协议或在非 SpreadJS 场景中复用底层框架时需要直接使用。

## 开发参考（Reference）

查阅编写协同代码时的行为规则与接口定义。

* **[协同规范](gcdocsite__documentlink?toc-item-id=dc7183a3-e36f-421e-977c-20902f045e36)** — 编写协同代码需遵循的约束（嵌套对象整体赋值、公式协同行为等）。
* **[协同插件-快照与变更集](gcdocsite__documentlink?toc-item-id=24d984bd-7688-4282-b8d3-e752a3aa5b58)** — 快照、变更集、批处理等底层 API。
    * [操作类型枚举](gcdocsite__documentlink?toc-item-id=5ab30edb-2308-4b23-9e7f-9e738078e85b) — 所有 OpType 枚举。
* **[用户与权限 API](gcdocsite__documentlink?toc-item-id=d56fb152-9b05-4331-a7b2-a9b38e1a0878)** — UserManager、setPresences/getPresences。
    * [活动状态](gcdocsite__documentlink?toc-item-id=ad1912ee-5918-49d1-b1b0-9afdc8eba1b6) — 实时显示其他用户的光标与选区。
    * [权限类型](gcdocsite__documentlink?toc-item-id=5ef1033a-4d6d-44cc-9260-22b36a276c4b) — BrowsingMode / PermissionTypes 枚举。
    * [设计器权限配置](gcdocsite__documentlink?toc-item-id=c2d2f31b-03a8-403b-97bb-62f8cb026a93) — 设计器对查看模式权限的 UI 支持。

## 附录

* **[协同术语表](gcdocsite__documentlink?toc-item-id=283d4ae0-9469-45ef-9072-e4d6bdf65e7e)** — 协同相关名词解释。
* **[协同授权](gcdocsite__documentlink?toc-item-id=cf512de0-543c-4fb0-b0cf-957a3b542d41)** — 协同功能的授权与许可说明。
* **[性能测试报告](gcdocsite__documentlink?toc-item-id=9e7bf8e1-6de0-4c44-86d5-263492950d80)** — 协同服务的性能基准数据。