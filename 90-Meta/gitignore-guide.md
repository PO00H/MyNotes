---
title: Gitignore-忽略文件指南
created: 2026-04-05
tags: [Git, 工具, 配置]
---

# Gitignore-忽略文件指南

## 一句话定义

`.gitignore` 是 Git 的配置文件，告诉 Git **哪些文件不需要版本控制**（不追踪、不提交）。

---

## 核心作用

| 作用 | 说明 | 例子 |
|------|------|------|
| **避免提交临时文件** | 编辑器自动生成的缓存 | `.obsidian/workspace.json` |
| **保护隐私** | 个人配置、密钥 | `.env`, `config.json` |
| **减少仓库体积** | 大文件、生成的文件 | `node_modules/`, `*.pdf` |
| **避免冲突** | 每个人的环境不同 | macOS `.DS_Store`, Windows `Thumbs.db` |

---

## 怎么创建

### 方法 1：命令行

```bash
# 进入项目文件夹
cd MyNotes

# 创建 .gitignore 文件
touch .gitignore

# 或者直接用编辑器创建
# Windows: 记事本保存为 .gitignore（注意前面有个点）
# macOS/Linux: 直接在编辑器中创建
```

### 方法 2：Obsidian 中创建

1. 在根目录创建新文件
2. 文件名输入 `.gitignore`（前面有个点）
3. Obsidian 会提示"隐藏文件"，确认即可

---

## 语法规则

```gitignore
# 1. 井号开头是注释

# 2. 忽略特定文件
filename.md
config.json

# 3. 忽略特定文件夹（斜杠结尾表示文件夹）
.obsidian/
node_modules/

# 4. 通配符 * 匹配任意字符
*.tmp          # 忽略所有 .tmp 文件
*.log          # 忽略所有日志文件

# 5. 通配符 ** 匹配任意层级目录
**/.DS_Store    # 忽略所有子目录中的 .DS_Store

# 6. 感叹号 ! 表示不忽略（例外规则）
*.md           # 忽略所有 md 文件
!important.md  # 但 important.md 不忽略

# 7. 斜杠 / 开头表示从根目录开始
/temp.md       # 只忽略根目录的 temp.md
# 不忽略 subfolder/temp.md
```

---

## Obsidian 知识库推荐配置

### 基础版（必加）

```gitignore
# ============================================
# Obsidian Gitignore - 基础版
# ============================================

# Obsidian 工作区配置（每个人不同）
.obsidian/workspace.json
.obsidian/workspaces.json

# 缓存文件
.obsidian/cache/

# 插件数据（可选，如果想同步插件配置则注释掉）
# .obsidian/plugins/

# 主题缓存
.obsidian/themes/*/main.js
.obsidian/themes/*/manifest.json

# 其他 Obsidian 临时文件
.trash/

# 系统文件
.DS_Store          # macOS
Thumbs.db          # Windows
*.tmp
*.temp
~$*                # Office 临时文件
```

### 完整版（推荐）

```gitignore
# ============================================
# Obsidian Gitignore - 完整版
# ============================================

# --------------------------------------------
# Obsidian 配置（部分个人化，部分共享）
# --------------------------------------------

# 工作区状态（完全个人化，必须忽略）
.obsidian/workspace.json
.obsidian/workspaces.json
.obsidian/graph.json

# 缓存
.obsidian/cache/

# 插件（可选）
# 如果想同步插件配置，注释掉下面这行
# .obsidian/plugins/

# 但某些插件的临时数据要忽略
.obsidian/plugins/*/.hotreload
.obsidian/plugins/*/data.json

# 主题（可选）
# 如果只想用官方主题，忽略自定义主题
# .obsidian/themes/

# --------------------------------------------
# 笔记相关
# --------------------------------------------

# 回收站
.trash/

# 大的附件（可选）
# attachments/*.pdf
# attachments/*.zip
# attachments/*.mp4

# --------------------------------------------
# 系统和编辑器
# --------------------------------------------

# macOS
.DS_Store
.AppleDouble
.LSOverride

# Windows
Thumbs.db
ehthumbs.db
Desktop.ini

# 编辑器
.vscode/
.idea/
*.swp
*.swo
*~

# 临时文件
*.tmp
*.temp
*.bak
*.old

# Office
~$*
```

---

## 常见场景

### 场景 1：忘记创建 .gitignore，已经提交了不该提交的文件

```bash
# 1. 停止追踪（但不删除文件）
git rm --cached .obsidian/workspace.json

# 2. 添加到 .gitignore
echo ".obsidian/workspace.json" >> .gitignore

# 3. 提交更改
git add .gitignore
git commit -m "chore: remove personal config from tracking"
```

### 场景 2：检查哪些文件会被忽略

```bash
git check-ignore -v filename.md
```

### 场景 3：强制添加被忽略的文件（不推荐）

```bash
git add -f filename.md
```

---

## Obsidian 知识库特别注意事项

### 哪些文件**应该**同步？

| 文件/文件夹 | 说明 | 是否同步 |
|-------------|------|----------|
| `.obsidian/app.json` | 应用设置（主题、字体等） | ✅ 建议同步 |
| `.obsidian/appearance.json` | 外观配置 | ✅ 建议同步 |
| `.obsidian/core-plugins.json` | 核心插件开关 | ✅ 建议同步 |
| `.obsidian/plugins/` | 社区插件 | ⚠️ 可选 |
| `.obsidian/snippets/` | CSS 片段 | ✅ 建议同步 |
| `.obsidian/hotkeys.json` | 快捷键配置 | ✅ 建议同步 |

### 哪些文件**不应该**同步？

| 文件/文件夹 | 说明 | 是否同步 |
|-------------|------|----------|
| `.obsidian/workspace.json` | 当前工作区状态 | ❌ 不同步 |
| `.obsidian/graph.json` | 图谱视图状态 | ❌ 不同步 |
| `.obsidian/cache/` | 缓存 | ❌ 不同步 |
| `.trash/` | 回收站 | ❌ 不同步 |

---

## 快速参考卡片

```bash
# 创建 .gitignore
touch .gitignore

# 编辑 .gitignore
# 用 Obsidian 直接打开编辑即可

# 检查哪些文件被忽略
git check-ignore -v filename

# 查看所有被忽略的文件
git status --ignored

# 重新添加被错误忽略的文件
git add -f filename
```

---

## 推荐配置（复制即用）

```gitignore
# Obsidian
.obsidian/workspace.json
.obsidian/workspaces.json
.obsidian/graph.json
.obsidian/cache/
.trash/

# System
.DS_Store
Thumbs.db
*.tmp
```

---

## 更新记录

- 2026-04-05: 创建 Gitignore 指南
