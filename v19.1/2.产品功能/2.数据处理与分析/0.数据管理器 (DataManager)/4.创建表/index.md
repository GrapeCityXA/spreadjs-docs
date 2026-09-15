# creating-tables

## 什么是表

表（Table）是 DataManager 中的核心数据容器。
它负责：

* 存储数据
* 管理 schema
* 处理数据同步
* 维护与其他表的关系
* 作为视图（View）的宿主

视图定义数据的展示方式。
表定义数据的存储和管理方式。

## 表类型

DataManager 支持两种类型的表：

### 内存表

内存表会将数据存储在客户端本地。

* 数据可以直接以 JSON、CSV 或 XML 的形式提供。
* 所有操作都在内存中完成。
* 不需要与服务器通信。

此类型适用于：

* 静态数据集
* 客户端应用
* 离线场景
* 原型开发

### 远程表

远程表会从服务器获取数据，并与服务器同步数据。

* 数据从远程端点读取。
* 数据变更可以自动同步，也可以批量同步。
* 列定义也可以由远程管理。

此类型适用于：

* 企业应用
* CRUD 系统
* 集中式数据存储
* 多用户环境

## 创建表 API

可以通过以下方式创建表：

```javascript
dataManager.addTable(name, dataSourceOption);
```

`dataSourceOption` 决定：

* 表基于内存还是基于远程数据源
* 是否启用同步
* 如何定义 schema

## 基本数据流

```auto
内存数据或远程数据源
          ↓
        Table
          ↓
        View
          ↓
      Component
```

表层独立于 UI 层。

## 后续步骤

* [添加内存表](gcdocsite__documentlink?toc-item-id=d7c19eef-9d2c-4523-bf0a-3ade0a3832b6)
* [添加远程表](gcdocsite__documentlink?toc-item-id=1bec150c-b7e8-4400-b8d2-c8d1fd5e3b5d)


<br>
