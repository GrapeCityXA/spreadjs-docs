# schema

schema 定义表如何解释和管理其数据。
在 DataManager 中创建表时，schema 用于描述：

* 原始数据如何解析
* 字段如何组织结构并设置类型
* 计算值如何定义
* 表是否包含可复用的窗口规范
* 表是否具有层次结构

schema 属于表，并决定表的结构行为。

## 不提供 schema 时会发生什么

如果未提供 schema：

* 数据会使用默认解析规则加载
* 字段会直接从原始数据推断
* 不会应用结构约束或计算列
* 不会提供层次结构或可复用窗口定义

提供 schema 后，可以显式控制结构和行为。

## Schema 结构

schema 定义在表选项中：

```javascript
dataManager.addTable("orders", {
    data: [...],
    schema: {
        // schema configuration
    }
});
```

schema 可以包含以下主要部分：

```typescript
interface ISchemaOption {
    type?: string;               // parsing type
    dataPath?: string;           // nested data path
    columns?: {...};             // column definitions
    window?: {...};              // reusable window definitions
    hierarchy?: {...};           // hierarchical structure
}
```

每个部分都控制表结构的某个特定方面。

## 数据解析

解析配置决定如何解释原始数据。
它控制：

* 数据源类型（例如 JSON 或 CSV）
* 嵌套数据提取
* 字段规范化规则

有关详细信息，请参阅 **[数据解析](gcdocsite__documentlink?toc-item-id=c481d982-0feb-41a2-a213-0095261a65aa)**。

## 定义列

列定义各个字段在表中的行为。
它们控制：

* 字段映射和标识
* 数据类型
* 验证规则
* 计算值
* 展示元数据

有关详细配置，请参阅 **[定义列](gcdocsite__documentlink?toc-item-id=b46835ec-8596-4cd0-9149-85f959793a57)**。

## 窗口定义

窗口定义为 `WINDOW()` 公式提供可复用的窗口规范。
它们：

* 定义分区、排序和框架规则
* 提升复用性和一致性
* 仅影响公式计算

有关详细信息，请参阅 **[窗口定义](gcdocsite__documentlink?toc-item-id=df658faa-31e3-4aae-8f9e-f53ca1b9e33e)**。

## 层次结构配置

层次结构配置会在单个表中将记录组织为父子结构。
它定义：

* 如何推导父级关系
* 如何解释嵌套结构
* 可选的汇总字段行为

有关详细信息，请参阅 **[层次结构数据](gcdocsite__documentlink?toc-item-id=a118e238-657b-40a3-aa1d-f45685caefec)**。

## 职责边界

schema 定义 DataManager 内部的结构行为。
它：

* 不控制远程通信
* 不渲染 UI
* 不定义跨表关系
* 不执行 CRUD 操作

这些职责由系统的其他部分承担。
schema 只关注表如何理解和组织自身数据。

<br>
