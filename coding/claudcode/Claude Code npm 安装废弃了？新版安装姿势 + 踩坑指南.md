---
title: "Claude Code npm 安装废弃了？新版安装姿势 + 踩坑指南"
source: "https://zhuanlan.zhihu.com/p/2035743392399894164"
author:
  - "[[杰哥]]"
published:
created: 2026-06-29
description: "Claude Code npm 安装废弃了？新版安装姿势 + 踩坑指南 作者：小胡 缘起：今天想装 Claude Code，结果 npm install 报错说废弃了 前几天有个朋友跟我说，他按照去年收藏的教程，在终端里敲了一行 npm install -g @…"
tags:
  - "clippings"
---
1 人赞同了该文章

[Claude Code](https://zhida.zhihu.com/search?content_id=274389959&content_type=Article&match_order=1&q=Claude+Code&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3ODI4OTg3MTksInEiOiJDbGF1ZGUgQ29kZSIsInpoaWRhX3NvdXJjZSI6ImVudGl0eSIsImNvbnRlbnRfaWQiOjI3NDM4OTk1OSwiY29udGVudF90eXBlIjoiQXJ0aWNsZSIsIm1hdGNoX29yZGVyIjoxLCJ6ZF90b2tlbiI6bnVsbH0.LeJNEfVtkQO7snpXocQke2tjy4h0vulstmAllLUodYY&zhida_source=entity) npm 安装废弃了？新版安装姿势 + 踩坑指南

![](https://pic1.zhimg.com/v2-5442f7272bd2ac5fa32852aa2f5127e6_1440w.jpg)

作者：小胡

缘起：今天想装 Claude Code，结果 npm install 报错说废弃了

前几天有个朋友跟我说，他按照去年收藏的教程，在终端里敲了一行 `npm install -g @anthropic-ai/claude-code` ，想装一下 Claude Code。结果回车一按，屏幕上赫然跳出一行：

**NPM (Deprecated)**

他当时就懵了——"我是不是装了个寂寞？"

如果你也在某个教程里看到过 npm 安装方式，或者你在项目迁移时遇到旧项目用 npm 装的 Claude Code 不知道要不要更新，这篇文章就是写给你的。

今天我把 Claude Code **最新的安装方式** 、 **踩坑经历** 、 **各平台详细步骤** ，一次性给你整理清楚。照着做，保证你少走弯路。

一、为什么 npm 安装被废弃了？

先说结论： **不是你的问题，是 Anthropic 官方改了路线。**

去 GitHub 仓库看一眼就明白了——anthropics/claude-code 的 README 里已经明确标注：

**Note: Installation via npm is deprecated.**

什么意思呢？就是官方不推荐、也不再维护 npm 这条安装路径了。以前 npm 确实是唯一方式，但现在 Claude Code 已经从"一个 [Node.js](https://zhida.zhihu.com/search?content_id=274389959&content_type=Article&match_order=1&q=Node.js&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3ODI4OTg3MTksInEiOiJOb2RlLmpzIiwiemhpZGFfc291cmNlIjoiZW50aXR5IiwiY29udGVudF9pZCI6Mjc0Mzg5OTU5LCJjb250ZW50X3R5cGUiOiJBcnRpY2xlIiwibWF0Y2hfb3JkZXIiOjEsInpkX3Rva2VuIjpudWxsfQ.x3lnL4hNcfHZeChXyct8WXvIyhfdk_QamDyyi8rVzvQ&zhida_source=entity) 全局包"升级成了 **一个独立的桌面/终端应用** ，有了自己的原生安装器、自动更新机制、桌面 GUI，甚至 Windows 的 [WinGet](https://zhida.zhihu.com/search?content_id=274389959&content_type=Article&match_order=1&q=WinGet&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3ODI4OTg3MTksInEiOiJXaW5HZXQiLCJ6aGlkYV9zb3VyY2UiOiJlbnRpdHkiLCJjb250ZW50X2lkIjoyNzQzODk5NTksImNvbnRlbnRfdHlwZSI6IkFydGljbGUiLCJtYXRjaF9vcmRlciI6MSwiemRfdG9rZW4iOm51bGx9.GIsxCwjOC90igoeCC_3al1CqUaL1GqwBHjAQ8dx-3Gs&zhida_source=entity) 支持都安排上了。

简单说： **npm 方式还能用，但官方已经把它当"遗产模式"对待了。新功能、自动更新、安全补丁，可能都不会第一时间覆盖到 npm 安装的版本。**

所以，赶紧换成官方推荐的方式吧。

![](https://pic2.zhimg.com/v2-4700af3e7ecf860956e6299ba9bab487_1440w.jpg)

二、新版安装方式（推荐）

Anthropic 现在主推的是 **原生安装器** ，一句话搞定，还能自动更新。

macOS / Linux（最推荐）

打开终端，复制粘贴这一行：

bash

```
curl -fsSL https://claude.ai/install.sh | bash
```

就这么简单。安装器会自动检测你的系统、下载最新版本的 Claude Code、配置好环境变量。安装完成后，原生安装器还会 **在后台自动更新** ，你以后基本不用管。

**小贴士** ：如果你偏好稳定版本（跳过有严重 bug 的更新），可以装 stable 频道： >

bash

```
> curl -fsSL https://claude.ai/install.sh | bash -s stable

>
```

安装完验证一下：

bash

```
claude --version
```

看到版本号就说明安装成功了。

Windows（PowerShell）

Windows 用户同样有超简单的原生安装：

powershell

```
irm https://claude.ai/install.ps1 | iex
```

如果你在 CMD 里操作，用这条：

batch

```
curl -fsSL https://claude.ai/install.cmd -o install.cmd && install.cmd && del install.cmd
```

⚠️ **注意** ：Windows 用户强烈建议同时安装 Git for Windows，这样 Claude Code 可以在内部使用 Bash 执行命令，体验更好。

[Homebrew](https://zhida.zhihu.com/search?content_id=274389959&content_type=Article&match_order=1&q=Homebrew&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3ODI4OTg3MTksInEiOiJIb21lYnJldyIsInpoaWRhX3NvdXJjZSI6ImVudGl0eSIsImNvbnRlbnRfaWQiOjI3NDM4OTk1OSwiY29udGVudF90eXBlIjoiQXJ0aWNsZSIsIm1hdGNoX29yZGVyIjoxLCJ6ZF90b2tlbiI6bnVsbH0.en5Fy1Cvg0nOIio4f5BzMSn8S4bsUbt4vGgnft9sfvU&zhida_source=entity) （macOS / Linux）

如果你本身就是 Homebrew 用户，那更简单：

bash

```
# 稳定版（推荐）

brew install --cask claude-code

# 或者最新版（追新党）

brew install --cask claude-code@latest
```

**注意** ：Homebrew 安装的版本 **不会自动更新** 。你需要定期运行 `brew upgrade claude-code` 来获取新版本。如果不想手动升级，可以设置 `CLAUDE*CODE*PACKAGE*MANAGER*AUTO_UPDATE=1` ，让 Claude Code 自动跑升级命令。

WinGet（Windows）

powershell

```
winget install Anthropic.ClaudeCode
```

和 Homebrew 一样，需要手动升级： `winget upgrade Anthropic.ClaudeCode` 。

三、各平台系统要求

装之前先确认一下你的环境：

| 平台 | 最低版本 |
| --- | --- |
| macOS | 13.0+ |
| Windows | 10 1809+ 或 Server 2019+ |
| Ubuntu | 20.04+ |
| Debian | 10+ |
| Alpine Linux | 3.19+ |
| 内存 | 4 GB+ |
| 处理器 | x64 或 ARM64 |

Shell 支持 Bash、Zsh、PowerShell、CMD。

四、安装后怎么做？

安装完成后，打开你的项目目录，直接运行：

bash

```
claude
```

第一次运行会打开浏览器，引导你登录。

**重要提醒** ：Claude Code 需要 **Pro、Max、Team、Enterprise 或 Console** 账号。 **免费的 Claude.ai 计划不支持 Claude Code。** 如果你还没有付费账号，需要先去 Claude 官网升级。

登录完成后，你就可以在终端里用自然语言让 Claude 帮你写代码、改 Bug、解释代码、管理 Git 了。

![](https://picx.zhimg.com/v2-f30d2691da3411f4ad82698bdb98bb23_1440w.jpg)

五、踩坑指南 ️

我在自己用和帮助朋友的过程中，遇到了不少坑，帮你总结一下。

坑 1：旧 npm 版本和新版本冲突

如果你之前通过 npm 安装过 Claude Code，建议先卸载再装新的：

bash

```
# 卸载旧版 npm 安装

npm uninstall -g @anthropic-ai/claude-code

# 然后安装新版

curl -fsSL https://claude.ai/install.sh | bash
```

如果不卸载旧版，可能出现两个版本共存导致 `claude` 命令指向旧版的情况。

坑 2：Homebrew 安装后不自动更新

这是最常见的问题——装了之后发现版本不对。记住： **Homebrew 安装需要手动升级** ！

bash

```
brew upgrade claude-code
```

或者设置环境变量让 Claude Code 自动升级：

bash

```
export CLAUDE_CODE_PACKAGE_MANAGER_AUTO_UPDATE=1
```

坑 3：Windows 下 PowerShell 和 CMD 搞混

很多 Windows 新手分不清 PowerShell 和 CMD。教你一招： **看提示符** 。

✅显示 `PS C:\Users\xxx>` → PowerShell

✅显示 `C:\Users\xxx>` → CMD

PowerShell 用 `irm` 命令，CMD 用 `curl` 。用错了会报错。

坑 4： `command not found` 或 `不是内部或外部命令`

安装完成后输入 `claude` 报这个错，通常是 **PATH 没生效** 。解决方法：

1 **重启终端** （关闭再打开），让环境变量重新加载

2或者运行 `source ~/.zshrc` （Zsh）或 `source ~/.bashrc` （Bash）

3Windows 用户可能需要重启命令行窗口

坑 5：Alpine Linux 缺少依赖

如果你在 Alpine Linux 上安装，需要先安装这些依赖：

bash

```
apk add libgcc libstdc++ ripgrep
```

然后在 `settings.json` 里配置：

json

```
{

  "env": {

    "USE_BUILTIN_RIPGREP": "0"

  }

}
```

坑 6：账号权限问题

Claude Code **不支持免费账号** 。如果你用的是 Claude.ai 的免费计划，登录后会提示无法使用。解决方案：

1升级到 Pro（$20/月）或 Max（$100-200/月）计划

2或者使用第三方 API 提供商： [Amazon Bedrock](https://zhida.zhihu.com/search?content_id=274389959&content_type=Article&match_order=1&q=Amazon+Bedrock&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3ODI4OTg3MTksInEiOiJBbWF6b24gQmVkcm9jayIsInpoaWRhX3NvdXJjZSI6ImVudGl0eSIsImNvbnRlbnRfaWQiOjI3NDM4OTk1OSwiY29udGVudF90eXBlIjoiQXJ0aWNsZSIsIm1hdGNoX29yZGVyIjoxLCJ6ZF90b2tlbiI6bnVsbH0.OcCQEasRWIlNvTUf6GUnCO55RoWGAvgDi7KWQ68Ik1w&zhida_source=entity) 、Google Vertex AI、 [Microsoft Foundry](https://zhida.zhihu.com/search?content_id=274389959&content_type=Article&match_order=1&q=Microsoft+Foundry&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3ODI4OTg3MTksInEiOiJNaWNyb3NvZnQgRm91bmRyeSIsInpoaWRhX3NvdXJjZSI6ImVudGl0eSIsImNvbnRlbnRfaWQiOjI3NDM4OTk1OSwiY29udGVudF90eXBlIjoiQXJ0aWNsZSIsIm1hdGNoX29yZGVyIjoxLCJ6ZF90b2tlbiI6bnVsbH0.lt_oat5tfOwivYAJ1-kOtir-h6ufVUs6gYHzvODqj7Y&zhida_source=entity)

六、版本管理小技巧

安装成功后，你可能还想控制一下更新策略：

设置更新频道

通过 `/config` 命令或修改 `settings.json` ：

json

```
{

  "autoUpdatesChannel": "stable"

}
```

✅ `"latest"` （默认）：第一时间获得新功能

✅ `"stable"` ：稳定版，大约晚一周发布，跳过有严重 bug 的版本

锁定最低版本

如果你当前版本用得很舒服，不想被"降级"：

json

```
{

  "autoUpdatesChannel": "stable",

  "minimumVersion": "2.1.100"

}
```

完全关闭自动更新

json

```
{

  "env": {

    "DISABLE_AUTOUPDATER": "1"

  }

}
```

七、验证安装是否一切正常

安装完后，除了 `claude --version` ，还有一个更全面的检查命令：

bash

```
claude doctor
```

这个命令会检查你的安装、配置、账号状态等，相当于给 Claude Code 做一次"体检"。如果有问题，它会明确告诉你。

八、从 npm 迁移到新版，完整步骤

如果你现在还在用 npm 安装的老版本，建议按以下步骤迁移：

bash

```
# 1. 卸载旧版

npm uninstall -g @anthropic-ai/claude-code

# 2. 确认卸载完成（应该返回空或提示未找到）

which claude

# 3. 安装新版（macOS/Linux）

curl -fsSL https://claude.ai/install.sh | bash

# 4. 验证

claude --version

# 5. 体检

claude doctor

# 6. 启动

claude
```

整个过程不超过 3 分钟，但能确保你用上最新的 Claude Code。

写在最后

Claude Code 从 npm 包进化到独立安装的应用，说明 Anthropic 对它的定位已经变了——不再是"一个 CLI 工具"，而是一个 **完整的 AI 编程伴侣** 。新的安装方式带来了自动更新、更好的跨平台支持、桌面 GUI 等新能力，体验确实升级了不少。

如果你之前用的是 npm 方式，赶紧切换到新版吧。如果你刚开始接触 Claude Code，直接用官方推荐的安装命令，一步到位。

![](https://pica.zhimg.com/v2-11ac8aa98a157df0f285bf1d12b160fc_1440w.jpg)

**小胡** ：关注「运维也AI」，后续还会出更多 Claude Code 实战教程。下期预告——Claude Code 在运维场景下的实际用法，从写脚本到排查服务器故障，AI 怎么帮你提效。

粉丝福利

小胡给大家准备了 **运维人专属资料包** ，关注即可免费领取：

✅ Claude Code 完整技能清单

✅ ️ 运维人必备的 AI 工具配置模板

✅ OpenClaw 从入门到实战教程

**领取方式：**

1扫描下方二维码，关注公众号「 **运维也AI** 」

2后台回复关键词「 **粉丝福利** 」

3即可免费领取全部资料

http://weixin.qq.com/r/mp/cCPH3yDE6n2VrWS893Zi (二维码自动识别)

**小胡** ：资料会持续更新，关注后第一时间获取最新 AI 运维干货！

**小胡** ：关注后还可以发送「 **下载求助** 」，帮你找各种软件、工具、教程的资源！

有用就点个 **在看** ，有问题 **留言** 。觉得这篇文章对你有帮助，也欢迎 **转发** 给需要的朋友。

发布于 2026-05-07 15:41・北京[有了豆包学习搭子，作文、翻译、讲解，学习轻松无压力](http://www.doubao.com/download/desktop?ug_apk_token=LQqwd&ad_platform_id=zhihu_feed_lead&ug_callback_url=https%3A%2F%2Fsugar.zhihu.com%2Fplutus_adreaper_callback%3Fsi%3D024bdb29-0221-4d40-878d-2a1fe984da10%26os%3D3%26zid%3D1629%26zaid%3D3756217%26zcid%3D3751285%26cid%3D3751285%26event%3D__EVENTTYPE__%26value%3D__EVENTVALUE__%26ts%3D__TIMESTAMP__%26cts%3D__TS__%26mh%3D__MEMBERHASHID__%26adv%3D784532%26ocg%3D0%26cp%3D0%26ocs%3D0%26aic%3D0%26atp%3D0%26ct%3D0%26ed%3DGiBNJgVzfCMmUW9XFyEvRA8xBGxJICwkOhh0FlwxKw1Gdx87VSAsMi9Cb0oDdj1dByRedwhlKy0iVm9XFyU5WQ94CH0Kcmt5eRFmUQVheANYdx8lViYzJHMVdAtEbXyrfWDZIhpJ6w%3D%3D&cb=https%3A%2F%2Fsugar.zhihu.com%2Fplutus_adreaper_callback%3Fsi%3D024bdb29-0221-4d40-878d-2a1fe984da10%26os%3D3%26zid%3D1629%26zaid%3D3756217%26zcid%3D3751285%26cid%3D3751285%26event%3D__EVENTTYPE__%26value%3D__EVENTVALUE__%26ts%3D__TIMESTAMP__%26cts%3D__TS__%26mh%3D__MEMBERHASHID__%26adv%3D784532%26ocg%3D0%26cp%3D0%26ocs%3D0%26aic%3D0%26atp%3D0%26ct%3D0%26ed%3DGiBNJgVzfCMmUW9XFyEvRA8xBGxJICwkOhh0FlwxKw1Gdx87VSAsMi9Cb0oDdj1dByRedwhlKy0iVm9XFyU5WQ94CH0Kcmt5eRFmUQVheANYdx8lViYzJHMVdAtEbXyrfWDZIhpJ6w%3D%3D&ug_semver=v1.0.0&spu=biz%3D0%26ci%3D3751285%26si%3Dd93b995d-95c5-484b-b8d6-49832b372f81%26ts%3D1782725921%26zid%3D1629)

[

学生党学习搭子-豆包AI！不仅可以输出中英文作文、英语翻译、作文修改润色，还能有海量题目讲解

](http://www.doubao.com/download/desktop?ug_apk_token=LQqwd&ad_platform_id=zhihu_feed_lead&ug_callback_url=https%3A%2F%2Fsugar.zhihu.com%2Fplutus_adreaper_callback%3Fsi%3D024bdb29-0221-4d40-878d-2a1fe984da10%26os%3D3%26zid%3D1629%26zaid%3D3756217%26zcid%3D3751285%26cid%3D3751285%26event%3D__EVENTTYPE__%26value%3D__EVENTVALUE__%26ts%3D__TIMESTAMP__%26cts%3D__TS__%26mh%3D__MEMBERHASHID__%26adv%3D784532%26ocg%3D0%26cp%3D0%26ocs%3D0%26aic%3D0%26atp%3D0%26ct%3D0%26ed%3DGiBNJgVzfCMmUW9XFyEvRA8xBGxJICwkOhh0FlwxKw1Gdx87VSAsMi9Cb0oDdj1dByRedwhlKy0iVm9XFyU5WQ94CH0Kcmt5eRFmUQVheANYdx8lViYzJHMVdAtEbXyrfWDZIhpJ6w%3D%3D&cb=https%3A%2F%2Fsugar.zhihu.com%2Fplutus_adreaper_callback%3Fsi%3D024bdb29-0221-4d40-878d-2a1fe984da10%26os%3D3%26zid%3D1629%26zaid%3D3756217%26zcid%3D3751285%26cid%3D3751285%26event%3D__EVENTTYPE__%26value%3D__EVENTVALUE__%26ts%3D__TIMESTAMP__%26cts%3D__TS__%26mh%3D__MEMBERHASHID__%26adv%3D784532%26ocg%3D0%26cp%3D0%26ocs%3D0%26aic%3D0%26atp%3D0%26ct%3D0%26ed%3DGiBNJgVzfCMmUW9XFyEvRA8xBGxJICwkOhh0FlwxKw1Gdx87VSAsMi9Cb0oDdj1dByRedwhlKy0iVm9XFyU5WQ94CH0Kcmt5eRFmUQVheANYdx8lViYzJHMVdAtEbXyrfWDZIhpJ6w%3D%3D&ug_semver=v1.0.0&spu=biz%3D0%26ci%3D3751285%26si%3Dd93b995d-95c5-484b-b8d6-49832b372f81%26ts%3D1782725921%26zid%3D1629)

赞同 1