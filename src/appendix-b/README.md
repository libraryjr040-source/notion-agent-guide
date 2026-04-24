# 附录 B：属性类型速查表

本附录汇总 Notion 数据库中所有可查询和可设置的属性类型，以及它们在 SQL 查询和页面更新中的格式。

## 属性类型一览

| 属性类型 | SQL 列类型 | 可设置 | 说明 |
|---------|-----------|--------|------|
| Title | TEXT | ✅ | 页面标题，每个数据源必有 |
| Text | TEXT | ✅ | 富文本 |
| Number | FLOAT | ✅ | 数字 |
| Checkbox | TEXT | ✅ | 复选框 |
| Select | TEXT | ✅ | 单选 |
| Multi-select | TEXT (JSON) | ✅ | 多选 |
| Status | TEXT | ✅ | 状态 |
| Date | TEXT ×3 | ✅ | 日期（展开为三列） |
| Person | TEXT (JSON) | ✅ | 用户 |
| Relation | TEXT (JSON) | ✅ | 关联 |
| URL | TEXT | ✅ | 网址 |
| Email | TEXT | ✅ | 邮箱 |
| Phone | TEXT | ✅ | 电话 |
| Files | TEXT (JSON) | ✅ | 文件 |
| Place/Location | TEXT ×5 | ✅ | 地点（展开为五列） |
| Auto-increment ID | INTEGER | ❌ | 自增 ID |
| Created time | TEXT | ❌ | 创建时间 |
| Last edited time | TEXT | ❌ | 最后编辑时间 |
| Created by | TEXT | ❌ | 创建者 |
| Last edited by | TEXT | ❌ | 最后编辑者 |

## SQL 查询中的特殊值

### Checkbox

| SQL 值 | 含义 |
|--------|------|
| `"__YES__"` | ✅ 已勾选 |
| `"__NO__"` | ❌ 未勾选 |
| `NULL` | 未勾选（默认） |

### Multi-select

SQL 中存储为 JSON 数组字符串。筛选示例：

```sql
WHERE EXISTS (
  SELECT 1 FROM json_each(t."Tags")
  WHERE value = 'Important'
)
```

### Person

存储为用户 URL 的 JSON 数组。

### Relation

存储为页面 URL 的 JSON 数组。JOIN 示例：

```sql
SELECT o.url, o."名称"
FROM "数据源A" o
JOIN "数据源B" t
  ON t.url IN (SELECT value FROM json_each(o."关联属性"))
```

## 日期属性的展开格式

日期属性展开为三个列/键：

| 键 | 类型 | 说明 |
|----|------|------|
| `date:<属性名>:start` | TEXT | 开始日期/时间（ISO-8601） |
| `date:<属性名>:end` | TEXT | 结束日期/时间（单日期设为 null） |
| `date:<属性名>:is_datetime` | INTEGER | 1 = 包含时间，0 = 仅日期 |

### 设置示例

**单个日期：**
```
"date:截止日期:start": "2025-01-15"
"date:截止日期:end": null
"date:截止日期:is_datetime": 0
```

**日期范围：**
```
"date:活动日期:start": "2025-01-15"
"date:活动日期:end": "2025-01-20"
"date:活动日期:is_datetime": 0
```

**包含时间：**
```
"date:会议时间:start": "2025-01-15T10:30:00Z"
"date:会议时间:end": null
"date:会议时间:is_datetime": 1
```

## 地点属性的展开格式

地点属性展开为五个键：

| 键 | 类型 | 说明 |
|----|------|------|
| `place:<属性名>:address` | TEXT | 地址 |
| `place:<属性名>:name` | TEXT | 地点名称（可选） |
| `place:<属性名>:latitude` | FLOAT | 纬度 |
| `place:<属性名>:longitude` | FLOAT | 经度 |
| `place:<属性名>:google_place_id` | TEXT | Google Place ID（可选） |

最简设置（仅地址）：
```
"place:地点:address": "北京市朝阳区建国门外大街1号"
```

## 设置属性时的值格式

| 属性类型 | 设置格式 | 示例 |
|---------|---------|------|
| Title / Text | 字符串 | `"新标题"` |
| Number | 数字 | `42` |
| Checkbox | 布尔值 | `true` / `false` |
| Select | 选项名字符串 | `"进行中"` |
| Multi-select | 字符串数组 | `["重要", "紧急"]` |
| Status | 状态名字符串 | `"已完成"` |
| Person (限1) | 用户 URL | `"dataSourceUrl"` |
| Person (多个) | URL 数组 | `["dataSourceUrl", "okrs"]` |
| Relation (限1) | 页面 URL | `"dataSourceUrl"` |
| Relation (多个) | URL 数组 | `["dataSourceUrl", "okrs"]` |
| URL / Email / Phone | 字符串 | `"https://example.com"` |
| 清除任何值 | null | `null` |

## 系统列名冲突

当属性名与系统列名（`id`、`url`、`createdTime`）冲突时，需要加 `userDefined:` 前缀：

```
属性名 "url" → 列名/键名 "userDefined:url"
```

## 属性名注意事项

- **大小写敏感**：`Status` ≠ `status`
- **空格和特殊字符**：SQL 中用双引号包裹，如 `"Task Name"`
- **始终以数据源 schema 为准**：先查看数据库结构再操作
