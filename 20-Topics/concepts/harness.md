---
title: Harness-运行时框架
tags: [概念, AI, Claude, 系统架构]
created: 2026-04-05
status: 草稿
---

# Harness-运行时框架

## 一句话定义

Claude Code 的运行时框架，负责加载、协调和管理所有组件（skills、plugins、memory 等），为 AI 助手提供工作环境的系统架构。

## 核心原理

- **组件生命周期管理** - 负责启动、运行和关闭各组件
- **依赖注入** - 自动处理组件间的依赖关系
- **事件系统** - 协调组件间的通信和事件传递
- **配置管理** - 统一管理所有配置和设置

## 与 AI 的关系

Harness 是 [[AI]] 应用的**基础设施层**，类似于：
- 传统应用的运行时环境（如 JVM、Node.js）
- 但专门为 [[llm]] 和 AI Agent 设计
- 让 AI 能够安全、高效地调用外部工具和资源

## 连接

- [[skills]] - Harness 加载和执行的功能模块
- [[plugins]] - Harness 集成的外部扩展
- [[memory]] - Harness 管理的持久化存储组件
- [[claude-code]] - Harness 是 Claude Code 的核心架构

## 类比理解

| 传统开发 | Claude Code 生态 |
|----------|------------------|
| 操作系统 | Harness |
| 应用程序 | Skills |
| 驱动程序 | Plugins |
| 文件系统 | Memory |

## 来源

- [[2026-04-05]] - 整理 Claude Code 生态概念
- [[claudian/插件与技能清单|插件与技能清单]]

## 待深化

- [ ] Harness 的具体技术实现细节
- [ ] 与其他 AI 框架（如 LangChain）的对比
