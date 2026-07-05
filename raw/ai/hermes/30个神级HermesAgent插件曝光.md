---
title: "30个神级HermesAgent插件曝光！把AI培育成你最得力的专属特工"
source: "https://www.toutiao.com/article/7647230875163247146/?wid=1783006577477"
author:
  - "[[余晖晚风信]]"
published: 2026-06-04
created: 2026-07-02
description: "在开源AI智能体领域，HermesAgent 凭借强大的可定制性正受到广泛关注。本文精心盘点并汇总了当前实际公开的 30 个核心周边仓库，内容涵盖搜索、记忆扩展、自动化浏览器操作、多智能体委派及高效工作区等全方位生态。"
tags:
  - "clippings"
---
![](https://p3-sign.toutiaoimg.com/tos-cn-i-axegupay5k/17c1816447d84bd3a7dd385cc1546ead~tplv-tt-origin-web:gif.jpeg?_iz=58558&from=article.pc_detail&lk3s=953192f4&x-expires=1783611377&x-signature=85wQOWoDPLMSKI6qlojCG8PrFUs%3D)

在开源AI智能体领域，HermesAgent 凭借强大的可定制性正受到广泛关注。本文精心盘点并汇总了当前实际公开的 30 个核心周边仓库，内容涵盖搜索、记忆扩展、自动化浏览器操作、多智能体委派及高效工作区等全方位生态。

## 搜索

\[ 01 \] amanning3390/hermeshub

面向 Hermes Agent 的 Skills Hub（技能中心）。可以作为寻找、分享和安装社区技能的入口。

URL: https://github.com/amanning3390/hermeshub

\[ 02 \] chigwell/skilldock.io

基于 AgentSkills 规范的 Skill 注册表。可以跨 OpenClaw、Claude 及支持 Skills 的智能体，发现、安装和发布带有版本控制的 Skills。

URL: https://github.com/chigwell/skilldock.io

## 记忆与内存扩展

\[ 03 \] vectorize-io/hindsight

可以为智能体添加具备学习能力的记忆。适用于沿着语义和时间流向来召回过去信息的场景。

URL: https://github.com/vectorize-io/hindsight

\[ 04 \] elkimek/honcho-self-hosted

面向 Hermes Agent，支持私有化部署 Honcho 的记忆层。通过 OpenRouter 和 Venice 的组合，无需修改代码即可使用记忆层。

URL: https://github.com/elkimek/honcho-self-hosted

\[ 05 \] yantrikos/yantrikdb-hermes-plugin

面向 Hermes Agent，支持添加 YantrikDB 的内存提供程序。可处理记忆规范化、矛盾追踪、时效性排序以及可解释性召回。

URL: https://github.com/yantrikos/yantrikdb-hermes-plugin

\[ 06 \] plur-ai/plur

可以创建供多个 AI 智能体共享的记忆。在 Hermes 的外部，放置一个供智能体之间共同使用的公共内存。

URL: https://github.com/plur-ai/plur

\[ 07 \] amanning3390/flowstate-qmd

支持面向 AI 智能体的预读型内存。作为 Hermes 2026 Hackathon 的作品，可以处理将记忆与 RAG 结合的扩展。

URL: https://github.com/amanning3390/flowstate-qmd

## 技能自制与自我进化

\[ 08 \] AMAP-ML/SkillClaw

支持通过会话历史来进化技能库的机制。作为一种智能体式的 Evolver，可以持续改进 Skill。

URL: https://github.com/AMAP-ML/SkillClaw

\[ 09 \] Romanescu11/hermes-skill-factory

面向 Hermes Agent，可以监控工作流程并将其转换为可复用的 Skill。能够把每次都需要解释的步骤，留存为下次起就能直接使用的形式。

URL: https://github.com/Romanescu11/hermes-skill-factory

\[ 10 \] Cranot/super-hermes

在 Hermes Agent 中添加支持编写专属分析提示词（Prompt）的 Skill。甚至可以将分析时的提示词创建工作也交给 Hermes 侧来完成。

URL: https://github.com/Cranot/super-hermes

\[ 11 \] Yonkoo11/hermes-dojo

监控 Hermes Agent 的性能，找出薄弱的 Skill，并通过自我进化进行修复。涵盖到改进结果的报告输出。

URL: https://github.com/Yonkoo11/hermes-dojo

\[ 12 \] armelhbobdad/bmad-module-skill-forge

可将代码仓库、文档网站以及开发者的讨论转换为符合 agentskills.io 规范的 Skill。可以创建带有固定版本和来源信息的 Skill。

URL: https://github.com/armelhbobdad/bmad-module-skill-forge

## 搜索与调研

\[ 13 \] robbyczgw-cla/hermes-web-search-plus

为 Hermes Agent 添加支持多个提供商的网络搜索与提取功能。可以使用搜索目标路由、质量报告以及调研模式。

URL: https://github.com/robbyczgw-cla/hermes-web-search-plus

\[ 14 \] ZeroPointRepo/youtube-skills

可让 AI 智能体使用 YouTube 的字幕获取、视频搜索以及频道浏览功能。这是一款可在 Hermes-Agent、OpenClaw、Claude Code、Cursor、Windsurf 中使用的多智能体兼容 Skill。

URL: https://github.com/ZeroPointRepo/youtube-skills

## 浏览器与网页操作

\[ 15 \] unmodeled-tyler/vessel-browser

可使用专为智能体打造的开源 AI 浏览器。可在 Linux、Mac、Windows 上处理持久化状态、MCP 控制、BYOK（自带密钥）以及自主浏览。

URL: https://github.com/unmodeled-tyler/vessel-browser

\[ 16 \] raulvidis/hermes-cloudflare

支持从 Hermes Agent 中使用 Cloudflare Browser Rendering。可处理网页的爬取、抓取以及正文提取。

URL: https://github.com/raulvidis/hermes-cloudflare

\[ 17 \] anpicasso/hermes-plugin-chrome-profiles

可以在 Hermes Agent 的浏览器工具中切换 Chrome 配置文件（Profile）。通过 CDP 协议，可以灵活切换使用多个 Chrome 配置文件。

URL: https://github.com/anpicasso/hermes-plugin-chrome-profiles

## 沟通与生产力

\[ 18 \] 42-evey/hermes-plugins

面向 Hermes Agent 的自制插件集。可处理目标管理、智能体间桥接、模型选择以及成本控制。

URL: https://github.com/42-evey/hermes-plugins

\[ 19 \] Andrew-Girgis/microsoft-workspace-skill

支持从 Hermes Agent 中使用 Microsoft Graph API。可处理与 Outlook 日历、邮件、联系人的联动。

URL: https://github.com/Andrew-Girgis/microsoft-workspace-skill

\[ 20 \] Alexeyisme/hermes-spotify-skill

支持从 Hermes Agent 中处理 Spotify 的播放操作。可在 Linux 和 树莓派（Raspberry Pi）4/5 上使用搜索、播放、暂停、跳过、音量调节以及设备切换。

URL: https://github.com/Alexeyisme/hermes-spotify-skill

## 执行环境与部署

\[ 21 \] xmbshwll/hermes-agent-docker

可以使用面向 Hermes Agent 的 Docker 沙箱镜像。可为在 Docker 环境中运行 Hermes 搭建好基础。

URL: https://github.com/xmbshwll/hermes-agent-docker

\[ 22 \] 0xrsydn/nix-hermes-agent

可以使用面向 Hermes Agent 的 Nix 包和 NixOS 模块。能够以在 Nix 或 NixOS 上极易复现的形式来处理 Hermes。

URL: https://github.com/0xrsydn/nix-hermes-agent

\[ 23 \] ellickjohnson/portainer-stack-hermes

可以通过 Portainer 堆栈部署 Hermes Agent。可以运行带有 ttyd Web 终端的 Hermes。

URL: https://github.com/ellickjohnson/portainer-stack-hermes

\[ 24 \] 0xNyk/openclaw-to-hermes

支持从 OpenClaw 迁移到 Hermes Agent。这是一款经过实战测试的迁移工具。

URL: https://github.com/0xNyk/openclaw-to-hermes

## 多智能体

\[ 25 \] Ridwannurudeen/hermes-council

面向 Hermes Agent，可以使用多视角委员会的 MCP 服务器。可以将对抗性的、多视角的论证过程融入到智能体的工作中。

URL: https://github.com/Ridwannurudeen/hermes-council

\[ 26 \] Rainhoole/hermes-agent-acp-skill

可以在 Hermes 中使用 ACP 风格的多智能体委派。支持在 Hermes、Codex、Claude Code 之间进行任务委派。

URL: https://github.com/Rainhoole/hermes-agent-acp-skill

## 安全、检测与支付

\[ 27 \] nativ3ai/hermes-payguard

支持从 Hermes Agent 中处理 USDC 和 x402 的支付。这是用于将支付周边功能融入到智能体工作中的插件。

URL: https://github.com/nativ3ai/hermes-payguard

\[ 28 \] resemble-ai/detect-skill

可以使用深度伪造（Deepfake）检测的 Skill。可通过 Resemble AI 检测 AI 生成的声音、图片和视频。

URL: https://github.com/resemble-ai/detect-skill

## GUI 与工作区

\[ 29 \] outsourc-e/hermes-workspace

可以使用面向 Hermes Agent 的 Web 工作区。可在单个画面中处理对话、终端、内存、Skills 以及检查器（Inspector）。

URL: https://github.com/outsourc-e/hermes-workspace

\[ 30 \] dodo-reach/hermes-desktop

可以从 Mac 管理 Hermes。通过纯 SSH 链接，无需网关、公开端口或浏览器层即可进行管理。

URL: https://github.com/dodo-reach/hermes-desktop

## 如何选择

无需全部添加这 30 个插件。如果您想让它拥有记忆，可以从内存扩展开始；如果您想保留相同的作业，可以从技能自制开始；如果您想用于日常调研，可以从搜索与调研开始；如果是每天动用，从执行环境或工作区中各挑选 1 个或 2 个逐步尝试，这样更易于推进。

仅仅收集名字是无法融入到实际业务中的。请选择一个在您自己的工作中反复进行的作业，并从与该作业最贴近的仓库开始尝试。