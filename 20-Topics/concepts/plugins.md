---
title: Plugins-插件系统
tags: [概念, AI, Claude, 扩展机制]
created: 2026-04-05
status: 草稿
---

# Plugins-插件系统

## 一句话定义

Claude Code 的扩展机制，通过标准化的接口让外部服务和工具能够被 AI 调用，扩展 AI 的能力边界。

## 核心原理

- **MCP 协议** - Model Context Protocol，标准化的 AI 工具接口
- **声明式配置** - 通过 JSON/YAML 描述插件能力
- **沙箱执行** - 安全隔离的插件运行环境
- **动态加载** - 运行时添加/移除插件

## 与 AI 的关系

Plugins 是 AI 的**能力扩展器**：

- 原生 LLM 只能处理文本
- Plugins 让 AI 能够：
  - 访问文件系统（读代码、写文件）
  - 调用 API（GitHub、Notion、浏览器）
  - 执行代码（运行测试、构建项目）
  - 操作外部工具（数据库、云服务）

这实现了从 [[llm]] 到 **AI Agent** 的跃迁。

## 插件类型

| 类型 | 示例 | 作用 |
|------|------|------|
| **Local MCP** | notion, github | 本地运行的 MCP 服务 |
| **User 插件** | claude-hud | 用户安装的增强插件 |
| **Built-in** | everything-claude-code | 内置功能扩展 |

## 连接

- [[harness]] - Plugins 由 Harness 加载和管理
- [[skills]] - Plugins 可以提供 Skills 的实现
- [[mcp]] - 插件基于 MCP 协议通信
- **ai-agent** - 插件让 LLM 成为真正的 Agent

## 来源

- [[2026-04-05]] - 整理 Claude Code 生态概念
- [[claudian/插件与技能清单|插件与技能清单]]
- [[claudian/plugins/everything-claude-code|everything-claude-code]]

## 待深化

- [ ] MCP 协议的技术细节
- [ ] 如何开发自定义插件
