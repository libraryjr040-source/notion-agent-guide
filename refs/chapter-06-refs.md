# Chapter 6: 自定义 Agent — Research Refs

## 核心技术点

### 1. Agent 结构
- agentUrl + instructionsPageUrl + configuration
- configuration: name, description, icon, integrations, triggers
- instructions 是一个普通 Notion 页面，通过 updatePage 修改

### 2. 创建 Agent
- createAgent({ name, description, icon, integrations, triggers })
- 返回 agentUrl + instructionsPageUrl
- icon 类型：agent_icon (shape+color) / emoji / url
- agent_icon shapes: triangle, square, bulb, chat, check, hat, globe, plug, sign, book, apple, file, ghost, unbrella, mailbox, puzzle, alarm, rock
- agent_icon colors: brown, orange, yellow, green, blue, purple, pink, red, gray

### 3. 集成（Integrations）
- 每个集成是一个模块实例（slack / github / notion / mail / calendar 等）
- 每个集成有独立的 permissions 和 state
- 自定义 Agent 默认没有任何权限（least privilege）
- 必须显式授权才能访问资源
- Web 访问通过 Notion 模块的 web-search 权限配置

### 4. 触发器（Triggers）
- 定时触发（RecurrenceTrigger）
- 数据库页面创建/更新/删除
- 评论添加
- 按钮点击
- 外部触发（Slack mention 等）

### 5. Autofill Agent
- createAutofillAgent({ dataSourceUrl, propertyNames, name, isLite })
- Lite mode (基础自动填充): 免费，只能用行数据，不能搜索/联网
- Full mode (自动填充 Agent): 消耗 AI 积分，支持搜索/联网/定时触发
- 用于超过 20 行的批量填充

### 6. 测试
- createAndRunThread 可以测试 Agent 行为
- 配置变更后必须测试

### 7. Instructions 编写规范
- 用清晰的标题和 emoji 组织
- 从概述开始，然后分节说明
- 不包含技术实现细节、API 名称、函数调用
- 不包含触发器调度和权限细节
- 只写 WHAT，不写 HOW

## 确定性陷阱
1. 自定义 Agent 默认无权限，必须显式授权
2. Instructions 不应包含技术实现细节
3. Autofill 超过 20 行必须用 autofill agent，不能批量 updatePage
4. 配置变更后必须测试
