# 术语表（Glossary）

> 全书术语的权威定义。每个术语包含：定义、教学锚点、前置心智模型、首次出现章节。

---

## Workspace（工作区）
- **定义**: Notion 的顶层协作空间，包含页面、数据库、成员和权限设置
- **教学锚点**: Ch1 用「共享办公室」类比引入
- **首次出现**: Chapter 1

## Page（页面）
- **定义**: Notion 的基本内容单元，可以包含文本（Block）、子页面、数据库等。也可以是数据库中的一行
- **教学锚点**: Ch1「乐高底板」概念提及；Ch3 详细讲解创建/编辑/移动/属性
- **首次出现**: Chapter 1（概念），Chapter 3（详细操作）

## Block（块）
- **定义**: 页面内容的最小单元。每个段落、标题、图片、代码块、表格都是一个 Block
- **教学锚点**: Ch3 用「积木块」类比引入
- **首次出现**: Chapter 3

## Database（数据库）
- **定义**: 页面的结构化集合，包含 Data Source（定义属性）和 View（展示方式）
- **教学锚点**: Ch1「智能文件柜」概念提及；Ch4 详细讲解完整概念体系
- **首次出现**: Chapter 1（概念），Chapter 4（详细操作）

## Data Source（数据源）
- **定义**: Database 中拥有 Schema（属性定义）的实体。一个 Database 可以有多个 Data Source
- **教学锚点**: Ch4 用「文件柜里的分区」类比引入
- **首次出现**: Chapter 4

## Schema（模式）
- **定义**: Data Source 的属性定义集合，决定了数据库中每页（行）有哪些属性（列）
- **教学锚点**: Ch4 用「建筑蓝图」类比引入
- **首次出现**: Chapter 4

## Property（属性）
- **定义**: 页面的结构化数据字段。有 25+ 种类型（title, text, number, select, status, relation, formula 等）
- **教学锚点**: Ch3 基本属性概念；Ch4「插座类型」类比详细讲解
- **首次出现**: Chapter 3（基本），Chapter 4（全部类型）

## View（视图）
- **定义**: 数据库的展示方式。同一份数据可以有表格、看板、日历、时间线、图表、画廊、地图等多种视图
- **教学锚点**: Ch4「同一批照片的不同相册排列方式」类比引入
- **首次出现**: Chapter 4

## Agent（个人 Agent / Personal Agent）
- **定义**: Notion 内置的 AI 助理，能直接操作 Workspace 中的页面、数据库，并搜索信息
- **教学锚点**: Ch1「私人助理」类比引入；Ch2 实操对话
- **首次出现**: Chapter 1（概念），Chapter 2（实操）

## Custom Agent（自定义 Agent）
- **定义**: 用户创建的专职 AI Agent，有独立的指令、权限和触发器，默认无任何权限（最小权限原则）
- **教学锚点**: Ch6「专职员工」类比引入
- **首次出现**: Chapter 6

## Thread（对话线程）
- **定义**: 一次与 Agent 的对话会话，有上下文记忆
- **教学锚点**: Ch2「电话通话」类比引入
- **首次出现**: Chapter 2

## Search（搜索）
- **定义**: Agent 的信息检索能力，可跨 Notion、Slack、Google Drive、GitHub、Web 等多源搜索
- **教学锚点**: Ch2 初步使用；Ch5「万能搜索框」类比详细讲解
- **首次出现**: Chapter 2（初步），Chapter 5（详细）

## Connector（连接源）
- **定义**: Notion 预集成的外部数据源（Slack、Google Drive、GitHub、Jira 等）
- **教学锚点**: Ch5「翻译耳机」类比引入
- **首次出现**: Chapter 5

## Instructions（Agent 指令页）
- **定义**: Custom Agent 的行为说明，是一个 Notion 页面，用自然语言撰写
- **教学锚点**: Ch6「岗位说明书」类比引入
- **首次出现**: Chapter 6

## Integration（Agent 集成）
- **定义**: 给 Custom Agent 添加的能力模块（Notion、Slack、GitHub、MCP Server 等）
- **教学锚点**: Ch6「工具箱里的工具」类比引入
- **首次出现**: Chapter 6

## Trigger（触发器）
- **定义**: 让 Custom Agent 自动执行的事件源：定时、页面创建/更新/删除、按钮按下、@ 提及等
- **教学锚点**: Ch7「闹钟 + 门铃 + 对讲机」类比引入
- **首次出现**: Chapter 7

## Skill（技能）
- **定义**: 一种结构化的指令模式，将复杂工作流编码为 Agent 可遵循的步骤化指南
- **教学锚点**: Ch7「培训手册中的某一章」类比引入
- **首次出现**: Chapter 7

## MCP（Model Context Protocol）
- **定义**: 一种开放标准协议，让 Agent 能调用任何符合该协议的外部服务暴露的工具
- **教学锚点**: Ch8「USB 接口标准」类比引入
- **首次出现**: Chapter 8

## Autofill Agent（自动填充 Agent）
- **定义**: 专门绑定某个数据库、批量填写属性的 Custom Agent
- **教学锚点**: Ch7「流水线工人」类比引入
- **首次出现**: Chapter 7

## Sub-thread（子线程）
- **定义**: 从主对话中派生的子任务线程，主线程最多可创建 50 个子线程
- **教学锚点**: Ch9「派出去跑腿的小弟」类比引入
- **首次出现**: Chapter 9

## Teamspace（团队空间）
- **定义**: Workspace 中的独立分区，有独立的权限和成员管理
- **教学锚点**: Ch1「办公室里的会议室」类比引入
- **首次出现**: Chapter 1

## Template（页面模板）
- **定义**: 属于 Data Source 的特殊页面，创建新页面时可复制模板的内容和属性
- **教学锚点**: Ch4「复印件的原稿」类比引入
- **首次出现**: Chapter 4

## Notion-flavored Markdown
- **定义**: Notion 内部的内容表示格式，基于标准 Markdown 但有大量扩展
- **教学锚点**: Ch3「方言」类比引入；附录 A 完整速查
- **首次出现**: Chapter 3（核心），Appendix A（速查）
