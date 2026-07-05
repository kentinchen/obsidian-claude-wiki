---
title: "claude code第三方API使用WebFetch的问题"
source: "https://zhuanlan.zhihu.com/p/2012819798686454483"
author:
  - "[[vito wang]]"
published:
created: 2026-07-05
description: "问题描述由于claude code的各种限制，懒得折腾就直接接入国内大模型（ qwen3.5-plus，具体接入方法见大模型服务平台百炼控制台）。在获取网页内容时遇到一些问题。最开始与ClaudeCode 排疑 - 知乎类似，即：Fetch(…"
tags:
  - "clippings"
---
15 人赞同了该文章

### 问题描述

由于 [claude code](https://zhida.zhihu.com/search?content_id=270993698&content_type=Article&match_order=1&q=claude+code&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3ODMzOTAwNjcsInEiOiJjbGF1ZGUgY29kZSIsInpoaWRhX3NvdXJjZSI6ImVudGl0eSIsImNvbnRlbnRfaWQiOjI3MDk5MzY5OCwiY29udGVudF90eXBlIjoiQXJ0aWNsZSIsIm1hdGNoX29yZGVyIjoxLCJ6ZF90b2tlbiI6bnVsbH0.1d-GvQlIeYOWS4T0odmY76eITwGEV7uTnXU_Oj1obYk&zhida_source=entity) 的各种限制，懒得折腾就直接接入国内大模型（ `qwen3.5-plus` ，具体接入方法见 [大模型服务平台百炼控制台](https://link.zhihu.com/?target=https%3A//bailian.console.aliyun.com/cn-beijing/%3Ftab%3Ddoc%23/doc/%3Ftype%3Dmodel%26url%3D3023078) ）。在获取网页内容时遇到一些问题。最开始与 [ClaudeCode 排疑 - 知乎](https://zhuanlan.zhihu.com/p/1980757659327165949) 类似，即：

```
Fetch(https://huggingface.co/microsoft/VibeVoice-Realtime-0.5B)
  ⎿  Error: Unable to verify if domain huggingface.co is safe to fetch. This may be due to network restrictions or enterprise security policies blocking claude.ai.
```

### 问题探索

根据 [ClaudeCode 排疑 - 知乎](https://zhuanlan.zhihu.com/p/1980757659327165949) ，在`.claude/settings.json` 设置

```
"skipWebFetchPreflight": true
```

发现WebFetch能获取网页内容，但claude code会多次获取并且无法返回相关结果（后面知道专业术语是“摘要”），如：

```
● Fetch(https://k.sina.com.cn/article_7857201856_1d45362c001902v6uq.html)
  ⎿  Received 53.3KB (200 OK)

● Bash(curl -s "https://k.sina.com.cn/article_7857201856_1d45362c001902v6uq.html" -H "User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64)
      AppleWebKit/537.36" -L 2>/d…)
  ⎿  广西贵港一女子将车停家门口半月，发现踩刹车时有异响，一查天塌了：车底被老鼠囤了20斤红薯和玉米-新浪汽车
     (sinaads = window.sinaads || []).push({})
     正文
     … +30 lines (ctrl+o to expand)

● 已读取该文章，内容如下：
```

即，claude code最终还是调用了curl直接获取网页内容。郁闷~

网上实在找不到解决方法，后来干脆直接问claude code：

```
❯ 为什么你每次fetch完后还要用curl

● 这是因为 WebFetch 工具出现了 API 错误：

  Error: model \`claude-haiku-4-5-20251001\` is not supported

  WebFetch 内部依赖一个不支持的模型来处理网页内容，所以调用失败了。我转而使用 curl 直接获取网页 HTML，然后用 grep 提取文本内容作为替代方案。

  简单来说：
  - WebFetch → 失败（模型不支持）
  - curl → 成功（直接获取原始 HTML）

  如果 WebFetch 能正常工作，我就不需要额外再用 curl 了。
```

这说的，好像你还有脾气了。

于是，我继续，

```
❯ 我应该如何让WebFetch正常工作

● 这个问题出在 WebFetch 工具的内部配置上。错误信息显示它尝试使用 claude-haiku-4-5-20251001 模型来处理网页内容，但这个模型在当前环境中不可用。

  这是系统级别的配置问题，作为用户你可能无法直接修复。以下是几种可能的解决方案：

  可选方案

  1. 使用 curl + Bash 作为替代（目前可行的方法）
  curl -s "URL" | grep -oP '...'
  2. 尝试简化 URL - 有时某些网站会阻止爬虫，可以试试：
    - 使用移动版 URL（如 m.sina.com.cn）
    - 某些网站可能需要特殊处理
  3. 反馈给系统管理员 - 这是根本解决方案：
    - 问题：WebFetch 依赖的模型 claude-haiku-4-5-20251001 不可用
    - 需要更新配置以使用可用的模型
  4. 使用 WebSearch 间接获取信息 - 对新闻类网站，搜索结果有时也能提供所需内容

  ---
  总结：这不是你的问题，是当前环境的配置问题。在修复之前，我会继续使用 curl 方式来帮你获取网页内容。
```

当然不是我的问题，继续问：

```
❯ 如何将WebFetch使用的模型改为qwen3.5-plus

● Searched for 1 pattern, read 1 file (ctrl+o to expand)

● 我找到了配置文件！问题在于 WebFetch 工具的模型配置是由后端 API 服务决定的，而不是由本地配置文件控制。

  当前配置

  {
      "env": {
          "ANTHROPIC_MODEL": "qwen3.5-plus"  // 主模型已正确设置
      },
      "skipWebFetchPreflight": true
  }

  问题根源

  WebFetch 工具内部调用了一个硬编码的模型 claude-haiku-4-5-20251001 来处理网页内容。这个配置在：

  1. 后端 API 服务 - 即 https://coding.dashscope.aliyuncs.com/apps/anthropic
  2. 不在本地配置文件的控制范围内

  可能的解决方案

  方案 1：修改后端 API 配置（需要管理员权限）

  如果你能访问部署这个 API 服务的管理后台，可以修改 WebFetch 工具的默认模型配置。

  方案 2：使用自定义脚本替代

  创建一个本地脚本来替代 WebFetch：

  #!/bin/bash
  # ~/bin/fetch-url
  curl -s "$1" | lynx -dump -stdin

  方案 3：继续使用 curl + 文本提取

  这是当前最实用的方法，我已经在使用了。

  ---
  总结：这个配置不在本地，而是在阿里云 DashScope 的后端服务上。如果你有该服务的管理权限，可以登录管理后台修改 WebFetch 的工具配置；否则，我们继续使用 curl
  方式来获取网页内容。
```

肯定不可能修改后端 API 服务（ [coding.dashscope.aliyuncs.com](https://link.zhihu.com/?target=https%3A//coding.dashscope.aliyuncs.com/apps/anthropic) ），但这些回复让我大概知道了WebFetch的工作原理（关于此，这篇博文也有帮助： [搞懂 Claude Code 联网搜索 2 种方式：自带 WebSearch 和 6 大 MCP 搜索插件对比指南 - Apiyi.com Blog](https://link.zhihu.com/?target=https%3A//help.apiyi.com/claude-code-web-search-websearch-mcp-guide.html) ）

[在 Claude Code 中使用自定义模型服务 | Rokcso's Blog](https://link.zhihu.com/?target=https%3A//rokcso.com/p/using-custom-models-in-claude-code/) 中，提到了环境变量，除了 `ANTHROPIC_MODEL` 还有 `ANTHROPIC_SMALL_FAST_MODEL` ，于是在`.claude/settings.json` 设置：

```
"ANTHROPIC_SMALL_FAST_MODEL": "glm-4.7"
```

这边应该要阿里code plan所能支持的模型才行。

```
推荐模型：qwen3.5-plus（支持图片理解）、kimi-k2.5（支持图片理解）、glm-5、MiniMax-M2.5
更多模型：qwen3-max-2026-01-23、qwen3-coder-next、qwen3-coder-plus、glm-4.7
```

结果，竟然解决了问题。不过返回摘要的速度好像慢了点，可能跟所选择的模型有关，毕竟glm-4.7也曾是旗舰模型。

后来，查阅官方文档 [Claude Code 设置 - Claude Code Docs](https://link.zhihu.com/?target=https%3A//code.claude.com/docs/zh-CN/settings%23%25E7%258E%25AF%25E5%25A2%2583%25E5%258F%2598%25E9%2587%258F) ，发现 `ANTHROPIC_SMALL_FAST_MODEL` 已经被弃用（实际上还可用），于是改为设置 `ANTHROPIC_DEFAULT_HAIKU_MODEL` ，也能正常运行。

### 配置文件参考

`.claude/settings.json` 示例：

```
{
    "env": {
        "ANTHROPIC_AUTH_TOKEN": "your-token",
        "ANTHROPIC_BASE_URL": "https://coding.dashscope.aliyuncs.com/apps/anthropic",
        "ANTHROPIC_MODEL": "qwen3.5-plus",
        "ANTHROPIC_SMALL_FAST_MODEL": "glm-4.7"
    },
    "skipWebFetchPreflight": true
}
```

编辑于 2026-05-04 17:01・福建[有了豆包学习搭子，作文、翻译、讲解，学习轻松无压力](http://www.doubao.com/download/desktop?ug_apk_token=LXrQB&ad_platform_id=zhihu_feed_lead&ug_callback_url=https%3A%2F%2Fsugar.zhihu.com%2Fplutus_adreaper_callback%3Fsi%3Dea95583e-9b4d-49d9-8f40-331a246bc7eb%26os%3D3%26zid%3D1629%26zaid%3D3764980%26zcid%3D3766023%26cid%3D3766023%26event%3D__EVENTTYPE__%26value%3D__EVENTVALUE__%26ts%3D__TIMESTAMP__%26cts%3D__TS__%26mh%3D__MEMBERHASHID__%26adv%3D784532%26ocg%3D0%26cp%3D0%26ocs%3D0%26aic%3D0%26atp%3D0%26ct%3D0%26ed%3DGiBNJgVzfCMmUW9XFyEvRA8xBGxJICwkOhh0FlwxKw1Gdx87VSAsMi9Cb0oDdj1dByRedwhlKy0iVm9XFyU5WQ94CH0Kcmt5eRFmUQVheANYdx8lViYzJHMVdAtEbXyrfWDZIhpJ6w%3D%3D&cb=https%3A%2F%2Fsugar.zhihu.com%2Fplutus_adreaper_callback%3Fsi%3Dea95583e-9b4d-49d9-8f40-331a246bc7eb%26os%3D3%26zid%3D1629%26zaid%3D3764980%26zcid%3D3766023%26cid%3D3766023%26event%3D__EVENTTYPE__%26value%3D__EVENTVALUE__%26ts%3D__TIMESTAMP__%26cts%3D__TS__%26mh%3D__MEMBERHASHID__%26adv%3D784532%26ocg%3D0%26cp%3D0%26ocs%3D0%26aic%3D0%26atp%3D0%26ct%3D0%26ed%3DGiBNJgVzfCMmUW9XFyEvRA8xBGxJICwkOhh0FlwxKw1Gdx87VSAsMi9Cb0oDdj1dByRedwhlKy0iVm9XFyU5WQ94CH0Kcmt5eRFmUQVheANYdx8lViYzJHMVdAtEbXyrfWDZIhpJ6w%3D%3D&ug_semver=v1.0.0&spu=biz%3D0%26ci%3D3766023%26si%3D22caa5e4-dd5c-4671-9de7-ccf67d7ceb00%26ts%3D1783217268%26zid%3D1629)

[

学生党学习搭子-豆包AI！不仅可以输出中英文作文、英语翻译、作文修改润色，还能有海量题目讲解

](http://www.doubao.com/download/desktop?ug_apk_token=LXrQB&ad_platform_id=zhihu_feed_lead&ug_callback_url=https%3A%2F%2Fsugar.zhihu.com%2Fplutus_adreaper_callback%3Fsi%3Dea95583e-9b4d-49d9-8f40-331a246bc7eb%26os%3D3%26zid%3D1629%26zaid%3D3764980%26zcid%3D3766023%26cid%3D3766023%26event%3D__EVENTTYPE__%26value%3D__EVENTVALUE__%26ts%3D__TIMESTAMP__%26cts%3D__TS__%26mh%3D__MEMBERHASHID__%26adv%3D784532%26ocg%3D0%26cp%3D0%26ocs%3D0%26aic%3D0%26atp%3D0%26ct%3D0%26ed%3DGiBNJgVzfCMmUW9XFyEvRA8xBGxJICwkOhh0FlwxKw1Gdx87VSAsMi9Cb0oDdj1dByRedwhlKy0iVm9XFyU5WQ94CH0Kcmt5eRFmUQVheANYdx8lViYzJHMVdAtEbXyrfWDZIhpJ6w%3D%3D&cb=https%3A%2F%2Fsugar.zhihu.com%2Fplutus_adreaper_callback%3Fsi%3Dea95583e-9b4d-49d9-8f40-331a246bc7eb%26os%3D3%26zid%3D1629%26zaid%3D3764980%26zcid%3D3766023%26cid%3D3766023%26event%3D__EVENTTYPE__%26value%3D__EVENTVALUE__%26ts%3D__TIMESTAMP__%26cts%3D__TS__%26mh%3D__MEMBERHASHID__%26adv%3D784532%26ocg%3D0%26cp%3D0%26ocs%3D0%26aic%3D0%26atp%3D0%26ct%3D0%26ed%3DGiBNJgVzfCMmUW9XFyEvRA8xBGxJICwkOhh0FlwxKw1Gdx87VSAsMi9Cb0oDdj1dByRedwhlKy0iVm9XFyU5WQ94CH0Kcmt5eRFmUQVheANYdx8lViYzJHMVdAtEbXyrfWDZIhpJ6w%3D%3D&ug_semver=v1.0.0&spu=biz%3D0%26ci%3D3766023%26si%3D22caa5e4-dd5c-4671-9de7-ccf67d7ceb00%26ts%3D1783217268%26zid%3D1629)

赞同 15