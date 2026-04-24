# Chapter 8: 高级技巧与最佳实践 — Research Refs

## 核心译自模块文档的最佳实践

### 1. 提示词工程
- 明确 > 模糊：给出具体的页面/数据库名称
- 分步 > 一口气：复杂任务拆成步骤
- 提供示例 > 抽象描述
- 说明输出格式偏好

### 2. 内容编辑技巧
- contentUpdates 的 oldStr/newStr 模式：精确替换 > 全量替换
- replaceAllMatches 用于批量查找替换
- 不要在 oldStr/newStr 中包含 <content> 标签
- 避免重复 loadPage：已加载的内容可复用

### 3. 数据库查询优化
- querySql 支持多表 JOIN
- 参数化查询防止注入
- json_each 处理数组字段（multi-select, relation, person）
- 始终包含 url 列以便后续操作

### 4. 视图与数据源分离
- 一个数据库可有多个数据源
- 视图可引用外部数据源（linked database）
- createDatabase 时 dataSources: {} + 外部 dataSourceUrl 创建 linked view

### 5. 搜索策略
- 关键词 2-4 个最具区分度的词
- lookback 用具体值，不用自然语言
- 多次搜索用不同关键词，而非重复同一查询
- includeWebResults: false 可只搜工作区

### 6. 模板与批量操作
- createPage 中 pageTemplate 可复制模板
- asTemplate: true 创建数据库模板
- 超过 20 行用 autofill agent

### 7. 分享与权限
- loadPermissions / updatePermission
- 支持 user / workspace / public 级别
- 自定义 Agent 权限通过 loadAgent/updateAgent 管理

### 8. 页面验证
- verification: { status: "verified" } / { status: "none" }
- 可设置过期天数 expirationDays
