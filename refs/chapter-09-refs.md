# Chapter 9: 常见问题与排障 — Research Refs

## 核心问题来源

### 1. 权限相关
- 自定义 Agent 默认无权限
- 页面锁定/删除后不可编辑
- 连接状态: ready / needs_connection / needs_permissions
- wiki 数据库页面必须用 wikiPageUrl 作为 parent

### 2. 属性格式相关
- 属性名大小写敏感
- 日期属性需用 date:<Name>:start/end/is_datetime 格式
- 地点属性需用 place:<Name>:address 等展开格式
- 系统列名冲突需加 userDefined: 前缀
- checkbox 在 SQL 中是 __YES__ / __NO__
- multi-select/relation/person 在 SQL 中是 JSON 数组

### 3. 内容编辑相关
- oldStr 必须唯一（除非 replaceAllMatches: true）
- 不能在 oldStr/newStr 中包含 <content> 标签
- 不能编辑已删除或锁定的页面
- <database> 块必须保持原样，不能通过页面编辑创建
- <page> 标签代表子页面，移除会删除子页面

### 4. 数据库操作相关
- CREATE-* 标识符只用于创建时的占位
- 显示名称不能作为键
- 表名和列名必须双引号包裹
- Autofill 超过 20 行必须用 autofill agent

### 5. 搜索相关
- lookback 不接受自然语言，必须用具体值
- 重复相同查询返回相同结果
- includeWebResults 默认 true

### 6. Agent 相关
- 配置变更后必须测试
- 指令不应包含技术实现细节
- 子线程每个父线程最多 50 次
- Autofill agent 必须保留 button.pressed 触发器
