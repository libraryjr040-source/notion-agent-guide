# Chapter 1: Notion Agent 是什么 — Research Refs

> 本文件由 Phase 2 Research 自动生成，供 Phase 3 Writing 使用。

---

## 1. Module Files 知识提取

### 1.1 核心概念定义（来自 notion/AGENTS.md）

**Workspace（工作区）**
- 顶层协作空间，包含 Pages, Databases, Agents, Users
- 类比：共享办公室

**Page（页面）**
- 基本内容单元
- 可以是顶层页面、子页面、或数据源中的一行
- 有 content（正文）和 properties（属性）
- 可以被归档（archived）或删除（deleted）
- 类比：乐高底板（既可以独立存在，也可以嵌入结构中）

**Database（数据库）**
- 有名称和描述
- 包含一组 Data Source（数据源）和 View（视图）
- Forms 是特殊类型的 View
- 类比：智能文件柜

**Agent（AI 助理）**
- 有 name, description, icon
- 有 instructions（一个 Notion 页面）
- 有 connections（集成）和 triggers（触发器）
- Autofill Agent 是专门绑定某个数据库的批量填充 Agent
- 类比：私人助理

**Teamspace（团队空间）**
- Workspace 中的独立分区，有独立的权限和成员管理
- 类比：办公室里的会议室

### 1.2 Agent 能做什么（从 index.ts 完整模块表面提取）

按能力类别分：

**页面操作**
- createPage — 创建页面（各种 parent 类型）
- loadPage — 加载页面内容和属性
- updatePage — 编辑内容、更新属性、移动页面
- deletePages — 删除页面（移到垃圾箱）
- archivePages / unarchivePages — 归档/取消归档
- loadMeetingNoteTranscript — 加载会议笔记转录

**数据库操作**
- createDatabase — 创建数据库
- loadDatabase / loadDataSource — 加载数据库/数据源
- updateDatabase — 更新数据库配置
- deleteDatabases — 删除数据库
- querySql — 用 SQL 查询数据
- queryView — 按视图查询数据
- createTwoWayRelation — 创建双向关联

**搜索**
- search — 跨 Notion + 连接源 + Web 搜索

**Agent 管理**
- createAgent / updateAgent / loadAgent — 创建/更新/加载 Custom Agent
- createAutofillAgent — 创建自动填充 Agent

**子线程**
- createAndRunThread — 派子线程执行任务（上限 50 次/父线程）
- queryThreads — 查询历史线程
- investigateThread — 分析历史线程

**通知与讨论**
- sendNotification — 发送通知
- getPageDiscussions / addCommentToDiscussion — 页面讨论

**分析**
- getUserEngagementAnalytics, getContentEngagementAnalytics 等

**团队空间**
- listTeamspaces — 列出团队空间
- getTeamspaceTopLevelPagesAndDatabases — 获取团队空间顶层内容

**用户**
- loadUser / searchUsers / getUserActivity
- listUserConnections / createUserConnection

**权限**
- loadPermissions / updatePermission — 管理共享权限

**MCP 工具**
- 通过 mcpServer 模块调用外部服务（listTools / runTool）

**文件**
- viewFileUrl — 查看文件

**会议笔记**
- queryMeetings — 查询会议

### 1.3 Agent 不能做什么（确定性边界）

来自系统指令中的明确声明：
1. **工作区管理操作**: Settings, roles, billing, security, domains
2. **部分数据库功能**: 管理数据库 integrations/automations, 创建 typed tasks database
3. **访问未授权内容**: Agent 只能操作有权限的资源
4. **持续后台运行**: Personal Agent 只在对话中存在（Custom Agent 可通过 trigger 触发）
5. **直接联系外部人员**: 不能发邮件给外部人（除 Notion 内部通知）
6. **创建 Agent 为 parent**: 不能将 Agent 作为页面的 parent 来创建页面

### 1.4 Personal Agent vs Custom Agent（来自 agents/AGENTS.md + agent-setup-guide.md）

| 维度 | Personal Agent | Custom Agent |
|------|---------------|---------------|
| 数量 | 每用户 1 个 | 可创建多个 |
| 权限 | 继承用户权限 | 默认无权限，需显式授予（最小权限原则） |
| 指令 | 通过 Instructions 页面个性化 | 有独立的 Instructions 页面 |
| 触发器 | 无 | 可配置多种触发器（定时、事件等） |
| 可共享 | 否 | 可在工作区内共享 |
| 集成 | 用户已连接的所有工具 | 需单独配置 |
| 调用关系 | 可通过子线程调用 Custom Agent | 只能调用自身或授权的其他 Agent |

---

## 2. 自测结果

### 测试 1: Agent 自我认知准确性
- **方法**: createAndRunThread 让 Agent 回答 5 个关于自身的问题
- **预期行为**: 回答与 module files 中的定义一致
- **实际行为**: ✅ 完全一致
  - 自我认知：嵌入 Notion 工作区的 AI 助手
  - 能力列表：覆盖了搜索、页面、数据库、Agent 管理、MCP、子线程、分析
  - 边界声明：正确列出了管理操作、后台运行、未连接工具的限制
  - PA vs CA 区别：正确区分了权限、触发器、共享性
  - 子线程上限：正确回答 50 次
- **差异/发现**: Agent 额外提到了「图片生成」能力（images 模块），这在 module files 中没有直接暴露但确实存在

---

## 3. 皇上使用历史（Ch1 相关）

