---
title: "Obsidian 接入 Claude 与国产大模型：让 AI 成为你的知识库协作者"
source: "https://zhuanlan.zhihu.com/p/2017274639743721534"
author:
  - "[[千年老鸟]]"
published:
created: 2026-04-16
description: "传统的 AI 辅助笔记方式，无非是复制粘贴到聊天窗口，让 AI 帮忙总结、改写，再贴回来。这种“切出切进”的操作不仅打断思路，AI 也无法真正理解你笔记的上下文。 现在，有了 Claudian 插件，我们可以把 Claude（…"
tags:
  - "clippings"
---
传统的 AI 辅助笔记方式，无非是复制粘贴到聊天窗口，让 AI 帮忙总结、改写，再贴回来。这种“切出切进”的操作不仅打断思路，AI 也无法真正理解你笔记的上下文。

现在，有了 **Claudian 插件** ，我们可以把 Claude（包括国产大模型）直接“请进” [Obsidian](https://zhida.zhihu.com/search?content_id=271609078&content_type=Article&match_order=1&q=Obsidian&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3NzY1MTE2NzIsInEiOiJPYnNpZGlhbiIsInpoaWRhX3NvdXJjZSI6ImVudGl0eSIsImNvbnRlbnRfaWQiOjI3MTYwOTA3OCwiY29udGVudF90eXBlIjoiQXJ0aWNsZSIsIm1hdGNoX29yZGVyIjoxLCJ6ZF90b2tlbiI6bnVsbH0.zbZ1H0gaXpunJADSA63oBm_pQHWPtbWBrBOhVGY5smk&zhida_source=entity) ，让 AI 在笔记内部与你协作，像一位真正的伙伴一样参与思考、整理和创作。

## 什么是 Claudian？

[Claudian](https://link.zhihu.com/?target=https%3A//github.com/YishenTu/claudian) 是一款 Obsidian 桌面端插件，它的作用是将 **Claude Code CLI** 的能力无缝集成到 Obsidian 中。

简单来说，Claudian = **Obsidian 里的 Claude 助手** 。  
它支持 Claude 官方的 **Skills 体系** ，允许你在笔记中直接与 AI 对话，并且能够内联编辑选中的文本。

更重要的是， **它不仅支持官方 Claude API，也兼容任何实现了 [Anthropic API](https://zhida.zhihu.com/search?content_id=271609078&content_type=Article&match_order=1&q=Anthropic+API&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3NzY1MTE2NzIsInEiOiJBbnRocm9waWMgQVBJIiwiemhpZGFfc291cmNlIjoiZW50aXR5IiwiY29udGVudF9pZCI6MjcxNjA5MDc4LCJjb250ZW50X3R5cGUiOiJBcnRpY2xlIiwibWF0Y2hfb3JkZXIiOjEsInpkX3Rva2VuIjpudWxsfQ.qsi7bUI7pYUetxNQvyYZt4NtkLWHlMy6cyapJn01Hfk&zhida_source=entity) 接口的国产大模型** ，比如智谱 GLM、DeepSeek、 [月之暗面 Kimi](https://zhida.zhihu.com/search?content_id=271609078&content_type=Article&match_order=1&q=%E6%9C%88%E4%B9%8B%E6%9A%97%E9%9D%A2+Kimi&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3NzY1MTE2NzIsInEiOiLmnIjkuYvmmpfpnaIgS2ltaSIsInpoaWRhX3NvdXJjZSI6ImVudGl0eSIsImNvbnRlbnRfaWQiOjI3MTYwOTA3OCwiY29udGVudF90eXBlIjoiQXJ0aWNsZSIsIm1hdGNoX29yZGVyIjoxLCJ6ZF90b2tlbiI6bnVsbH0.813YLwleSsxUIegDk9oheS90fgIIP6lfuziaHZLb2Tg&zhida_source=entity) 等。这让我们可以自由选择模型，甚至在国内网络环境下顺畅使用。

## 准备工作

在安装 Claudian 之前，请确保满足以下条件：

- ✅ 已安装 [Claude Code CLI](https://link.zhihu.com/?target=https%3A//code.claude.com/docs/en/overview) （强烈建议使用 Native Install 方式）
- ✅ Obsidian 版本 ≥ **v1.8.9**
- ✅ 拥有支持 Anthropic API 格式的 API Key（官方 Claude 或国产模型均可）
- ✅ 操作系统：macOS / Linux / Windows（仅桌面端）

如果你使用国产模型，请确认该平台提供了兼容 Anthropic API 的接入方式。例如：

- [智谱 BigModel](https://link.zhihu.com/?target=https%3A//docs.z.ai/devpack/tool/claude) （glm-5 等模型）
- [DeepSeek](https://link.zhihu.com/?target=https%3A//api-docs.deepseek.com/guides/anthropic_api)
- [OpenRouter](https://link.zhihu.com/?target=https%3A//openrouter.ai/docs/guides/claude-code-integration)
- [Kimi（月之暗面）](https://link.zhihu.com/?target=https%3A//platform.moonshot.ai/docs/guide/agent-support)

## 安装 Claudian 插件（手动）

由于 Claudian 尚未上架 Obsidian 社区市场，需要手动安装。

### 1️⃣ 下载插件文件

访问 [GitHub Releases 页面](https://link.zhihu.com/?target=https%3A//github.com/YishenTu/claudian/releases/latest) ，下载最新版本的三个文件：

- `main.js`
- `manifest.json`
- `styles.css`
![](https://pic2.zhimg.com/v2-51a9aa666d1420909a367593dde61cff_1440w.jpg)

2️⃣ 创建插件目录

在你的 Obsidian 仓库（Vault）中，创建以下目录：

```
/你的仓库路径/.obsidian/plugins/claudian/
```

### 3️⃣ 拷贝文件

将下载的三个文件复制到 `claudian` 文件夹内。

![](https://pic2.zhimg.com/v2-209b5f6f4c674c92c60cc6ee9a625c93_1440w.jpg)

4️⃣ 启用插件

在 Obsidian 中，进入 **设置 → 社区插件** ，点击“刷新”按钮，然后找到 **Claudian** 并启用。  

![](https://pica.zhimg.com/v2-856166985c4fce5d520f27e22ad07e52_1440w.jpg)

如果左侧功能区出现了 🤖 机器人图标，说明插件已成功加载。  

![](https://pic2.zhimg.com/v2-107d9ac13263f17d09574bd697c4fe01_1440w.jpg)

## 配置模型环境

启用插件后，进入 **设置 → Claudian → Environment** ，在这里配置你的 API 信息。

你可以在环境变量中填写：

- `ANTHROPIC_API_KEY` ：你的 API Key
- `ANTHROPIC_BASE_URL` ：API 请求地址（如果是国产模型，需要填写对应的中转地址）
- `ANTHROPIC_MODEL` ：模型名称（如 `claude-3-5-sonnet-20241022` 或 `glm-` 5）

例如，使用智谱 BigModel 的配置：

```
ANTHROPIC_API_KEY=your_zhipu_api_key
ANTHROPIC_BASE_URL=https://open.bigmodel.cn/api/anthropic
ANTHROPIC_MODEL=glm-5
```

Pasted image 20260317161723.png  
配置完成后，Claudian 就会使用你指定的模型与 API 进行交互。

![](https://pica.zhimg.com/v2-4e106ef58b8da1bda996545117b2dfb2_1440w.jpg)

## 在 Obsidian 中与 Claude 协作

### 基础使用

点击左侧的 🤖 机器人图标，或者通过命令面板（ `Cmd/Ctrl + P` ）搜索“Claudian”，即可打开聊天窗口。

最常用的场景是 **选中一段笔记文本** ，然后让 AI 直接帮你改写、扩写、总结或翻译。  
操作方式：

1. 在笔记中选中需要处理的文字。
2. 打开 Claudian 聊天窗口，输入你的指令（例如：“用更通俗的语言重写这一段”）。
3. 点击发送，AI 的修改结果会 **直接替换** 你选中的文本（或者按照你的要求插入到指定位置）。

这种“内联编辑”的体验，让 AI 真正成为你的写作搭档，而不是隔着一层对话框的顾问。

### 使用 Skills（技能）

Claudian 最大的亮点是完整支持 **Claude Code 的 Skills 体系** 。  
在聊天输入框中输入 `/` ，就会弹出所有可用的命令和已注册的 Skills。

你可以直接调用这些技能来完成复杂任务，例如：

- `/重构` ：将一篇杂乱的文章梳理成结构清晰的文档。
- `/拆解` ：把一个复杂概念分解成多个要点。
- `/大纲` ：根据现有内容生成文章大纲或 TODO 列表。
- `/知识卡片` ：将笔记转换成适合复习的知识卡片格式。
- `/统一风格` ：让整篇文档的语言风格保持一致。

Skills 的本质是预定义的提示词模板 + 上下文理解，你可以自己编写或从社区下载更多技能，让 Claude 学会更多“招式”。

## 实战场景举例

### 场景一：将零散笔记整理成知识卡片

假设你在阅读时随手记下了几个零散的观点，现在想整理成一张便于回顾的知识卡片。  
只需选中这些笔记，输入 `/知识卡片` ，Claude 就会自动提取关键信息，生成结构化的卡片，甚至添加标签和链接。

### 场景二：重构技术文章

写了一篇技术文章初稿，但觉得逻辑混乱、表达不够清晰。  
选中全文，输入 `/重构` ，并附上你的要求（如“按照问题-解决方案-总结的结构重新组织”），Claude 会重写文章，同时保留所有技术细节。

### 场景三：生成学习大纲

你有一个文件夹里收集了多篇关于“机器学习”的笔记，想让 AI 帮你梳理出学习路径。  
在聊天窗口中输入 `/大纲 请根据当前文件夹中的笔记，生成一份机器学习学习大纲` ，Claude 会分析所有笔记，输出一份包含章节、重点概念的提纲。

## 为什么这种组合值得尝试？

1. **沉浸式体验** ：无需离开 Obsidian，AI 就在你的知识库里工作。
2. **上下文理解** ：Claude 能读取你当前笔记乃至整个仓库的内容，回答更具针对性。
3. **国产模型友好** ：不必依赖海外 API，智谱、DeepSeek 等模型同样可以胜任，速度和成本可控。
4. **技能扩展** ：通过 Skills，你可以不断扩展 AI 的能力边界，让它学会你需要的特定工作流。
5. **数据安全** ：笔记仍然保存在本地，AI 只是辅助编辑，不会劫持你的数据。

## 写在最后

如果说 Obsidian 给了我们一个存放思想的“仓库”，那么 Claudian + Claude/国产大模型 就为这个仓库配备了一位永不疲倦的“图书管理员”——他不仅能帮你整理书架，还能和你一起探讨书中的内容，甚至帮你写出新的篇章。

现在，你的 Obsidian 不再只是笔记库，而是一个 **可以持续进化、与 AI 协同思考的个人知识系统** 。

如果你也想让笔记真正“活”起来，不妨按照本文的步骤，试试这个组合。欢迎在评论区分享你的使用心得！

**觉得有用的话，别忘了点赞、收藏、转发～我们下篇见！**

编辑于 2026-03-17 16:38・广东