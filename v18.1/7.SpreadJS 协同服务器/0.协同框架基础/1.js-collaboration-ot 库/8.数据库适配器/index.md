# database-adapter

**数据库适配器**（[IDatabaseAdapter](gcdocsite__documentlink?toc-item-id=2512e56f-4385-4fa4-a86e-ae14867d8d70)）是服务器端功能的核心组件，负责文档快照和操作的持久化存储。
数据库适配器定义了与底层存储的交互方式。操作（op）会被持续存储以记录历史，而快照仅保留最新版本，并通过累积的操作进行更新。
本文档介绍如何使用和实现数据库适配器，并将其集成到DocumentServices中。

* 存储和读取文档快照及操作
* 支持历史数据查询和提交

**适用场景**：生产环境中的持久化存储、自定义存储解决方案**内置适配器**：MemoryDb（内存存储）、Postgres Adapter和SQLite3 Adapter

## 接口：IDatabaseAdapter

```typescript
/**
 * 数据库适配器接口
 */
export interface IDatabaseAdapter<S = unknown, T = unknown> {
    /**
     * 获取两个版本之间的操作，包含起始版本，不包含结束版本
     */
    getOps(id: string, from: number, to?: number, options?: unknown): Promise<IOp<T>[]>;
    /**
     * 通过ID获取文档信息
     */
    getDocument(id: string, options?: unknown): Promise<IDocument | undefined | null>;
    /**
     * 通过ID获取快照
     */
    getSnapshot(id: string, options?: unknown): Promise<ISnapshot<S> | undefined | null>;
    getFragment(id: string, fragmentId: string, options?: unknown): Promise<S | undefined | null>;
    getFragments(id: string, fragmentIds?: string[], options?: unknown): Promise<{ [id: string]: S }>;
    commitOp(id: string, op: IOp<T>, document: IDocument, options?: unknown): Promise<boolean>;
    commitSnapshot(id: string, snapshot: ICommitSnapshot<S>, options?: unknown): Promise<boolean>;
    /**
     * 获取已提交操作的版本，如果操作已提交，返回提交版本，否则返回undefined
     */
    getCommittedOpVersion(id: string, to: number, op: IOp): Promise<number | undefined>;
    /**
     * 关闭数据库
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