# 概念依赖图（Concept Dependency Graph）

> 本文件是全书概念引入顺序的权威依据。写作时，每引入一个新概念，必须检查其前置概念是否已在前序章节出现。

## 拓扑排序（按引入顺序）

### Level 0 — 零依赖

#### 1. Workspace（工作区）
- **认知难度**: 1
- **使用频率**: 高
- **前置心智模型**: 读者可能以为 Workspace = 文件夹 → 实际上 Workspace 是一个协作空间，包含页面、数据库、成员、权限
- **首选教学类比**: 「公司的共享办公室」——所有人在同一空间工作，但各自有私人抽屉
- **首次引入**: Ch1

### Level 1 — 依赖 Workspace

#### 2. Page（页面）
- **认知难度**: 1
- **使用频率**: 高
- **前置心智模型**: 读者以为页面只是文档 → 实际上页面也可以是数据库中的一行，也可以包含子页面和数据库
- **首选教学类比**: 「乐高底板」——本身是一块板，但可以在上面搭各种积木（文字、数据库、子页面）
- **首次引入**: Ch1（概念提及），Ch3（详细讲解）

#### 3. Agent（Personal Agent / 个人 Agent）
- **认知难度**: 2
- **使用频率**: 高
- **前置心智模型**: 读者以为 Agent = ChatGPT 聊天机器人 → 实际上 Agent 能直接操作 Workspace 中的页面和数据库
- **首选教学类比**: 「私人助理」——不只会聊天，还能帮你跑腿（创建页面、查数据库、搜资料）
- **首次引入**: Ch1（概念），Ch2（实操）

#### 4. Teamspace（团队空间）
- **认知难度**: 1
- **使用频率**: 中
- **前置心智模型**: 读者以为 Teamspace = 子文件夹 → 实际上 Teamspace 有独立的权限和成员管理
- **首选教学类比**: 「办公室里的会议室」——属于大办公室，但有自己的门禁
- **首次引入**: Ch1（提及），Ch3（使用）

### Level 2 — 依赖 Page / Agent

#### 5. Block（块）
- **认知难度**: 1
- **使用频率**: 高
- **前置心智模型**: 读者可能不知道 Notion 页面由 Block 组成 → 每个段落、标题、图片都是一个 Block
- **首选教学类比**: 「积木块」——页面就是一摞积木，每块可以是文字、图片、代码、表格等
- **首次引入**: Ch3

#### 6. Notion-flavored Markdown
- **认知难度**: 3
- **使用频率**: 高（Agent 内部表示）
- **前置心智模型**: 读者以为是标准 Markdown → 实际上有大量 Notion 特有扩展（callout, toggle, mention, table 等）
- **首选教学类比**: 「方言」——大体能懂标准 Markdown，但有很多地方说法不同
- **首次引入**: Ch3（核心讲解），附录 A（速查）

#### 7. Property（页面属性）
- **认知难度**: 2
- **使用频率**: 高
- **前置心智模型**: 读者以为属性 = 标签 → 实际上属性有严格的类型系统（文本、数字、日期、关联等 20+ 种）
- **首选教学类比**: 「表格的列头」——每个属性是一列的定义，决定这列能放什么数据
- **首次引入**: Ch3（页面属性），Ch4（数据库属性详解）

#### 8. Conversation / Thread（对话 / 线程）
- **认知难度**: 1
- **使用频率**: 高
- **前置心智模型**: 读者以为对话 = 无状态聊天 → 实际上每个 Thread 有上下文记忆，Agent 可以在对话中连续操作
- **首选教学类比**: 「电话通话」——一次通话（Thread）里你可以连续交代多件事，助理记得前面说过什么
- **首次引入**: Ch2

#### 9. Search（搜索）
- **认知难度**: 2
- **使用频率**: 高
- **前置心智模型**: 读者以为搜索只搜 Notion 内容 → 实际上可以跨 Slack、Google Drive、GitHub 等连接源搜索，也可搜 Web
- **首选教学类比**: 「万能搜索框」——一个入口搜遍你的所有工具
- **首次引入**: Ch2（初步使用），Ch5（详细讲解）

### Level 3 — 依赖 Page + Property / Search

#### 10. Database（数据库）
- **认知难度**: 3
- **使用频率**: 高
- **前置心智模型**: 读者以为 Database = MySQL/Excel → 实际上 Notion Database 是「页面的集合 + 结构化属性 + 多种视图」
- **首选教学类比**: 「智能文件柜」——每个抽屉（页面）都有统一的标签系统（属性），还能用不同方式排列查看（视图）
- **首次引入**: Ch1（概念），Ch4（详细讲解）

