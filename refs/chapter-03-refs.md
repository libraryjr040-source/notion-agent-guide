# Chapter 3: 页面操作 — Research Refs

## 核心技术点（来自 pages/AGENTS.md + index.ts + page-content-spec.md + notion-markdown.md）

### 1. 页面的五种 Parent 类型
- user（顶层私人页面）
- page（子页面）
- dataSource（数据库条目）
- teamspace（团队空间顶层）
- agent（Agent 指令页，只读，不可创建/移动到此）

### 2. 创建页面
- 必须指定 parent
- 可选：icon（emoji / URL / Notion Icon）、properties、content
- 数据源页面可用 pageTemplate 复制模板
- asTemplate: true 创建模板页
- Wiki 数据库必须用 { type: "page", url: wikiPageUrl } 作 parent

### 3. 编辑页面（updatePage）
- propertyUpdates：更新属性（注意：创建用 properties，更新用 propertyUpdates）
- contentUpdates：用 oldStr/newStr 局部替换（推荐），或省略 oldStr 全量替换（最后手段）
- oldStr 必须唯一，除非 replaceAllMatches: true
- 不能对 deleted 或 locked 页面调用
- 同一页面不要并行调用 updatePage

### 4. 移动页面
- updatePage 传 parent 参数即可移动
- 不能移到 agent 下

### 5. 删除 vs 归档
- deletePages：移到回收站（可恢复）
- archivePages：归档，隐藏但留在工作区
- unarchivePages：取消归档

### 6. 属性格式
- Title/Text → string
- Number → number
- Checkbox → boolean
- Select/Status → string（选项名）
- Multi-select → string[]
- Person → userUrl string / string[]
- Relation → pageUrl string / string[]
- Date → 展开为三个键 date:<Name>:start / :end / :is_datetime
- Place → 展开为五个键 place:<Name>:address / :name / :latitude / :longitude / :google_place_id
- 属性名区分大小写！

### 7. 内容格式（Notion-flavored Markdown）
- 标准 MD 基本可用（标题、列表、粗斜体、代码块、链接、表格）
- 特有：callout、toggle、columns、synced_block、mention-*、color 属性
- 表格只能含富文本，不能嵌套块
- <page> 标签 = 子页面引用（移除会删页面！）
- <mention-page> = 行内引用（安全）
- 代码块内不转义

### 8. 分享与权限（sharing.ts）
- loadPermissions / updatePermission
- 三种目标：user / workspace / public
- 六级权限：full_access > can_edit > can_edit_content > can_comment > can_view > no_access
- public = Share to web

### 9. Verification
- 内置页面属性，所有页面可用
- verified / none

### 10. Presentation Mode
- 用 --- 分隔幻灯片
- Plus 计划及以上

## 确定性陷阱
1. properties vs propertyUpdates 混用 → 出错
2. 属性名大小写不匹配 → 静默失败
3. <page> 标签误删 → 子页面被移除
4. 对 locked/deleted 页面调用 updatePage → 报错
5. oldStr 不唯一 → 报错（除非 replaceAllMatches）
6. Date/Place 属性必须用展开键名
