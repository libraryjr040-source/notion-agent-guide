# Chapter 5: 搜索与信息获取 — Research Refs

## 核心技术点

### 1. 搜索模块（search module）
- search({ queries, includeWebResults? }) 跨 Notion + 连接源 + 互联网
- 每个 query: question + keywords + lookback + includeNotionHelpdocs
- lookback: "default" / "all_time" / "7d" / "2w" / "3m" / "1y" / ISO date
- includeWebResults 默认 true，设 false 只搜内部
- 搜索结果类型：block / page / slack / gmail / google-drive / github / jira / webpage 等
- 支持语义搜索，不仅仅是关键词匹配

### 2. Web 模块
- web.search({ queries }) 纯互联网搜索
- web.loadPage({ url }) 抓取网页内容
- 支持 category 过滤（news / research paper / github 等）
- 支持 domain 白名单/黑名单
- loadPage 先用 fast_mode，不够再用慢模式

### 3. 连接源（Connectors）
- 搜索可覆盖的外部工具：Slack, Google Drive, GitHub, Jira, Gmail, Google Calendar, Outlook, SharePoint, Salesforce, Discord, Asana, Linear, Box 等
- 需要在 Notion 设置中先连接这些服务

### 4. 搜索策略
- 简单请求用单个 query
- 复杂请求用多个不同 query
- 修正明显错别字但不过度纠正
- 相对日期转为具体值（"上周" → "7d"）
- 模糊时间词（"最近"）从 1w 开始，逐步扩大
- Notion 产品帮助设 includeNotionHelpdocs: true

### 5. Notion 帮助文档（helpdocs）
- 用于 Notion 产品使用问题
- search 模块的 includeNotionHelpdocs 参数
- 也有独立的 helpdocs 模块

## 确定性陷阱
1. 搜索默认包含互联网结果——可能引入不相关信息
2. 连接源需要先在设置中配置——Agent 无法替你连接
3. 搜索结果有数量限制，不一定返回所有匹配
4. 网页抓取可能被截断，需要用 line_start 翻页
5. 日历搜索结果中的时间是 UTC，需要转换时区