#### 11. Data Source（数据源）
- **认知难度**: 4
- **使用频率**: 中
- **前置心智模型**: 读者以为 Database = Data Source → 实际上一个 Database 可以有多个 Data Source，Data Source 才是拥有 Schema 的实体
- **首选教学类比**: 「文件柜里的分区」——同一个文件柜（Database）可以有不同的分区（Data Source），每个分区有自己的列定义
- **首次引入**: Ch4
- **⚠️ 教学风险**: 这是全书认知跳跃最大的概念之一，必须用具体例子铺垫

#### 12. Connector（连接源 / Connected Source）
- **认知难度**: 2
- **使用频率**: 中
- **前置心智模型**: 读者以为要手动配置 API → 实际上是 Notion 预集成的外部数据源（Slack、Google Drive 等）
- **首选教学类比**: 「翻译耳机」——戴上就能听懂外语（连上就能搜其他工具的数据）
- **首次引入**: Ch5

#### 13. Custom Agent（自定义 Agent）
- **认知难度**: 3
- **使用频率**: 中
- **前置心智模型**: 读者以为 Custom Agent = Personal Agent 的副本 → 实际上 Custom Agent 是独立的角色，有自己的权限、指令和触发器，默认无任何权限
- **首选教学类比**: 「专职员工」——Personal Agent 是你的私人助理，Custom Agent 是你雇来做特定工作的专员，需要明确授权才能动东西
- **首次引入**: Ch6

#### 14. Sub-thread（子线程 / createAndRunThread）
- **认知难度**: 4
- **使用频率**: 低
- **前置心智模型**: 读者以为 Agent 只能单线程工作 → 实际上可以启动子线程让分身并行/串行执行任务
- **首选教学类比**: 「派出去跑腿的小弟」——主线程的 Agent 派一个分身去做子任务，做完回来汇报
- **首次引入**: Ch9

### Level 4 — 依赖 Database / Data Source / Custom Agent

#### 15. Schema（模式 / 属性定义）
- **认知难度**: 3
- **使用频率**: 中
- **前置心智模型**: 读者以为 Schema = 表头 → 实际上 Schema 包含属性类型、选项、格式、关联关系等完整定义
- **首选教学类比**: 「建筑蓝图」——决定了这栋楼（数据库）每层（属性）长什么样
- **首次引入**: Ch4

#### 16. Property Type（属性类型）
- **认知难度**: 3
- **使用频率**: 高
- **前置心智模型**: 读者以为只有文本和数字 → 实际上有 25+ 种类型（title, text, number, select, status, relation, formula, rollup...）
- **首选教学类比**: 「插座类型」——不同类型的插座只能插对应的插头，选错类型数据就放不进去
- **首次引入**: Ch4，附录 B（速查）

#### 17. View（视图）
- **认知难度**: 2
- **使用频率**: 高
- **前置心智模型**: 读者以为视图 = 排序/筛选 → 实际上视图是完全不同的呈现形式（表格、看板、日历、时间线、图表、地图...）
- **首选教学类比**: 「同一批照片的不同相册排列方式」——数据不变，展示方式完全不同
- **首次引入**: Ch4

#### 18. Filter / Sort（筛选 / 排序）
- **认知难度**: 2
- **使用频率**: 高
- **前置心智模型**: 读者以为只有简单的等于/包含 → 实际上支持复杂的组合筛选（and/or 嵌套）、相对日期等
- **首选教学类比**: 「筛子」——不同孔径的筛子组合使用
- **首次引入**: Ch4

#### 19. SQL Query / querySql
- **认知难度**: 4
- **使用频率**: 中
- **前置心智模型**: 读者以为要写标准 SQL → 实际上是 SQLite 方言，表名是数据源 URL，列名是属性名，值有特殊编码（如 checkbox = "__YES__"）
- **首选教学类比**: 「对文件柜的高级检索指令」——用结构化语言精确查找和统计数据
- **首次引入**: Ch4

#### 20. Instructions（Agent 指令页）
- **认知难度**: 2
- **使用频率**: 中
- **前置心智模型**: 读者以为指令 = prompt → 实际上指令是一个 Notion 页面，用自然语言写，给人和 AI 都能读
- **首选教学类比**: 「岗位说明书」——告诉专职员工（Custom Agent）该做什么、怎么做
- **首次引入**: Ch6

#### 21. Integration（Agent 集成）
- **认知难度**: 3
- **使用频率**: 中
- **前置心智模型**: 读者以为集成 = 连接外部工具 → 实际上集成是给 Agent 的一个能力模块，包含 Notion 本身、Slack、GitHub 等
- **首选教学类比**: 「工具箱里的工具」——每添加一个集成，就是给员工多发一把工具
- **首次引入**: Ch6

#### 22. Trigger（触发器）
- **认知难度**: 3
- **使用频率**: 中
- **前置心智模型**: 读者以为触发器 = 定时任务 → 实际上触发器可以是时间、事件（页面创建/更新）、按钮按下、被 @ 提及等多种类型
- **首选教学类比**: 「闹钟 + 门铃 + 对讲机」——不同类型的信号都能叫醒员工干活
- **首次引入**: Ch7