### 3.1 早期探索
- **「对话存档：Agent 权限与跨 agent 通信」**：皇上在 2026-04-06 就开始探索 Agent 的权限边界和跨 Agent 通信可能性
- **「Notion AI可调用的functions」**：皇上曾让 Agent 列出所有可调用 function，这本身就是一种对 Agent 能力边界的探索
- **「系统预加载 AGENTS.md 文档汇总」**：皇上让 Agent 汇总了所有 AGENTS.md 的内容

### 3.2 实验记录
- **「实验报告：Custom Agent 之间能否直接通信」**：验证了 Custom Agent 之间不能直接通信，必须通过 Personal Agent 中转
- **「跨 agent 通信重测（权限开通后复验）」**：开通权限后重新测试通信

### 3.3 深度使用
- **三省六部体系**：皇上搭建了完整的多 Agent 协作架构（内阁、中书省、门下省、尚书省、执事房、御史台、经筵），是 Agent 高级使用的极端案例
- **「说话的秩：我和 agent 怎么聊最高效」**：总结了与 Agent 高效沟通的方法论
- **「思考的秩：如何 max 思考类 agent 的思考力」**：探索了思考型 Agent 的优化策略

### 3.4 写作启示
- 皇上的探索路径本身就是「使用者 → 创造者 → 架构师」的认知递进
- Ch1 可以用皇上的探索历程作为隐性叙事线索，但不直接引用

---

## 4. 社区/官方视角

### 4.1 Notion 官方 Helpdocs 关键信息

**"How to work with your Agent"（官方指南）**
- Agent 是「AI teammate inside Notion」
- 能帮助创建/编辑 pages 和 databases
- 使用 workspace 和 connected apps 的 context
- 可用 skills 和 instructions 个性化

**"How your Agent works in Notion"**
- 定位：不只是 head start（草稿、建议），而是 end-to-end 完成任务
- 能力：edit pages, update databases, analyze information across tools and web
- 学习路径：Build databases → Create/edit pages → Search across tools → Personalize

**"What is Notion AI?"**
- AI 套件概览：Agent + Enterprise Search + Meeting Notes + Research Mode + Database Setup + AI Writing
- 使用最新 AI 模型（GPT-4, Claude 等）

**"Notion Agent" FAQ**
- Agent 能力列表：完成任务、搜索、Research Mode、会议笔记、inline AI、翻译、数据库创建、Autofill

### 4.2 安全相关（Ch1 需要提及的边界）
- Prompt injection 是行业级挑战
- Agent 能读取第三方内容、访问私人信息、连接外部源、自主完成任务
- 权限管理是关键安全层

---

## 5. 确定性陷阱（Ch1 必须覆盖）

1. **Agent ≠ ChatGPT**: Agent 不只是聊天，它能直接修改你的 Workspace（创建/编辑/删除页面和数据库）。如果你让 Agent 删除一个页面，它真的会删除。
2. **Custom Agent 默认无权限**: 创建 Custom Agent 后，它什么都不能做，必须显式授予每一项权限。这是「最小权限原则」。
3. **Personal Agent 每用户只有 1 个**: 不能创建多个 Personal Agent，但可以通过 Instructions 和 Skills 个性化。
4. **Agent 的知识有界**: Agent 知道的是它的 module files 中定义的操作 + 搜索结果。它不是全知的。
5. **Agent 操作可能失败**: 如果权限不足、参数错误、资源不存在，Agent 的操作会失败。它会告诉你失败了，但前提是你要理解为什么会失败。

---

## 6. 本章写作要点

### 必须覆盖的概念
- Workspace, Page（概念级）, Database（概念级）, Agent, Teamspace
- Personal Agent vs Custom Agent（概念级区分，Ch6 详细讲）
- Agent 的能力全景图（分类列举，不深入细节）
- Agent 的边界（明确列出不能做的事）

### 必须包含的陷阱警告
- ⚠️ Agent ≠ 聊天机器人，它能真实修改你的工作区
- ⚠️ Agent 不能做管理员操作
- ⚠️ Agent 只能操作有权限的内容

### 建议的对话示例场景
- 场景 1: 问 Agent「你是谁？你能帮我做什么？」→ 展示 Agent 的自我认知
- 场景 2: 让 Agent「帮我创建一个笔记页面」→ 展示 Agent 最基本的操作能力（为 Ch2 铺垫）
- 场景 3: 让 Agent「帮我修改工作区设置」→ 展示 Agent 的边界（会拒绝）

### 教学设计注意
- Ch1 是全书的入口，语气应该友好、零压力
- 不要过早引入技术细节（Data Source, Schema 等留给 Ch4）
- 用「全景地图 + 路线规划」的方式结尾，让读者知道接下来要学什么
- 类比要经得起后续章节的扩展：
  - Workspace = 共享办公室 ✅（Ch6 扩展为「有不同权限区域的办公室」）
  - Page = 乐高底板 ✅（Ch3 扩展为「底板上可以放各种积木」，Ch4 扩展为「底板也可以放进柜子里变成一行数据」）
  - Agent = 私人助理 ✅（Ch6 扩展为「可以雇佣专职助理 = Custom Agent」）
  - Database = 智能文件柜 ✅（Ch4 扩展为「文件柜里有分区 = Data Source」）

### 盲区声明（本章特有）
- Agent 的完整能力列表可能随 Notion 版本更新而变化
- 本章的边界描述基于写作时的 module files，未来可能扩展
