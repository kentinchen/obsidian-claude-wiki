---
title: "AI开发范式---OpenSpec 新手入门教程"
source: "https://zhuanlan.zhihu.com/p/1980408655154257981"
author:
  - "[[老顾聊技术随便聊聊，说点有价值的]]"
published:
created: 2026-04-16
description: "目录什么是OpenSpec？为什么需要OpenSpec？准备工作快速开始核心概念完整工作流程实际示例支持的AI工具常用命令团队采用指南常见问题什么是OpenSpec？ OpenSpec 是一个为AI编码助手设计的规范驱动开发工具，它通过…"
tags:
  - "clippings"
---
## 目录

1. 什么是OpenSpec？
2. 为什么需要OpenSpec？
3. 准备工作
4. 快速开始
5. 核心概念
6. 完整工作流程
7. 实际示例
8. 支持的AI工具
9. 常用命令
10. 团队采用指南
11. 常见问题

## 什么是OpenSpec？

**OpenSpec** 是一个为AI编码助手设计的 [规范驱动开发](https://zhida.zhihu.com/search?content_id=267268780&content_type=Article&match_order=1&q=%E8%A7%84%E8%8C%83%E9%A9%B1%E5%8A%A8%E5%BC%80%E5%8F%91&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3NzY1MjI4NjEsInEiOiLop4TojIPpqbHliqjlvIDlj5EiLCJ6aGlkYV9zb3VyY2UiOiJlbnRpdHkiLCJjb250ZW50X2lkIjoyNjcyNjg3ODAsImNvbnRlbnRfdHlwZSI6IkFydGljbGUiLCJtYXRjaF9vcmRlciI6MSwiemRfdG9rZW4iOm51bGx9.rzV5pBjGpQQaDa8Ph1KUmYJpjH-BQdvaocNTfjkILMY&zhida_source=entity) 工具，它通过轻量级的工作流程，确保人类开发者和AI助手在编写任何代码之前就能对需求达成明确共识。

### 核心特点

- 🚀 **轻量级** ：无需API密钥，最小化设置
- 🔄 **现有项目优先** ：特别适合修改现有功能 (1→n)
- 📋 **变更跟踪** ：提案、任务和规范差异的完整生命周期管理
- 🤖 **AI工具集成** ：支持多种主流AI编码助手

## 为什么需要OpenSpec？

### 传统AI编码助手的问题

当您使用AI编码助手时，是否遇到过以下情况：

- ❌ AI根据模糊提示生成不符合需求的代码
- ❌ 遗漏重要功能要求
- ❌ 添加了不必要的功能
- ❌ 代码行为不可预测

### OpenSpec的解决方案

OpenSpec通过 **规范驱动开发** 解决这些问题：

✅ **明确共识** ：在编码前确定所有要求  
✅ **结构化变更** ：所有相关文档集中管理  
✅ **可审查输出** ：AI根据明确规范生成代码  
✅ **版本控制** ：完整追踪所有变更历史

## 准备工作

### 系统要求

- **[Node.js](https://zhida.zhihu.com/search?content_id=267268780&content_type=Article&match_order=1&q=Node.js&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3NzY1MjI4NjEsInEiOiJOb2RlLmpzIiwiemhpZGFfc291cmNlIjoiZW50aXR5IiwiY29udGVudF9pZCI6MjY3MjY4NzgwLCJjb250ZW50X3R5cGUiOiJBcnRpY2xlIiwibWF0Y2hfb3JkZXIiOjEsInpkX3Rva2VuIjpudWxsfQ.VZoEpBxWEyqBeoXgizBU8hB5bTMtKQp9oBbUpWQo9FI&zhida_source=entity)** >= 20.19.0
- 支持的AI编码助手（见支持的AI工具）

### 检查Node.js版本

```
node --version
```

如果版本不符合要求，请访问 Node.js官网 更新。

## 快速开始

### 第一步：安装OpenSpec CLI

```
npm install -g @fission-ai/openspec@latest
```

### 验证安装

```
openspec --version
```

### 第二步：在项目中初始化OpenSpec

```
cd your-project-directory
openspec init
```

初始化过程会：

1. 询问您使用的AI工具（ [Claude Code](https://zhida.zhihu.com/search?content_id=267268780&content_type=Article&match_order=1&q=Claude+Code&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3NzY1MjI4NjEsInEiOiJDbGF1ZGUgQ29kZSIsInpoaWRhX3NvdXJjZSI6ImVudGl0eSIsImNvbnRlbnRfaWQiOjI2NzI2ODc4MCwiY29udGVudF90eXBlIjoiQXJ0aWNsZSIsIm1hdGNoX29yZGVyIjoxLCJ6ZF90b2tlbiI6bnVsbH0.JW-bfv_Dhe1VkKev4ecpekYUpPk9t-W2rj9Yf5OyCVA&zhida_source=entity) 、 [Cursor](https://zhida.zhihu.com/search?content_id=267268780&content_type=Article&match_order=1&q=Cursor&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3NzY1MjI4NjEsInEiOiJDdXJzb3IiLCJ6aGlkYV9zb3VyY2UiOiJlbnRpdHkiLCJjb250ZW50X2lkIjoyNjcyNjg3ODAsImNvbnRlbnRfdHlwZSI6IkFydGljbGUiLCJtYXRjaF9vcmRlciI6MSwiemRfdG9rZW4iOm51bGx9.rccD0NGvA7YScYzgppQynqheazqLUVpiL9rTm-905GE&zhida_source=entity) 等）
2. 自动配置相应的斜杠命令
3. 创建 `openspec/` 目录结构
4. 生成 `AGENTS.md` 文件

### 第三步：验证设置

```
openspec list
```

如果您的AI助手没有立即显示新的斜杠命令，请重启它。

## 核心概念

### 1\. 双文件夹模型

OpenSpec使用两个主要目录：

```
openspec/
├── specs/          # 当前真理源规范
│   └── auth/
│       └── spec.md
├── changes/        # 变更提案
│   └── feature-name/
│       ├── proposal.md
│       ├── tasks.md
│       └── specs/
└── project.md      # 项目级别约定
```

### 2\. 规范格式

规范使用Markdown格式，包含：

```
# Auth Specification
## Purpose
Authentication and session management.
## Requirements
### Requirement: User Authentication
The system SHALL issue a JWT on successful login.
#### Scenario: Valid credentials
- WHEN a user submits valid credentials
- THEN a JWT is returned
```

### 3\. 变更差异

变更通过"差异"格式显示：

```
# Delta for Auth
## ADDED Requirements
### Requirement: Two-Factor Authentication
The system MUST require a second factor during login.
#### Scenario: OTP required
- WHEN a user submits valid credentials
- THEN an OTP challenge is required
```

## 完整工作流程

OpenSpec遵循四步工作流程：

### 1️⃣ 起草变更提案

```
# 使用AI助手或直接创建
/openspec:proposal Add profile search filters
```

AI会自动创建：

- `openspec/changes/feature-name/proposal.md` - 变更说明
- `openspec/changes/feature-name/tasks.md` - 实施任务
- `openspec/changes/feature-name/specs/` - 规范差异

### 2️⃣ 审查与对齐

```
# 查看变更详情
openspec show feature-name

# 验证规范格式
openspec validate feature-name
```

与AI助手讨论，直到所有人同意：

**您** ：能否为角色和团队过滤器添加验收标准？  
**AI** ：我来更新规范差异，添加角色和团队过滤器的场景。  
*\[编辑相应文件\]*

### 3️⃣ 实施任务

```
# 开始实施
/openspec:apply feature-name
```

AI会按照 `tasks.md` 中的清单逐步实施，每完成一个任务会标记为 ✓。

### 4️⃣ 归档与更新规范

```
# 归档完成的变更
openspec archive feature-name --yes
```

归档会将批准的变更合并回 `openspec/specs/` 中，并移动到 `archive/` 目录。

## 实际示例

让我们通过一个完整的示例来理解整个流程：

### 示例：添加用户资料搜索过滤功能

### 步骤1：创建变更提案

```
您：请为添加按角色和团队过滤的用户资料搜索创建一个OpenSpec变更提案
[或使用快捷命令：/openspec:proposal Add profile search filters]
```

AI响应：

```
AI：我来为您创建用户资料过滤器的OpenSpec变更提案。
*创建 openspec/changes/add-profile-filters/ 目录，包含 proposal.md、tasks.md 和规范差异文件*
```

### 步骤2：验证和审查

```
# 确认变更文件夹存在
openspec list

# 验证规范格式
openspec validate add-profile-filters

# 审查提案、任务和规范差异
openspec show add-profile-filters
```

### 步骤3：完善规范

```
您：能否为角色和团队过滤器添加验收标准？
```

AI更新相应的规范差异和任务列表。

### 步骤4：实施变更

```
您：规范看起来很好，让我们实施这个变更吧。
[或使用：/openspec:apply add-profile-filters]
```

AI按任务清单逐步实施，并标记完成状态。

### 步骤5：归档

```
您：请归档这个变更
[或使用：/openspec:archive add-profile-filters]
```

## 支持的AI工具

### 原生斜杠命令支持

![](https://pic1.zhimg.com/v2-70bfad0a87254338333e4b421c641820_1440w.jpg)

### AGENTS.md兼容工具

- Amp
- Jules
- Gemini CLI
- 其他兼容AGENTS.md的工具

## 常用命令

### 查看和管理变更

```
openspec list                    # 查看所有活动变更
openspec view                    # 交互式规范仪表板
openspec show <change-name>      # 显示变更详情
openspec validate <change-name>  # 验证规范格式
```

### 归档变更

```
openspec archive <change-name>   # 交互式归档
openspec archive <change-name> --yes  # 非交互式归档
```

### 工具管理

```
openspec update                  # 刷新AI指导，重新生成斜杠命令
```

## 团队采用指南

### 1\. 初始化团队项目

```
# 在团队仓库中运行
openspec init
```

### 2\. 从新功能开始

要求团队成员将即将到来的工作作为变更提案与AI助手讨论。

### 3\. 增量式发展

每个完成的变更都会归档到记录您系统的实时规范中。

### 4\. 保持工具灵活性

不同团队成员可以使用Claude Code、Cursor或任何AGENTS.md兼容工具，同时共享相同的规范。

### 5\. 工具切换

当有人切换到不同AI工具时，运行：

```
openspec update
```

## 项目上下文设置（可选但推荐）

初始化后，建议完善项目上下文：

### 使用示例提示

```
请阅读 openspec/project.md，并帮助我填写关于我的项目、技术栈和约定的详细信息。
```

### project.md 内容示例

```
# Project Context

## Tech Stack
- Frontend: React + TypeScript
- Backend: Node.js + Express
- Database: PostgreSQL
- Styling: Tailwind CSS

## Code Conventions
- 使用 TypeScript 严格模式
- 组件名使用 PascalCase
- 函数名使用 camelCase
- 常量使用 UPPER_SNAKE_CASE

## Architecture Patterns
- 采用组件化设计
- 前后端分离
- RESTful API 设计
- 响应式设计原则
```

## 规范文件理解

### Delta格式

差异文件显示规范如何变化：

```
## ADDED Requirements          # 新功能
## MODIFIED Requirements       # 行为变更（包含完整更新文本）
## REMOVED Requirements        # 已废弃功能
```

### 格式要求

- 使用 `### Requirement:` 作为标题
- 每个要求至少需要一个 `#### Scenario:` 块
- 在要求文本中使用 SHALL/MUST

## 升级和维护

### 升级OpenSpec

```
npm install -g @fission-ai/openspec@latest
```

### 刷新AI指导

```
# 在每个项目中运行
openspec update
```

## 常见问题

### Q1: AI助手没有显示新的斜杠命令怎么办？

**A:** 重启您的AI编码助手，然后运行 `openspec update` 刷新指导。

### Q2: 可以同时处理多个变更吗？

**A:** 是的，OpenSpec支持同时存在多个变更提案，但一次只能应用一个。

### Q3: 如何修改已归档的规范？

**A:** 创建一个新的变更提案，通过相同的流程来更新现有规范。

### Q4: OpenSpec适用于绿地项目吗？

**A:** OpenSpec特别适合修改现有功能，但也可用于新项目。通常建议从简单功能开始。

### Q5: 团队成员使用不同AI工具可以吗？

**A:** 可以！OpenSpec的AGENTS.md兼容性确保所有AI工具都能理解相同的规范。

## 与其他工具对比

### vs. 没有规范

- **传统方式** ：AI根据模糊提示生成代码，常常遗漏要求或添加不必要功能
- **OpenSpec** ：通过明确规范带来可预测性

### vs. spec-kit

- **spec-kit** ：适合0→1新功能项目
- **OpenSpec** ：在修改现有行为和跨多规范更新时表现更优

### vs. Kiro

- **Kiro** ：将更新分散到多个规范文件夹
- **OpenSpec** ：将相关变更分组在一个文件夹中，便于跟踪

## 社区和支持

- **官方网站** ： [openspec.dev/](https://link.zhihu.com/?target=https%3A//openspec.dev/)
- **GitHub仓库** ： [github.com/Fission-AI/O](https://link.zhihu.com/?target=https%3A//github.com/Fission-AI/OpenSpec)
- **Discord社区** ： [discord.gg/YctCnvvshC](https://link.zhihu.com/?target=https%3A//discord.gg/YctCnvvshC)
- **NPM包** ： [npmjs.com/package/@fiss](https://link.zhihu.com/?target=https%3A//www.npmjs.com/package/%40fission-ai/openspec)

## 总结

OpenSpec通过轻量级但结构化的规范驱动开发方法，成功解决了AI编码助手的不可预测性问题。无论您是个人开发者还是团队协作，OpenSpec都能帮助您：

✅ **提高开发效率** ：减少因需求不明确导致的返工  
✅ **确保代码质量** ：AI根据明确规范生成可预测的代码  
✅ **改善团队协作** ：所有人共享相同的规范理解  
✅ **简化变更管理** ：结构化的变更追踪和归档

现在就开始使用OpenSpec，让您的AI编码助手发挥最大效能！

编辑于 2025-12-05 23:03・江苏