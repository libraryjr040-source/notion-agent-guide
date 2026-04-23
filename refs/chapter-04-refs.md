# Chapter 4: 数据库操作 — Research Refs

## 核心技术点

### 1. 数据库结构
- Database = name + parent + dataSources + views
- DataSource = schema（属性定义）+ 模板
- View = 数据的展示方式（table/board/calendar/list/gallery/timeline/chart/map/form/dashboard）
- 一个数据库可以有多个数据源和多个视图

### 2. 属性类型（dataSourceTypes.ts）
- title, text, url, email, phone_number
- number（支持货币/百分比/精度/进度条）
- date（支持提醒）
- select, multi_select
- status（分组：to_do / in_progress / complete）
- person（limit: 1 = 单人）
- relation（单向/双向）
- checkbox
- file
- formula（计算属性）
- rollup（汇总关联数据）
- created_time, last_edited_time, created_by, last_edited_by
- auto_increment_id
- place / location
- button, verification

### 3. 视图类型（viewTypes.ts）
- table: 表格视图
- board: 看板视图（需要 groupBy）
- calendar: 日历视图（需要 calendarBy 日期属性）
- list: 列表视图
- gallery: 画廊视图（支持封面）
- timeline: 时间线视图（需要 timelineBy 日期属性）
- chart: 图表视图（column/bar/line/donut/number）
- map: 地图视图（需要 place 属性）
- form_editor: 表单视图
- dashboard: 仪表盘（嵌套多个 widget 视图）

### 4. 查询
- querySql: SQL 查询，支持 JOIN、json_each 等
- queryView: 按视图查询（返回视图展示的数据）
- Checkbox 值: __YES__ / __NO__
- Multi-select/Person/Relation: JSON 数组
- Date: 展开为三列 date:<Name>:start / :end / :is_datetime

### 5. 关联与汇总
- 单向关联: relation 属性 + dataSourceUrl
- 双向关联: createTwoWayRelation（两边都创建属性）
- Rollup: 基于 relation 属性汇总目标属性

### 6. Linked Database
- dataSources: {} + views 引用外部 dataSourceUrl
- 用于在不同页面展示同一数据源的不同视图

### 7. Wiki Database
- isWiki: true, wikiPageUrl
- 创建页面必须用 { type: "page", url: wikiPageUrl }

## 确定性陷阱
1. 创建数据库时用 CREATE-* 作键名，不是属性名
2. Status 属性必须定义 groups（to_do/in_progress/complete）
3. 双向关联必须用 createTwoWayRelation，不能手动创建两个单向
4. SQL 中 Checkbox 比较用 "__YES__" 而非 true
5. 查询 Multi-select 需要 json_each
6. Wiki 数据库的页面 parent 不是 dataSource
