---
title: MCP-Model Context Protocol
tags: [概念, AI, 协议, 基础设施, 标准]
created: 2026-04-06
status: 草稿
---

# MCP-Model Context Protocol

## 一句话定义

Model Context Protocol（模型上下文协议），由 Anthropic 推出的开放标准协议，用于统一 AI 模型与外部工具、数据源之间的通信接口。

## 核心原理

- **标准化接口** - 定义统一的工具调用格式（类似 USB 接口标准）
- **上下文传递** - 规范模型与工具间的上下文交换机制
- **安全沙箱** - 工具运行在隔离环境中，防止恶意操作
- **声明式配置** - 通过 JSON/YAML 描述工具能力

## 与 AI 的关系

MCP 是 AI 生态的**基础设施层**：

- 类似 HTTP 之于互联网、USB 之于硬件
- 让 **LLM** 能够**标准化地**连接外部世界
- 解决碎片化问题：每个工具不需要单独适配每个模型

## 连接

- [[../../concepts/harness|Harness]] - Claude Code 的 Harness 支持 MCP
- [[../../concepts/plugins|Plugins]] - MCP 是插件系统的底层协议
- [[../03-agents/manus|Manus]] - Agent 通过 MCP 调用工具
- [[../../concepts/skills|Skills]] - Skills 可以通过 MCP 扩展能力

## 应用场景

| 场景 | MCP 作用 |
|------|----------|
| 文件操作 | 统一读写文件的接口 |
| API 调用 | 标准化调用 GitHub/Notion 等服务 |
| 数据库查询 | 安全的 SQL 执行接口 |
| 浏览器控制 | 自动化网页操作 |

## 技术对比

| 协议/标准 | 层级 | 说明 |
|-----------|------|------|
| **MCP** | 应用层 | AI 专用工具调用协议 |
| **Function Calling** | 模型层 | LLM 原生函数调用能力 |
| **API** | 传输层 | 具体服务的接口 |

## 来源

- [[../../../10-Journal/2026/04-April/2026-04-06|2026-04-06]] - 整理 AI 新概念
- Anthropic 官方文档

## 待深化

- [ ] MCP 与 Function Calling 的技术细节对比
- [ ] 如何开发 MCP 服务端
- [ ] MCP 与 LangChain Tool 的异同
