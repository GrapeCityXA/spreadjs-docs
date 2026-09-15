# collaboration-server

SpreadJS 提供了强大的 **协同服务器**，通过其专有的 **[协同框架](gcdocsite__documentlink?toc-item-id=3e2d95c7-cc76-430c-a676-ad9aefea8594)** 和 **[SpreadJS 协同](gcdocsite__documentlink?toc-item-id=ff57ad15-7dbe-41fc-bfdc-79696d5f540e)**，旨在满足企业的多样化需求。

## 企业中的协同挑战

在当今快节奏的商业世界中，高效协同是企业蓬勃发展的必备条件。但让不同团队和用户顺利协同工作一直是一大障碍。数据更新延迟、权限冲突以及无法跟踪变更等问题，都可能导致项目进度放缓并引发错误。

## SpreadJS 协同服务器解决方案

SpreadJS 凭借其强大的协同服务器来解决这些问题。作为服务器的技术基础，**[协同框架](gcdocsite__documentlink?toc-item-id=3e2d95c7-cc76-430c-a676-ad9aefea8594)** 由三个核心模块组成：

* [js-collaboration](gcdocsite__documentlink?toc-item-id=aa6197b8-ca65-405d-84a9-3015b2906d14)：核心通信框架，支持双向数据同步和消息广播。
* [js-collaboration-ot](gcdocsite__documentlink?toc-item-id=513b7d54-8720-4e10-982a-08fb0afc8d7f)：
    • 基于 OT（操作转换）的文档协同库，适用于富文本编辑器、电子表格和代码编辑器。
    • 包含数据库适配器，可与各种存储系统无缝集成。
* [js-collaboration-presence](gcdocsite__documentlink?toc-item-id=a3fd6db5-ad9f-40da-934d-0e5c06045ee2)：实时用户状态共享，包括光标位置和文本选择高亮显示。

### 可定制的协同框架

[协同框架](gcdocsite__documentlink?toc-item-id=3e2d95c7-cc76-430c-a676-ad9aefea8594) 的核心功能和附加模块为上层应用提供标准化的能力支持。您可以利用此框架快速构建诸如 `spread-sheets-collaborative` 和 `quillis-collaboration` 之类的解决方案，从而实现用户管理和文档版本历史跟踪等特定业务需求。
![architecture2](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/1f04de1b-0add-4f88-889e-295f2a2e218b/architecture2.792e63.87499f.png)

### SpreadJS 表格协同

SpreadJS 专门提供了 [SpreadJS 协同框架](gcdocsite__documentlink?toc-item-id=ff57ad15-7dbe-41fc-bfdc-79696d5f540e)（`spread-sheets-collaborative`），支持多个用户同时编辑同一文档或单个用户使用多个视图，同时确保所有操作实时同步。
协同过程中，工作簿会显示用户的在线状态。此外，您可以为不同用户分配编辑或仅查看权限。

## 开始使用

在本指南中，我们将带您了解 [协同框架基础](gcdocsite__documentlink?toc-item-id=3e2d95c7-cc76-430c-a676-ad9aefea8594) 和 [SpreadJS 协同框架](gcdocsite__documentlink?toc-item-id=ff57ad15-7dbe-41fc-bfdc-79696d5f540e)。您不仅会学习如何使用这些工具，还会理解其设计背后的原因。
通过理论概念和实践练习相结合，您将全面了解如何在日常工作中充分利用 SpreadJS 协同服务器的功能。