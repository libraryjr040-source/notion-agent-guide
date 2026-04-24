# 附录 A：Notion Markdown 速查表

本附录汇总 Notion Agent 在创建和编辑页面时使用的 Notion 风格 Markdown 语法。当你想精确控制页面格式时，可以参考这个速查表。

> 💡 **提示**：大多数情况下你不需要写 Markdown——直接用自然语言告诉 Agent 想要什么格式就行。这个速查表是为需要精确控制的高级用户准备的。

## 基础格式

| 语法 | 效果 |
|------|------|
| `**文字**` | **粗体** |
| `*文字*` | *斜体* |
| `~~文字~~` | ~~删除线~~ |
| `` `代码` `` | `行内代码` |
| `[链接文字](URL)` | 超链接 |

## 标题

| 语法 | 说明 |
|------|------|
| `# 标题` | 一级标题 |
| `## 标题` | 二级标题 |
| `### 标题` | 三级标题 |

> 注意：Notion 最多支持三级标题（H1-H3）。H4 会被转为 H3，H5/H6 会被转为 H4。

## 列表

| 语法 | 说明 |
|------|------|
| `- 项目` | 无序列表 |
| `1. 项目` | 有序列表 |
| `- [ ] 项目` | 待办（未完成） |
| `- [x] 项目` | 待办（已完成） |

用 Tab 缩进可以创建嵌套列表。

## 引用

```
> 这是一段引用
```

多行引用使用 `<br>` 换行，不要用普通换行符（会变成多个独立引用块）：

```
> 第一行<br>第二行<br>第三行
```

## 分割线

```
---
```

## 代码块

````
```语言
代码内容
```
````

代码块内不需要转义特殊字符。

## 数学公式

行内公式：`$E = mc^2$`

块级公式：
```
$$
E = mc^2
$$
```

## 颜色

### 文字颜色

可用颜色：gray, brown, orange, yellow, green, blue, purple, pink, red

```
<span color="blue">蓝色文字</span>
```

### 背景颜色

可用颜色：gray_bg, brown_bg, orange_bg, yellow_bg, green_bg, blue_bg, purple_bg, pink_bg, red_bg

```
<span color="yellow_bg">黄色高亮</span>
```

### 块级颜色

```
这段文字是红色的 {color="red"}
```

## 高级块

以下块类型仅在页面内容中可用（不能在聊天中使用）：

### 折叠块（Toggle）

```
<details>
<summary>点击展开</summary>
	内容在这里
</details>
```

### 标注（Callout）

```
<callout icon="💡">
	标注内容
</callout>
```

### 多列布局

```
<columns>
	<column>
		左列内容
	</column>
	<column>
		右列内容
	</column>
</columns>
```

### 表格

```
<table header-row="true">
	<tr>
		<td>表头 1</td>
		<td>表头 2</td>
	</tr>
	<tr>
		<td>数据 1</td>
		<td>数据 2</td>
	</tr>
</table>
```

### 折叠标题

```
## 点击展开 {toggle="true"}
	折叠的内容
```

### 同步块

```
<synced_block>
	同步的内容
</synced_block>
```

## 提及（Mentions）

| 语法 | 说明 |
|------|------|
| `<mention-user url="...">名字</mention-user>` | 提及用户 |
| `<mention-page url="...">标题</mention-page>` | 提及页面 |
| `<mention-database url="...">名称</mention-database>` | 提及数据库 |
| `<mention-date start="2025-01-15"/>` | 提及日期 |

## 媒体

| 语法 | 说明 |
|------|------|
| `![说明](URL)` | 图片 |
| `<video src="URL">说明</video>` | 视频 |
| `<audio src="URL">说明</audio>` | 音频 |
| `<file src="URL">说明</file>` | 文件 |
| `<pdf src="URL">说明</pdf>` | PDF |

## 幻灯片模式

用分割线 `---` 分隔每张幻灯片：

```
第一张幻灯片的内容

---

第二张幻灯片的内容

---

第三张幻灯片的内容
```

页面标题自动成为第一张幻灯片。

## 转义字符

在 Markdown 格式区域（代码块外），以下字符需要用反斜杠转义：

`\ * ~ \` $ [ ] < > { } | ^`

代码块内不需要转义。
