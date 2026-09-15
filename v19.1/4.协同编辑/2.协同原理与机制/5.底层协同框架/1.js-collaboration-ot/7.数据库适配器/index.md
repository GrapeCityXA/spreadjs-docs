# database-adapter

**数据库适配器**（[IDatabaseAdapter](gcdocsite__documentlink?toc-item-id=2512e56f-4385-4fa4-a86e-ae14867d8d70)）是服务器端功能的核心组件，负责文档快照和操作的持久化存储。
数据库适配器定义了与底层存储的交互方式。操作（op）会被持续存储以记录历史，而快照仅保留最新版本，并通过累积的操作进行更新。
本文档介绍如何使用和实现数据库适配器，并将其集成到DocumentServices中。

* 存储和读取文档快照及操作
* 支持历史数据查询和提交

**适用场景**：生产环境中的持久化存储、自定义存储解决方案
**内置适配器**：MemoryDb（内存存储）、Postgres Adapter和SQLite3 Adapter

## 接口：IDatabaseAdapter

```typescript
/** 
* 定义操作转换（OT）算法中的数据库适配器接口
* @template S - 快照数据的类型
* @template T - 操作数据的类型
* @public 公共接口
*/
export interface IDatabaseAdapter<S = unknown, T = unknown> {    
/**     
* 获取两个版本之间的操作（包含起始版本，不包含结束版本）
* @param {string} id - 文档唯一标识
* @param {number} from - 起始版本号
* @param {number} [to] - 结束版本号（可选）
* @param {unknown} [options] - 附加配置项（可选）
* @returns {Promise<IOp<T>[]>} 解析为操作数组的 Promise 对象
*/    
getOps(id: string, from: number, to?: number, options?: unknown): Promise<IOp<T>[]>;    
/**     
* 根据文档ID获取文档信息
* @param {string} id - 文档唯一标识
* @param {unknown} [options] - 附加配置项（可选）
* @returns {Promise<IDocument | null>} 解析为文档信息的 Promise 对象，未找到则返回 null
*/    
getDocument(id: string, options?: unknown): Promise<IDocument | null>;
    /**     
* 根据文档ID获取文档快照
* @param {string} id - 文档唯一标识
* @param {unknown} [options] - 附加配置项（可选）
* @returns {Promise<ISnapshot<S> | null>} 解析为文档快照的 Promise 对象，未找到则返回 null
*/    
getSnapshot(id: string, options?: unknown): Promise<ISnapshot<S> | null>;    
/**     
* 根据文档ID和片段ID获取指定的文档片段
* @param {string} id - 文档唯一标识
* @param {string} fragmentId - 片段唯一标识
* @param {unknown} [options] - 附加配置项（可选）
* @returns {Promise<{ version: number, data: S | null } | null>} 解析为包含片段版本和数据的对象；文档不存在则返回 null；文档存在但片段不存在则 data 为 null
*/    
getFragment(id: string, fragmentId: string, options?: unknown): Promise<{ version: number, data: S | null } | null>;
    /**     
* 向数据库提交一条操作
* @param {string} id - 文档唯一标识
* @param {IOp<T>} op - 待提交的操作
* @param {IDocument} document - 文档元数据
* @param {unknown} [options] - 附加配置项（可选）
* @returns {Promise<boolean>} 提交成功返回 true，失败返回 false
*/    
commitOp(id: string, op: IOp<T>, document: IDocument, options?: unknown): Promise<boolean>;    
/**     
* 向数据库提交一份快照
* @param {string} id - 文档唯一标识
* @param {ICommitSnapshot<S>} snapshot - 待提交的快照
* @param {unknown} [options] - 附加配置项（可选）
* @returns {Promise<boolean>} 提交成功返回 true，失败返回 false
*/    
commitSnapshot(id: string, snapshot: ICommitSnapshot<S>, options?: unknown): Promise<boolean>;
    /**     
* 获取操作已提交的版本号（若存在）
* @param {string} id - 文档唯一标识
* @param {number} to - 校验的最大版本号
* @param {IOp<T>} op - 待校验的操作
* @returns {Promise<number | null>} 解析为已提交版本号的 Promise 对象，未提交则返回 null
*/    
getCommittedOpVersion(id: string, to: number, op: IOp): Promise<number | null>;
    /**     
* 关闭数据库连接
* @returns {Promise<void>} 数据库关闭完成后解析的 Promise 对象
*/    
close(): Promise<void>;
}
```

## 集成到DocumentServices

将数据库适配器传入DocumentServices的配置中：

```typescript
import { DocumentServices, IDatabaseAdapter, MemoryDb } from '@grapecity-software/js-collaboration-ot';

const dbAdapter: IDatabaseAdapter = new MemoryDb();
const docService = new DocumentServices({ db: dbAdapter });
```

## 内置适配器

### MemoryDb

* **描述**：内存适配器，数据存储在RAM中
* **用例**：开发和测试
* **限制**：服务器重启后数据丢失，不适合生产环境
* **注意：** 创建 DocumentServices 时，MemoryDb 为默认数据库适配器。

```typescript
import { MemoryDb } from '@grapecity-software/js-collaboration-ot';

const dbAdapter = new MemoryDb();
```

### Postgres数据库适配器

* **描述**：基于PostgreSQL的持久化适配器
* **用例**：生产环境，支持持久化存储
* [内建 Postgres 表结构](gcdocsite__documentlink?toc-item-id=79d3ca66-d7e8-4611-b114-0058030200a9)

```typescript
import pg from 'pg';
import { PostgresDb } from '@grapecity-software/js-collaboration-ot-postgres';

const config = {
    host: 'localhost',
    database: 'your_database',
    user: 'your_user_name',
    password: 'your_password',
    port: 5432, // 默认端口
};
const dbInstance = new pg.Pool(config);
const dbAdapter = new PostgresDb(dbInstance);
```

### Sqlite3数据库适配器

* **描述**：基于SQLite3的持久化适配器
* **用例**：开发和测试环境，支持持久化存储
* [内建 SQLite3 表结构](gcdocsite__documentlink?toc-item-id=f3d9d0a1-8dba-431e-a5ae-72f63b2eb782)

```typescript
import sqlite3 from 'sqlite3';
import { SqliteDb } from '@grapecity-software/js-collaboration-ot-sqlite';

const dbInstance = new sqlite3.Database("./sample.db");
const dbAdapter = new SqliteDb(dbInstance);
```

## 实现自定义数据库适配器

如果内置适配器无法满足需求，可通过实现IDatabaseAdapter接口创建自定义数据库适配器。请参考[自定义数据库适配器](gcdocsite__documentlink?toc-item-id=fc57f5c3-b0d5-4884-b32b-e3e4af0aef57)。

## 里程碑数据库适配器

除了上述主数据库适配器外，本目录还包含一种可选的**[里程碑数据库适配器](gcdocsite__documentlink?toc-item-id=55308147-258f-4ddf-bf05-4698f2341ead)**（[IMilestoneDatabaseAdapter](gcdocsite__documentlink?toc-item-id=e1ba91f6-7359-40ea-907b-8d4135364c33)），它通过定期保存文档快照来优化 `fetchHistorySnapshot` 的查询性能。详见同目录下的"里程碑数据库适配器"文档。