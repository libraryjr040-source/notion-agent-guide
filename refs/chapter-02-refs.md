# Chapter 2: 你的第一次对话 — Research Refs

## 1. 自测结果（createAndRunThread 六问）

- Thread 创建时机：不确定是点击"新对话"时还是发送消息时
- 同 Thread 内全部可见，有 token 上限，跨 Thread 无记忆
- URL 传递：工具返回的压缩 URL 留在上下文中，后续操作直接引用
- 预加载：模块文档 + 用户指令 + 用户信息 + workspace + 连接 + System Memories
- @ 提及：转为 mention 标签含 URL，不自动加载内容
- 长度限制：有上限，工具调用消耗更快，开新 Thread 是解决方案

## 2. 确定性陷阱

1. 对话过长 Agent 会失忆
2. @ 提及 ≠ 加载内容
3. 工具调用比纯聊天更快消耗上下文
4. 跨 Thread 记忆靠 System Memories——不精确、不可控、不可见
5. 搜索默认包含互联网结果
