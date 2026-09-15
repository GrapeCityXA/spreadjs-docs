# ai-assistant

SpreadJS AI 插件提供了一个框架，通过提供上下文电子表格数据和解析能力来增强 AI 交互。这使得 AI 模型能够生成更准确且针对电子表格的回复。

## 安装与设置

### 添加 AI 插件

要在 SpreadJS 中启用 AI 功能，你必须在项目中包含 AI 插件脚本。

#### 对于在头部引用的实现方式：

```html
<script src="gc.spread.sheets.ai.x.x.x.min.js"></script>
```

#### 对于模块实现方式

```javascript
import '@grapecity-software/spread-sheets-ai-addon';
```

### 上下文智能

SpreadJS 智能地提取和组织工作表数据，为 AI 模型提供相关上下文，从而产生更精确的输出。
**示例场景**：

* *无上下文*：AI 猜测数据范围 (`=SUM(A1:A10)`)
* *有上下文*：AI 引用命名范围 (`=SUM(table1[sales])`)

## AI 模型集成方法

SpreadJS 提供了灵活的方法来连接 AI 模型。以下是详细的实现方法：

### 1\. 安全后端代理

如果你不接受公开 API 密钥，可以选择将请求发送到服务器并返回响应数据。
*最安全的方法 - 将 API 密钥保留在服务器端*

#### 前端实现：

```javascript
const backendAIProxy = async (request) => {
    // 添加 SpreadJS 元数据
    request.metadata = {
        spreadsheetId: workbook.getActiveSheet().name(),
        userId: currentUser.id,
        timestamp: new Date().toISOString()
    };
    
    const response = await fetch('/api/spreadjs-ai', {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json',
            'X-Request-ID': generateUUID()
        },
        body: JSON.stringify(request)
    });
    
    if (!response.ok) {
        const error = await response.json();
        throw new Error(error.message || 'AI 请求失败');
    }
    
    return response;
};

workbook.injectAI(backendAIProxy);
```

#### 后端实现（Node.js）：

```javascript
const { OpenAI } = require('openai');
const express = require('express');
const app = express();

// 初始化 AI 客户端
const aiClient = new OpenAI({
    apiKey: process.env.OPENAI_API_KEY,
    organization: process.env.ORG_ID,
    timeout: 30000
});

// AI 代理端点
app.post('/api/spreadjs-ai', async (req, res) => {
    try {
        // 1. 请求验证
        if (!req.body.messages ||!Array.isArray(req.body.messages)) {
            return res.status(400).json({ error: '无效的请求格式' });
        }

        // 2. 使用自定义逻辑处理请求
        const completion = await aiClient.chat.completions.create({
            model: req.body.model || 'gpt-4-turbo',
            messages: req.body.messages,
            temperature: req.body.temperature || 0.5,
            max_tokens: req.body.max_tokens || 1000,
            stream: false
        });

        // 3. 日志分析
        logAnalytics(req.body.metadata, completion.usage);

        // 4. 返回格式化的响应
        res.json({
            success: true,
            data: completion.choices[0].message.content,
            usage: completion.usage
        });
        
    } catch (error) {
        console.error('AI 处理错误:', error);
        res.status(500).json({ 
            error: error.message,
            type: error.type || 'ai_service_error' 
        });
    }
});
```

### 2\. 直接 API 配置

如果你不介意在 HTTP 请求体中公开 AI 配置（*不建议公开你的 API 密钥*），可以选择将配置作为环境变量注入。

```javascript
// 初始化 SpreadJS 工作簿
const workbook = new GC.Spread.Sheets.Workbook('ss');

// 直接配置 AI 服务凭证
workbook.injectAI({
    model: 'gpt-4-turbo',  // 指定你的 AI 模型
    key: 'sk-your-api-key-here',  // 你的 API 密钥
    basePath: 'https://api.openai.com/v1',  // API 端点
    
    // 可选的高级参数
    organization: 'your-org-id',  // 对于 OpenAI 组织
    timeout: 30000,  // 请求超时时间（毫秒）
    defaultTemperature: 0.7  // 默认的创意等级
});
```

### 3\. 自定义客户端处理程序

如果你不介意在 HTTP 请求体中公开 AI 配置（*不建议公开你的 API 密钥*），但想检查请求体是否包含敏感数据并执行数据清理等操作，你可以这样做。

```javascript
const aiHandler = async (requestConfig) => {
    // 1. 添加所需的模型配置
    requestConfig.model = 'gpt-4-turbo';
    
    // 2. 数据清理（示例）
    const sanitizedMessages = requestConfig.messages.map(msg => ({
       ...msg,
        content: msg.content.replace(/credit-card-\d{4}/g, '****')
    }));
    
    // 3. 自定义头部和参数
    const requestOptions = {
        method: 'POST',
        headers: {
            'Authorization': `Bearer ${API_KEY}`,
            'Content-Type': 'application/json',
            'X-SpreadJS-Version': '16.0.0'
        },
        body: JSON.stringify({
           ...requestConfig,
            messages: sanitizedMessages
        })
    };
    
    // 4. 带有重试逻辑的错误处理
    let retries = 3;
    while (retries > 0) {
        try {
            const response = await fetch('https://api.openai.com/v1/chat/completions', requestOptions);
            if (!response.ok) throw new Error(`HTTP ${response.status}`);
            return response;
        } catch (error) {
            if (--retries === 0) throw error;
            await new Promise(resolve => setTimeout(resolve, 1000));
        }
    }
};

workbook.injectAI(aiHandler);
```

## 语言本地化

SpreadJS 会自动以工作簿的当前语言请求 AI 回复：

```javascript
let culture = GC.Spread.Common.CultureManager.culture(); 
let language = GC.Spread.Common.CultureManager.getCultureInfo(culture).displayName 

// 在提示中
// '请用这种语言返回答案: ' + language;
```

## 安全最佳实践

1. **数据保护**：
    * 始终对敏感的电子表格数据进行清理
    * 考虑在回调中对字段进行编辑删除
2. **凭证安全**：
    * 不建议在客户端代码中直接公开 API 密钥。
    * 在生产环境中使用服务器代理
3. **验证**：
    * 验证所有由 AI 生成的公式/内容
    * 实施输出清理

> **AI 生成内容免责声明**
> 
> **1\. 内容生成风险**
> 本服务利用用户注入的第三方 AI 模型来生成输出。由于模型架构和训练数据的固有局限性，结果可能包含不准确、遗漏或误导性内容。虽然我们实施了 **提示工程** 和技术限制来优化输出，但我们无法消除由模型基本缺陷带来的所有错误风险。
> 
> **2\. 用户验证义务**
> 通过使用本服务，你确认并同意：
>
> * 对所有生成的内容进行手动验证
> * 避免在高风险场景（法律、医疗、金融等）中使用未经验证的输出
> * 对于因依赖生成内容而导致的任何直接/间接损害，使我们免于承担责任
>
> **3\. 技术限制**
> 对于以下情况，我们不承担责任：
>
> * 由第三方模型缺陷或逻辑错误导致的输出失败
> * 通过容错程序进行的错误恢复尝试未成功
> * 当前 AI 技术固有的技术限制
>
> **4\. 知识产权合规**
> 你必须确保：
>
> * 注入的模型/内容不侵犯第三方权利
> * 不通过本服务处理任何非法/敏感材料
> * 遵守模型提供商的知识产权协议
>
> **5\. 协议更新**
> 我们保留修改这些条款的权利，以符合：
>
> * 技术进步（例如新的 AI 安全协议）
> * 法规变化（例如更新的 AI 治理框架）
> * 服务架构改进