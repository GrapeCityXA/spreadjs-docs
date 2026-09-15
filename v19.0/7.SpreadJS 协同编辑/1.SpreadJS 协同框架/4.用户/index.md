# user

为支持协作功能，SpreadJS 的**通用（Common）模块引入了**[UserManager（用户管理器）](gcdocsite__documentlink?toc-item-id=e48c2c7a-7589-4559-bb38-25b37d7f47f0) 概念，将用户定义为\*\*[IUser（用户接口）](gcdocsite__documentlink?toc-item-id=4eb008cf-f54b-4728-b719-45c4e6090af4)\*\* 以简化用户管理操作。该模块同时提供了针对文档的用户访问权限配置项。本文档将对协作功能中与用户相关的特性进行详细说明。

## 用户能力

SpreadJS 目前为用户提供以下相关功能：

* **设置当前用户**：绑定当前用户并使用其身份信息。
* **获取当前用户**：获取指定用户的相关信息。
* **setPresences**：同步其他协作用户的在线状态信息。
* **getPresences**：获取当前在线状态信息。

### 设置当前用户

**[GC.Spread.Common.UserManager.current](gcdocsite__documentlink?toc-item-id=e48c2c7a-7589-4559-bb38-25b37d7f47f0#current)** 方法可将用户绑定至当前环境，从而使用该用户的身份信息。

```typescript
const loginUserId = 'userID1';
GC.Spread.Common.UserManager.current(loginUserId);
```

**说明**：调用\*\*[UserManager.current](gcdocsite__documentlink?toc-item-id=e48c2c7a-7589-4559-bb38-25b37d7f47f0#current)\*\* 方法可将某一用户设为当前环境的活跃用户。该操作会确定用户身份，适用于多用户协同编辑场景。绑定完成后，可通过用户的 **id**、**name** 和 **color** 属性标识操作来源，或在界面中展示用户状态。

### 获取当前用户

**[GC.Spread.Common.UserManager.get](gcdocsite__documentlink?toc-item-id=e48c2c7a-7589-4559-bb38-25b37d7f47f0#get)** 方法可通过用户ID获取指定用户信息。结合 **UserManager.current** 方法使用，即可获取当前活跃用户的相关信息。

```auto
const currentUserID = GC.Spread.Common.UserManager.current();
const currentUserInfo = await GC.Spread.Common.UserManager.get(currentUserID);
```

### setPresences / getPresences

[setPresences](gcdocsite__documentlink?toc-item-id=e4a9efd9-777b-4fe2-835e-858bb442229c#setPresences)/[getPresences](gcdocsite__documentlink?toc-item-id=e4a9efd9-777b-4fe2-835e-858bb442229c#getpresences) 方法主要用于多用户协作场景，展示其他用户的实时在线状态（如光标位置、选区范围等）。
详情请参阅 [活动状态](gcdocsite__documentlink?toc-item-id=ad1912ee-5918-49d1-b1b0-9afdc8eba1b6)。