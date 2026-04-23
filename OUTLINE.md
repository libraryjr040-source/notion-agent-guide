# OUTLINE.md

## 目标读者

Notion 用户（已会用 Notion 基本功能：创建页面、使用数据库），想要系统学习 Notion Agent 的人。
不要求编程基础，但有编程经验的读者会在 Ch4（SQL）和 Ch8（MCP）中获得额外收益。

## 全书定位

使用指南（非权威参考手册）。以「通俗易懂 + 可操作性」为核心目标。
允许不完美，但在每章末尾和全书结尾显式声明盲区。

## 认知层级体系

全书按三层认知递进编排：
1. **使用者**（Ch1-5）：学会用 Agent 完成日常任务
2. **创造者**（Ch6-8）：学会创建和配置自定义 Agent
3. **架构师**（Ch9-10）：学会设计复杂的多 Agent 协作体系

---

## 章节结构

### Chapter 1: Notion Agent 是什么

- **摘要**: 介绍 Notion Agent 的核心概念：什么是 Personal Agent、它能做什么（操作页面、数据库、搜索、连接外部工具）、不能做什么（不能做管理员操作、不能访问未授权的内容）。建立读者对 Agent 能力边界的正确期望。
- **章节依赖**: 无
- **预估字数**: 3000-4000
- **认知层级**: 概念入门
- **教学目标**: 读完后，读者知道 Agent 是什么、能做什么、不能做什么，以及本书的阅读路径
- **关键概念引入**: Workspace, Page（概念）, Agent（概念）, Database（概念）, Teamspace
- **对应 module files**: notion/AGENTS.md, agents/AGENTS.md, index.ts

### Chapter 2: 你的第一次对话

- **摘要**: 手把手带读者完成第一次与 Agent 的对话。从打开对话框开始，演示如何用自然语言让 Agent 创建页面、搜索信息、回答问题。讲解对话的基本机制：Thread（线程）、上下文记忆、Agent 的工具调用过程。
- **章节依赖**: Ch1
- **预估字数**: 3500-4500
- **认知层级**: 单元操作
- **教学目标**: 读完后，读者能独立发起对话、让 Agent 创建简单页面、使用搜索
- **关键概念引入**: Conversation/Thread, Search（初步使用）
- **对应 module files**: notion/index.ts, search/AGENTS.md, search/index.ts, pages/AGENTS.md

### Chapter 3: 页面操作全攻略

- **摘要**: 深入讲解 Agent 对页面的所有操作能力：创建页面（各种 parent 类型）、编辑内容（oldStr/newStr 模式）、设置属性、移动页面、管理子页面。重点讲解 Notion-flavored Markdown 的常用语法。包含常见错误和陷阱。
- **章节依赖**: Ch1, Ch2
- **预估字数**: 5000-6000
- **认知层级**: 单元操作
- **教学目标**: 读完后，读者能让 Agent 完成复杂的页面编辑任务，理解内容格式的基本规则
- **关键概念引入**: Page（详细）, Block, Notion-flavored Markdown, Property（基本）, Sharing（基本）
- **对应 module files**: pages/AGENTS.md, pages/index.ts, page-content-spec.md, notion-markdown.md

### Chapter 4: 数据库操作全攻略

- **摘要**: 全书最长章节。讲解 Database 的完整概念体系（Database → Data Source → Schema → Property → View），以及 Agent 能执行的所有数据库操作：创建数据库、设计属性、配置视图、查询数据（queryView 和 querySql）、更新页面属性。重点讲解 Data Source 这个容易混淆的概念。
- **章节依赖**: Ch1, Ch2, Ch3
- **预估字数**: 7000-8500
- **认知层级**: 单元操作 → 跨源操作
- **教学目标**: 读完后，读者能让 Agent 创建完整的数据库、设计属性和视图、用 SQL 查询数据
- **关键概念引入**: Database（详细）, Data Source, Schema, Property Type, View, View Type, Filter/Sort, Template, SQL Query
- **对应 module files**: databases/AGENTS.md, databases/index.ts, dataSourceTypes.ts, viewTypes.ts, data-source-sqlite-tables.md, query.ts

### Chapter 5: 搜索与连接器

- **摘要**: 深入讲解 Agent 的搜索能力：搜索语法（question, keywords, lookback）、跨源搜索（Notion + Slack + Google Drive + GitHub + Web）、搜索策略（何时搜、搜什么、怎么优化）。讲解各种 Connector 的特点和搜索结果格式。
- **章节依赖**: Ch1, Ch2
- **预估字数**: 4000-5000
- **认知层级**: 跨源操作
- **教学目标**: 读完后，读者能有效利用搜索功能，理解不同连接源的搜索能力差异
- **关键概念引入**: Search（详细）, Connector
- **对应 module files**: search/AGENTS.md, search/index.ts

