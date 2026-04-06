---
title: AI-MOC-AI领域索引
---

# AI-MOC-AI领域索引

AI 技术与产品分层索引。

---

## 01-Protocols 协议/基础设施

AI 底层协议与标准。

- [[01-protocols/mcp|MCP]] - Model Context Protocol，AI 工具接口标准

---

## 02-Products 产品/平台

AI 应用开发平台与产品。

- [[02-products/lovable|Lovable]] - AI 应用开发平台

---

## 03-Agents 智能代理

AI Agent 产品与系统。

- [[03-agents/manus|Manus]] - 通用 AI Agent
- [[03-agents/base44|Base44]] - AI Agent 平台

---

## 04-Concepts 基础概念

AI 基础理论与概念。

- [[04-concepts/llm|LLM]] - 大语言模型
- [[04-concepts/rag|RAG]] - 检索增强生成，结合外部知识库的 LLM 增强技术

---

## 跨层连接

```
Concepts (LLM) → Protocols (MCP) → Products/Agents
     ↑                                    ↓
     └────── 共同构成 AI 生态 ────────────┘
```

- **LLM** 提供基础能力
- **MCP** 提供连接标准
- **Products** 封装特定场景
- **Agents** 实现自主行动

---

## 维护记录

- 2026-04-05: 创建，添加 [[04-concepts/llm|LLM]]
- 2026-04-06: 重构分层结构，添加 Protocols/Products/Agents/Concepts 四层分类
