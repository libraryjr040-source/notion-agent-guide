# Chapter 7: 外部连接与集成 — Research Refs

## 核心技术点

### 1. 个人 Agent 的连接管理
- listUserConnections() → { connected, available }
- connected: 已激活连接，含 connectionStatus (ready / needs_connection / needs_permissions)
- available: 可用但未连接的集成和 MCP 服务器
- createUserConnection({ type, state?, permissions?, displayText? }) 添加新连接

### 2. 可连接类型 (UserConnectableType)
- Notion 原生: mail, calendar
- 第三方: slack, github, jira, linear, asana, discord, microsoftTeams
- 文档/存储: googleDrive, confluence, box, sharepoint
- 邮件/日历: gmail, outlook, googleCalendar
- CRM: salesforce
- 自定义: worker (自定义 worker), mcpServer

### 3. Notion Mail & Calendar
- mail 和 calendar 是 Notion 的原生连接器
- 不能连接多个 mail 或 calendar
- 优先推荐 mail 和 calendar 而非 gmail/outlook/googleCalendar

### 4. MCP 服务器
- type: "mcpServer", state: { serverUrl, name }
- 或 state: {} 让用户从列表选择
- available 列表中 moduleType: "mcpServer" 的条目
- MCP 工具: listTools() 和 runTool({ toolName, toolArguments })

### 5. 自定义 Agent 的集成
- 通过 updateAgent 的 integrations 字段配置
- 每个集成有 type, name, permissions, state
- 默认无权限，必须显式授权
- Web 搜索通过 Notion 模块的 web-search 权限配置

### 6. 搜索连接源
- search.search() 可搜索所有已连接源
- 支持的源类型: slack, gmail, google-drive, github, jira, etc.
- includeWebResults 控制是否包含网页结果

### 7. Web 模块
- web.search({ queries }) — 公开网页搜索
- web.loadPage({ url, fast_mode?, queries? }) — 加载网页内容
- 先用 fast_mode (默认)，不够再用 fast_mode: false

### 8. 通知
- sendNotification({ bodyContent, headerContent, userUrl?, sendToWorkflowOwner })
- bodyContent 限 100 字符

### 9. 子线程（Sub-agent threads）
- createAndRunThread 可让一个 Agent 调用另一个 Agent
- 个人 Agent 可调用自定义 Agent
- 自定义 Agent 只能调用自己或被授权的 Agent
- 每个父线程最多调用 50 次

## 确定性陷阱
1. mail ≠ gmail, calendar ≠ googleCalendar
2. MCP 服务器连接需要 serverUrl 和 name
3. 自定义 Agent 的集成权限与个人 Agent 的连接是两套体系
4. web.loadPage 先用 fast_mode，内容不够再用慢模式