### Chapter 6: 打造你的 Custom Agent

- **摘要**: 从 Personal Agent 过渡到 Custom Agent。讲解为什么需要 Custom Agent（权限隔离、专职化、可复用）、如何创建（createAgent）、如何配置指令页面、如何添加集成（Integration）和权限。重点强调「最小权限原则」。
- **章节依赖**: Ch1-5（所有基础操作）
- **预估字数**: 5000-6000
- **认知层级**: 创造者视角
- **教学目标**: 读完后，读者能独立创建一个 Custom Agent 并正确配置其权限和指令
- **关键概念引入**: Custom Agent, Instructions, Integration
- **对应 module files**: agents/AGENTS.md, agents/agent-setup-guide.md, agents/index.ts

### Chapter 7: 自动化与高级技能

- **摘要**: 讲解如何让 Agent 自动工作：Trigger 的各种类型（定时、事件驱动、按钮、@ 提及）、Autofill Agent 的创建和使用、Skill 模式（如何用结构化指令让 Agent 学会复杂任务）。
- **章节依赖**: Ch6
- **预估字数**: 5000-6000
- **认知层级**: 创造者视角
- **教学目标**: 读完后，读者能配置触发器、创建 Autofill Agent、理解 Skill 的设计模式
- **关键概念引入**: Trigger, Skill, Autofill Agent
- **对应 module files**: agents/AGENTS.md, agents/autofill-agent-setup-guide.md, notion/triggers.ts (type definitions)

### Chapter 8: MCP 集成——让 Agent 连接世界

- **摘要**: 讲解 MCP（Model Context Protocol）的概念和使用方法。如何让 Agent 通过 MCP 调用外部工具（以 GitHub MCP 为实例）：listTools 查看可用工具、runTool 执行工具、处理工具结果。讲解 MCP Server 的配置和常见问题。
- **章节依赖**: Ch6
- **预估字数**: 4000-5000
- **认知层级**: 创造者视角 → 系统架构
- **教学目标**: 读完后，读者能通过 MCP 让 Agent 与 GitHub 等外部服务交互
- **关键概念引入**: MCP, MCP Tool
- **对应 module files**: mcpServer/AGENTS.md, mcpServer/index.ts

### Chapter 9: 高级模式——多 Agent 协作

- **摘要**: 讲解 Agent 的高级使用模式：Sub-thread（子线程）的创建和使用、多 Agent 间的协作（Personal Agent 调用 Custom Agent）、复杂工作流的设计（以「三省六部」体系为案例）。讲解 Thread 的限制（50 次子线程上限）。
- **章节依赖**: Ch6, Ch7
- **预估字数**: 5000-6000
- **认知层级**: 系统架构
- **教学目标**: 读完后，读者理解多 Agent 协作的设计模式，能设计自己的多 Agent 工作流
- **关键概念引入**: Sub-thread
- **对应 module files**: threads/index.ts, 皇上的三省六部体系实例

### Chapter 10: 最佳实践与踩坑指南

- **摘要**: 综合前 9 章的知识，总结实战经验：常见错误及其原因（属性名大小写、wiki 数据库创建页面的特殊 parent、oldStr 匹配失败等）、性能优化（避免冗余 loadPage、合并 updatePage 调用）、Prompt 技巧（如何让 Agent 更准确地理解意图）。
- **章节依赖**: Ch1-9
- **预估字数**: 4000-5000
- **认知层级**: 综合应用
- **教学目标**: 读完后，读者知道最常见的坑在哪里，以及如何避免
- **关键概念引入**: （无新概念，综合应用）
- **对应 module files**: 全部（交叉引用），自测结果 + web search + 皇上使用历史

### Appendix A: Notion-flavored Markdown 速查表

- **摘要**: 以速查卡片形式，列出 Notion-flavored Markdown 的所有 Block 类型和 Rich Text 格式语法。按使用频率排序，常用的在前。每个语法给出最小示例。
- **章节依赖**: Ch3
- **预估字数**: 2500-3500
- **认知层级**: 参考
- **教学目标**: 需要时能快速查找正确语法
- **关键概念引入**: （无新概念）
- **对应 module files**: notion-markdown.md

### Appendix B: 属性类型速查表

- **摘要**: 以速查卡片形式，列出所有 25+ 种属性类型的定义方式（dataSourceTypes.ts）和查询方式（SQL 列映射）。每种类型给出创建示例、赋值示例、查询示例。
- **章节依赖**: Ch4
- **预估字数**: 3000-4000
- **认知层级**: 参考
- **教学目标**: 需要时能快速查找属性类型的正确用法
- **关键概念引入**: （无新概念）
- **对应 module files**: dataSourceTypes.ts, data-source-sqlite-tables.md
