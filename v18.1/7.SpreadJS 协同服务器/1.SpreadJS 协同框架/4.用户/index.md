# user

为了支持协同功能，SpreadJS的工作簿引入了**用户（User）** 概念，将用户定义为**IUser**接口，以便于管理用户权限和身份。本文档详细解释了[IUser](gcdocsite__documentlink?toc-item-id=6bb47d69-efe1-43cd-9be6-b450a360ea8c#iuser)接口的结构、属性及相关功能。

## IUser

**IUser**接口定义了SpreadJS协同中用户对象的结构，以下是其属性说明：

### 属性

* **id: string** 用户的唯一标识符，用于区分不同的协同用户。
* **name: string** 用户的名称。
* **color: string** (可选)与用户关联的颜色，用于在协同界面中进行视觉标识（如选区颜色）。
* **permission: IPermission** (可选)指定用户在工作簿中的权限设置对象。

```typescript
export type IUser {
  id?: string;
  name: string;
  color?: string;
  permission?: GC.Spread.Sheets.Collaboration.IPermission;
}
```

### IPermission

**[IPermission](gcdocsite__documentlink?toc-item-id=6bb47d69-efe1-43cd-9be6-b450a360ea8c#ipermission)**[ ](gcdocsite__documentlink?toc-item-id=6bb47d69-efe1-43cd-9be6-b450a360ea8c#ipermission)接口定义了用户的具体权限，包含以下属性：

* **mode: BrowsingMode**指定用户的主要访问模式，取值来自**BrowsingMode**枚举：
    * **BrowsingMode.edit**：用户可编辑文档。
    * **BrowsingMode.view**：用户仅可查看文档，但可能有额外权限。
* **viewModePermissions: PermissionTypes (可选)指定用户在**查看（view） 模式下的额外权限。该属性为位字段，支持通过位运算组合多个**PermissionTypes**值。

```typescript
export type IPermission {
    mode?: GC.Spread.Sheets.Collaboration.BrowsingMode;
    viewModePermissions?: GC.Spread.Sheets.Collaboration.PermissionTypes;
}
```

### 枚举类型

#### [BrowsingMode](gcdocsite__documentlink?toc-item-id=35310e62-ca76-4d06-87ae-7890ab0f7bce)

定义用户的浏览模式：

* **edit = 0**：编辑模式，用户可修改文档。
* **view = 1**：查看模式，用户仅可查看文档。

```typescript
/**
 * 枚举文档交互的浏览模式。
 * @enum {number}
 */
export enum BrowsingMode {
    /** 允许用户编辑文档。
     * @type {number}
     */
    edit,
    /** 限制用户仅查看文档。
     * @type {number}
     */
    view,
}
```

#### [PermissionTypes](gcdocsite__documentlink?toc-item-id=e6f27056-263d-43a1-b287-893153564386)

定义查看模式下的额外权限选项，支持通过位运算组合：

* `allowNonDataModifyingOperations = 1`：允许不修改数据的操作。
* `allowHideRowsOrColumns = 2`：允许隐藏或显示行/列。
* `allowResizeRowsOrColumns = 4`：允许调整行/列大小。
* `allowFilter = 8`：允许筛选区域。
* `allowSort = 16`：允许排序。

```typescript
/**
 * 定义权限类型
 * @enum {number}
 * @public
 */
export enum PermissionTypes {
  /**
    * 允许非数据修改操作
    */
  allowNonDataModifyingOperations= 1,
  /**
    * 允许隐藏或取消隐藏行/列。
    */
  allowHideRowsOrColumns= 2,
  /**
    * 允许调整行/列大小。
    */
  allowResizeRowsOrColumns= 4,
  /**
    * 允许筛选区域。
    */
  allowFilter= 8,
  /**
    * 允许排序。
    */
  allowSort= 16
}
```

## 用户功能

SpreadJS目前提供四个与**用户（User）** 相关的API：

* **[setUser](gcdocsite__documentlink?toc-item-id=e4a9efd9-777b-4fe2-835e-858bb442229c#setuser)**：绑定当前用户以使用其身份和权限。
* **[getUser](gcdocsite__documentlink?toc-item-id=e4a9efd9-777b-4fe2-835e-858bb442229c#getuser)**：获取当前用户。
* **[setPresences](gcdocsite__documentlink?toc-item-id=e4a9efd9-777b-4fe2-835e-858bb442229c#setpresences)**：同步其他协同用户的在线状态。
* **[getPresences](gcdocsite__documentlink?toc-item-id=e4a9efd9-777b-4fe2-835e-858bb442229c#getpresences)**：获取当前在线状态。

### setUser

**setUser**方法将用户绑定到当前工作簿实例，以使用该用户的身份和权限。**方法签名**

```typescript
/**
  * 设置当前用户。
  * @param {GC.Spread.Sheets.Collaboration.IUser} user 当前用户。
  * @example
  * ```
  * // 此示例设置当前用户。
  * let user = {
  *     id: '1',
  *     name: 'User1',
  *     color: '#FF0000',
  *     permission: {
  *         mode: GC.Spread.Sheets.Collaboration.BrowsingMode.edit,
  *     }
  * }
  * spread.collaboration.setUser(user);
  * ```
  */
setUser(user: GC.Spread.Sheets.Collaboration.IUser): void;
```

**参数user: GC.Spread.Sheets.Collaboration.IUser**要绑定到工作簿的用户对象，符合**IUser**接口定义。**功能说明**通过调用**setUser**方法，可将用户设置为当前工作簿实例的活跃用户。此操作决定了用户在工作簿中的身份和权限，适用于多用户协同编辑场景。绑定后，工作簿会根据用户权限限制或允许特定操作，用户的**id**、**name**和**color**属性可用于标识操作来源或在界面中显示用户状态。

### getUser

**getUser**方法用于获取当前用户。

```typescript
/**
  * 获取工作簿的用户
  * @returns {GC.Spread.Sheets.Collaboration.IUser}
  * @example
  * ```typescript
  * // 此示例获取当前用户。
  * const user = spread.collaboration.getUser();
  * ```
  */
getUser(): GC.Spread.Sheets.Collaboration.IUser;
```

### setPresences/getPresences

**setPresences/getPresences**方法主要用于多用户协同中显示其他用户的实时在线状态（如光标位置、选区等）。详情请见 [活动状态](gcdocsite__documentlink?toc-item-id=ad1912ee-5918-49d1-b1b0-9afdc8eba1b6)。