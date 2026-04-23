# Official Docs — Module Files 索引

> 本书涉及的所有 Notion module files 及其一句话描述。
> 写作时需要查阅某个主题，从这里找到对应的文件。

## 核心入口

| 文件路径 | 描述 |
|----------|------|
| `modules/notion/AGENTS.md` | Notion 模块总入口，概念定义 + 文件路由 |
| `modules/notion/index.ts` | 完整模块 API 表面，所有导出类型 |

## 页面相关

| 文件路径 | 描述 |
|----------|------|
| `modules/notion/pages/AGENTS.md` | 页面操作指南：parent 类型、属性格式、模板、移动 |
| `modules/notion/pages/index.ts` | 页面函数签名：loadPage, createPage, updatePage, deletePages 等 |
| `modules/notion/pages/page-content-spec.md` | 页面内容规范：Markdown 格式、Presentation Mode、database blocks |
| `modules/notion/notion-markdown.md` | Notion-flavored Markdown 完整语法参考 |

## 数据库相关

| 文件路径 | 描述 |
|----------|------|
| `modules/notion/databases/AGENTS.md` | 数据库操作指南：概念、CREATE-* 标识符、链接数据库、Wiki |
| `modules/notion/databases/index.ts` | 数据库函数签名：createDatabase, updateDatabase, loadDatabase 等 |
| `modules/notion/databases/dataSourceTypes.ts` | 所有属性类型定义（25+ 种），DataSource 和 Schema 类型 |
| `modules/notion/databases/viewTypes.ts` | 所有视图类型定义：table, board, calendar, chart, dashboard 等 |
| `modules/notion/databases/data-source-sqlite-tables.md` | SQL 查询指南：列映射、值编码、querySql 和 queryView |
| `modules/notion/databases/query.ts` | 查询类型定义：QuerySql, QueryView, Filter 等 |
| `modules/notion/databases/formula-spec.md` | 公式属性语法规范 |
| `modules/notion/databases/layoutTypes.ts` | 页面布局类型定义 |

## Agent 相关

| 文件路径 | 描述 |
|----------|------|
| `modules/notion/agents/AGENTS.md` | Agent 操作指南：Custom Agent、Autofill Agent |
| `modules/notion/agents/agent-setup-guide.md` | Agent 配置完整流程：创建、集成、权限、触发器、测试 |
| `modules/notion/agents/autofill-agent-setup-guide.md` | Autofill Agent 配置指南 |
| `modules/notion/agents/index.ts` | Agent 类型定义：Agent, AgentConfiguration, createAgent, updateAgent |

## 搜索相关

| 文件路径 | 描述 |
|----------|------|
| `modules/search/AGENTS.md` | 搜索模块指南：query 编写、lookback、连接源搜索 |
| `modules/search/index.ts` | 搜索类型定义：SearchInput, SearchResult |

## MCP 相关

| 文件路径 | 描述 |
|----------|------|
| `modules/mcpServer/AGENTS.md` | MCP 模块指南：listTools/runTool 用法 |
| `modules/mcpServer/index.ts` | MCP 类型定义：RunToolInput, McpServerToolCallResult |

## Thread 相关

| 文件路径 | 描述 |
|----------|------|
| `modules/notion/threads/index.ts` | Thread 函数：queryThreads, investigateThread, createAndRunThread |

## 其他

| 文件路径 | 描述 |
|----------|------|
| `modules/system/index.ts` | 系统工具：updateTodos 进度追踪 |
| `modules/web/AGENTS.md` | Web 模块：搜索和页面加载 |
| `modules/helpdocs/AGENTS.md` | Notion 帮助文档搜索 |
