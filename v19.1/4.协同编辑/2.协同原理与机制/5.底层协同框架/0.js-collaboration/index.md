# js-collaboration

`js-collaboration` 是一个支持**低延迟**、**双向通信**的库，用于实现客户端与服务器之间的实时数据同步。它分为客户端（[js-collaboration-client](gcdocsite__documentlink?toc-item-id=742e4a71-3312-495c-a4e1-074ee06fcde1)）和服务器端（[js-collaboration](gcdocsite__documentlink?toc-item-id=0e69f663-eb7d-4ba7-8ab1-fb1f156e6f31)）。

> 💡 本模块已由 [SpreadJS 协同框架](gcdocsite__documentlink?toc-item-id=ff57ad15-7dbe-41fc-bfdc-79696d5f540e) 封装为 SpreadJS 工作簿的协同通信底层。若仅使用 SpreadJS 协同，通常无需直接调用本模块 API。

## 核心功能

* **双向连接**：支持客户端与服务器的双向通信，并确保实时数据同步。
* **房间机制**：支持房间的生命周期操作（创建/加入/离开），用于组织多用户协同。
* **消息广播**：将消息实时广播至房间内所有参与者。
* **心跳与自动重连**：实现心跳监测和自动重连机制，维持持久连接。
* **中间件与钩子系统**
    * 中间件提供了在连接和消息处理过程中插入自定义逻辑的机制，可用于实现认证、权限控制等功能。
    * 钩子在关键事件发生时触发自定义处理逻辑。

## 关于房间

当客户端通过WebSocket连接到服务器时，初始化阶段完成。服务器采用**基于房间的架构**管理并发客户端会话，每个房间代表一个隔离的同步上下文。协同过程中，服务器通过广播机制向同一房间内的客户端**实时广播**消息。
了解更多关于广播的内容，请查看[消息发送与接收](gcdocsite__documentlink?toc-item-id=689ee552-5bd1-4ca7-8eba-3a698be9fef1)。
![overview-room](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/1f04de1b-0add-4f88-889e-295f2a2e218b/overview-room.4e4969.646c6d.png)

## 内容导航

### API 参考

本模块涵盖以下核心概念与 API：

* 客户端/服务器初始化
* 实时连接管理（Connection、Server 类）
* 服务器中间件机制
* 消息发送与接收
* 用户认证与权限

### 教程

通过以下分步教程，使用 `js-collaboration` 构建实时聊天室并实现用户认证功能：

* [教程：实时聊天室](gcdocsite__documentlink?toc-item-id=57806af3-435d-4db5-bebc-01c0245ac8e1)
* [教程：添加认证功能](gcdocsite__documentlink?toc-item-id=e72d4da6-8759-4302-9035-b4ddd28a0d67)