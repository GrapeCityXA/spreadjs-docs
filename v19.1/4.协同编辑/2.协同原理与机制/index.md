# collaboration-explaination

本章节帮助你理解协同系统的运作机制、组件分工与冲突处理方式，便于排查异常与做架构决策。各文档相互独立，可按需选读，无需通读。

* **[协同原理速览](gcdocsite__documentlink?toc-item-id=05e7aa9f-dd38-49da-b8f1-b00b11794e31)** — 简要介绍协同编辑的整体架构、操作流转过程与冲突处理机制。
* **[协同框架架构](gcdocsite__documentlink?toc-item-id=ff57ad15-7dbe-41fc-bfdc-79696d5f540e)** — SpreadJS 产品层协同封装的组件架构、工作机制与功能概览。
* **[协同模式](gcdocsite__documentlink?toc-item-id=5c43018b-87c1-4032-a706-593af4654507)** — 不同 SpreadJS 模型如何接入协同。下分两种模式：
    * [工作表模式](gcdocsite__documentlink?toc-item-id=3fda91f6-d262-423d-9f36-72e770d975ae) — 默认协作模式，基于工作簿快照同步。
    * [基于数据管理器的协作模式](gcdocsite__documentlink?toc-item-id=0123e95e-783d-475c-9caa-f8ae72cc8459) — 集算表协作，详见 [集算表](gcdocsite__documentlink?toc-item-id=1d277aa3-6942-4b04-962e-d288cd982a16)。
* **[冲突处理行为](gcdocsite__documentlink?toc-item-id=568d0215-7f9a-4ba8-ac7c-686a4ccd5054)** — 多人编辑时冲突操作（插入/删除行列、隐藏、排序等）的内置处理行为。
* **[协同撤销机制](gcdocsite__documentlink?toc-item-id=386ef288-dac1-4aea-b859-67c8ccb4a8d9)** — 协同场景下的撤销行为、OT 转换后的撤销结果、四个协同撤销事件。
* **[底层协同框架](gcdocsite__documentlink?toc-item-id=3e2d95c7-cc76-430c-a676-ad9aefea8594)** — 通信（js-collaboration）、OT（js-collaboration-ot）与状态（js-collaboration-presence）三个模块的完整 API。仅在自定义通信协议或在非 SpreadJS 场景中复用底层框架时需要直接使用。