#### 23. Template（页面模板）
- **认知难度**: 2
- **使用频率**: 中
- **前置心智模型**: 读者以为模板是独立的东西 → 实际上模板就是属于数据源的特殊页面
- **首选教学类比**: 「复印件的原稿」——每次新建页面时复印一份模板
- **首次引入**: Ch4

#### 24. Skill（技能 / 指令模式）
- **认知难度**: 3
- **使用频率**: 中
- **前置心智模型**: 读者以为 Skill = 插件 → 实际上 Skill 只是一种结构化的指令页面模式，定义了 Agent 的特定能力
- **首选教学类比**: 「培训手册中的某一章」——教员工（Agent）怎么做某一类工作
- **首次引入**: Ch7

#### 25. MCP（Model Context Protocol）
- **认知难度**: 4
- **使用频率**: 低
- **前置心智模型**: 读者以为 MCP = API 调用 → 实际上 MCP 是一种标准协议，让 Agent 能调用外部服务暴露的工具
- **首选教学类比**: 「USB 接口标准」——只要对方提供 USB 接口（MCP Server），你的电脑（Agent）就能直接用，不需要装专门驱动
- **首次引入**: Ch8

#### 26. MCP Tool（MCP 工具）
- **认知难度**: 3
- **使用频率**: 低
- **前置心智模型**: 读者以为 MCP Tool = 函数 → 基本正确，但需要理解 inputSchema、toolArguments 的 JSON 结构
- **首选教学类比**: 「USB 设备上的按钮」——每个 MCP Server 暴露若干工具（按钮），Agent 按一下就能执行操作
- **首次引入**: Ch8

#### 27. Autofill Agent（自动填充 Agent）
- **认知难度**: 3
- **使用频率**: 低
- **前置心智模型**: 读者以为 Autofill = 简单的自动补全 → 实际上是专门绑定某个数据库、批量填写属性的 Custom Agent
- **首选教学类比**: 「流水线工人」——专门负责给某个表格（数据库）的某些列（属性）批量填值
- **首次引入**: Ch7

#### 28. Sharing / Permission（共享 / 权限）
- **认知难度**: 2
- **使用频率**: 中
- **前置心智模型**: 读者以为只有公开/私密两种 → 实际上有 user/workspace/public 三层，每层有不同访问级别
- **首选教学类比**: 「门禁卡权限」——不同的卡（用户/工作区/公开）能开不同的门（读/写/完全控制）
- **首次引入**: Ch3（基本概念），Ch6（Agent 权限）

---

## 依赖关系总表

```
Workspace
├── Page
│   ├── Block
│   │   └── Notion-flavored Markdown
│   ├── Property
│   │   └── Property Type
│   ├── Database
│   │   ├── Data Source
│   │   │   ├── Schema
│   │   │   ├── Template
│   │   │   └── SQL Query (querySql)
│   │   ├── View
│   │   │   ├── View Type
│   │   │   └── Filter / Sort
│   │   └── Autofill Agent → Custom Agent
│   └── Sharing / Permission
├── Agent (Personal)
│   ├── Conversation / Thread
│   │   └── Sub-thread
│   ├── Search
│   │   └── Connector
│   └── Custom Agent
│       ├── Instructions
│       ├── Integration
│       │   ├── Trigger
│       │   └── MCP
│       │       └── MCP Tool
│       └── Skill
└── Teamspace
```

## 认知难度分布

| 难度 | 概念 |
|------|------|
| 1 | Workspace, Page, Teamspace, Block, Conversation/Thread |
| 2 | Agent, Property, Search, Connector, View, Filter/Sort, Instructions, Template, Sharing, Conversation |
| 3 | Database, Notion-flavored Markdown, Custom Agent, Schema, Property Type, Integration, Trigger, Skill, Autofill Agent, MCP Tool |
| 4 | Data Source, Sub-thread, SQL Query, MCP |

## 章节引入映射

| 章节 | 引入的概念（首次详细讲解） |
|------|---------------------------|
| Ch1 | Workspace, Page（概念）, Agent（概念）, Database（概念）, Teamspace |
| Ch2 | Conversation/Thread, Search（初步） |
| Ch3 | Page（详细）, Block, Notion-flavored Markdown, Property（基本）, Sharing |
| Ch4 | Database（详细）, Data Source, Schema, Property Type, View, Filter/Sort, Template, SQL Query |
| Ch5 | Search（详细）, Connector |
| Ch6 | Custom Agent, Instructions, Integration |
| Ch7 | Trigger, Skill, Autofill Agent |
| Ch8 | MCP, MCP Tool |
| Ch9 | Sub-thread |
| Ch10 | （无新概念，综合应用） |
