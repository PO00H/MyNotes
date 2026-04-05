---
title: Skills-技能系统
tags: [概念, AI, Claude, 功能模块]
created: 2026-04-05
status: 草稿
---

# Skills-技能系统

## 一句话定义

封装特定领域知识和工作流程的可复用模块，让 Claude Code 能够执行专业任务（如代码审查、测试驱动开发、项目规划等）。

## 核心原理

- **声明式定义** - 用 Markdown/YAML 描述 Skill 的触发条件和行为
- **上下文注入** - Skill 可以注入系统提示（system prompt）
- **工作流编排** - 定义多步骤任务的执行流程
- **组合复用** - Skills 可以相互调用和组合

## 与 AI 的关系

Skills 是 [[AI]] 的**专业能力包**：

- 基础 LLM 有通用能力，但缺乏专业深度
- Skills 给 AI 注入领域专业知识：
  - `tdd-guide` - 测试驱动开发专家
  - `security-reviewer` - 安全审计专家
  - `planner` - 项目规划专家
- 类似于给 AI "聘请"了各专业顾问

## Skill 类型

| 类型 | 说明 | 示例 |
|------|------|------|
| **Workflow** | 工作流定义 | `skill-organizer`, `tdd-workflow` |
| **Agent** | 子代理配置 | `planner`, `code-reviewer` |
| **Knowledge** | 领域知识库 | `golang-patterns`, `frontend-patterns` |
| **Command** | 斜杠命令 | `/plan`, `/tdd`, `/code-review` |

## 连接

- [[harness]] - Skills 由 Harness 加载和执行
- [[plugins]] - Plugins 可以提供新的 Skills
- [[prompt-engineering]] - Skills 本质是高级提示工程
- [[ai-agent]] - Skills 让 AI 具备专业能力

## 来源

- [[2026-04-05]] - 整理 Claude Code 生态概念
- [[claudian/skills/skill-organizer|skill-organizer]]
- [[claudian/插件与技能清单|插件与技能清单]]

## 待深化

- [ ] 如何编写自定义 Skill
- [ ] Skill 与 Function Calling 的关系
