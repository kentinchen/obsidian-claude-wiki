---
title: "手把手教你安装 Hermes Agent，接入OpenRouter 免费模型，IM消息集成 - 苏米客"
source: "https://www.xmsumi.com/detail/2945"
author:
published:
created: 2026-07-02
description: "Hermes Agent 简介Hermes Agent 是 Nous Research 推出的开源 AI Agent 框架，被视为新一代的 OpenClaw。它支持建立自学习循环（通过使用不断积累技能）、接入超过 15 家模型提供商，并实…"
tags:
  - "clippings"
---
## Hermes Agent 简介

Hermes Agent 是 Nous Research 推出的开源 AI Agent 框架，被视为新一代的 OpenClaw。它支持建立自学习循环（通过使用不断积累技能）、接入超过 15 家模型提供商，并实现跨平台消息集成（Telegram、Discord、Slack、WhatsApp）。

软件

**苏米注** ：回想一下，不久前有多少人在闲鱼上享受了 OpenClaw 的红利，现在你也可以通过 Hermes 获得同样的机会。

## 一键安装（推荐）

### Mac/Linux 安装

在终端输入以下命令并回车：

<iframe width="788" height="280" frameborder="0" allow="attribution-reporting; run-ad-auction" src="https://googleads.g.doubleclick.net/pagead/ads?client=ca-pub-0165002410112171&amp;output=html&amp;h=280&amp;num_ads=1&amp;adk=1624051043&amp;adf=129468725&amp;abgtt=6&amp;w=788&amp;fwrn=4&amp;fwrnh=100&amp;lmt=1783003874&amp;rafmt=1&amp;armr=3&amp;sem=mc&amp;pwprc=1331672177&amp;ad_type=text_image&amp;format=788x280&amp;url=https%3A%2F%2Fwww.xmsumi.com%2Fdetail%2F2945&amp;fwr=0&amp;pra=3&amp;rh=197&amp;rw=788&amp;rpe=1&amp;resp_fmts=3&amp;asro=0&amp;aimartd=4&amp;aieuf=1&amp;aicrs=1&amp;fa=27&amp;uach=WyJXaW5kb3dzIiwiMTkuMC4wIiwieDg2IiwiIiwiMTQ3LjAuMzkxMi42MCIsbnVsbCwwLG51bGwsIjY0IixbWyJNaWNyb3NvZnQgRWRnZSIsIjE0Ny4wLjM5MTIuNjAiXSxbIk5vdC5BL0JyYW5kIiwiOC4wLjAuMCJdLFsiQ2hyb21pdW0iLCIxNDcuMC43NzI3LjU2Il1dLDBd&amp;dt=1783003874672&amp;bpp=2&amp;bdt=3170&amp;idt=-M&amp;shv=r20260701&amp;mjsv=m202607010101&amp;ptt=9&amp;saldr=aa&amp;abxe=1&amp;cookie_enabled=1&amp;eoidce=1&amp;prev_fmts=0x0%2C1200x280&amp;nras=3&amp;correlator=2084598702418&amp;frm=20&amp;pv=1&amp;u_tz=480&amp;u_his=1&amp;u_h=1080&amp;u_w=1920&amp;u_ah=1032&amp;u_aw=1920&amp;u_cd=32&amp;u_sd=1&amp;dmc=32&amp;adx=381&amp;ady=924&amp;biw=1897&amp;bih=914&amp;scr_x=0&amp;scr_y=0&amp;eid=42532523%2C95395662%2C31099532&amp;oid=2&amp;pvsid=3805794066289450&amp;tmod=1578985471&amp;uas=0&amp;nvt=1&amp;ref=https%3A%2F%2Fcn.bing.com%2F&amp;fc=1408&amp;brdim=0%2C0%2C0%2C0%2C1920%2C0%2C1920%2C1032%2C1912%2C914&amp;vis=1&amp;rsz=%7C%7Cs%7C&amp;abl=NS&amp;fu=128&amp;bc=31&amp;plas=307x721_l%7C307x721_r&amp;bz=1&amp;ifi=3&amp;uci=a!3&amp;btvi=1&amp;fsb=1&amp;dtd=23" title="Advertisement" aria-label="Advertisement"></iframe>

```
curl -fsSL https://raw.githubusercontent.com/NousResearch/hermes-agent/main/scripts/install.sh | bash
```

### Windows 安装

在 PowerShell 中输入：

```
irm https://raw.githubusercontent.com/NousResearch/hermes-agent/main/scripts/install.ps1 | iex
```

[脚本](#) 会自动检测并安装 Python、Node.js、Git、ripgrep 等所有依赖项，只需耐心等待即可。

![安装脚本运行中](https://xmsumi.com/storage/picture/20260414/13385349cd5d225392149da170b05697.jpeg)

## 配置向导

<iframe width="788" height="280" frameborder="0" allow="attribution-reporting; run-ad-auction" src="https://googleads.g.doubleclick.net/pagead/ads?client=ca-pub-0165002410112171&amp;output=html&amp;h=280&amp;num_ads=1&amp;adk=1624051043&amp;adf=2592396009&amp;abgtt=6&amp;w=788&amp;fwrn=4&amp;fwrnh=100&amp;lmt=1783003874&amp;rafmt=1&amp;armr=3&amp;sem=mc&amp;pwprc=1331672177&amp;ad_type=text_image&amp;format=788x280&amp;url=https%3A%2F%2Fwww.xmsumi.com%2Fdetail%2F2945&amp;fwr=0&amp;pra=3&amp;rh=197&amp;rw=788&amp;rpe=1&amp;resp_fmts=3&amp;asro=0&amp;aimartd=4&amp;aieuf=1&amp;aicrs=1&amp;fa=27&amp;uach=WyJXaW5kb3dzIiwiMTkuMC4wIiwieDg2IiwiIiwiMTQ3LjAuMzkxMi42MCIsbnVsbCwwLG51bGwsIjY0IixbWyJNaWNyb3NvZnQgRWRnZSIsIjE0Ny4wLjM5MTIuNjAiXSxbIk5vdC5BL0JyYW5kIiwiOC4wLjAuMCJdLFsiQ2hyb21pdW0iLCIxNDcuMC43NzI3LjU2Il1dLDBd&amp;dt=1783003874672&amp;bpp=1&amp;bdt=3169&amp;idt=-M&amp;shv=r20260701&amp;mjsv=m202607010101&amp;ptt=9&amp;saldr=aa&amp;abxe=1&amp;cookie_enabled=1&amp;eoidce=1&amp;prev_fmts=0x0%2C1200x280%2C788x280%2C788x280&amp;nras=5&amp;correlator=2084598702418&amp;frm=20&amp;pv=1&amp;u_tz=480&amp;u_his=1&amp;u_h=1080&amp;u_w=1920&amp;u_ah=1032&amp;u_aw=1920&amp;u_cd=32&amp;u_sd=1&amp;dmc=32&amp;adx=381&amp;ady=2287&amp;biw=1897&amp;bih=914&amp;scr_x=0&amp;scr_y=0&amp;eid=42532523%2C95395662%2C31099532&amp;oid=2&amp;pvsid=3805794066289450&amp;tmod=1578985471&amp;uas=0&amp;nvt=1&amp;ref=https%3A%2F%2Fcn.bing.com%2F&amp;fc=1408&amp;brdim=0%2C0%2C0%2C0%2C1920%2C0%2C1920%2C1032%2C1912%2C914&amp;vis=1&amp;rsz=%7C%7Cs%7C&amp;abl=NS&amp;fu=128&amp;bc=31&amp;plas=307x721_l%7C307x721_r&amp;bz=1&amp;ifi=5&amp;uci=a!5&amp;btvi=3&amp;fsb=1&amp;dtd=28" title="Advertisement" aria-label="Advertisement"></iframe>

安装完成后，配置向导将自动启动。选择第一项 **Quick setup** （推荐）：

免费软件与共享软件

![选择 Quick setup](https://xmsumi.com/storage/picture/20260414/1338551eb2d62e84419f2c11ab200258.jpeg)

### 配置 Inference Provider

接下来进入 Inference Provider 配置，系统会提示输入 OpenRouter API Key。请粘贴提前申请好的 Key 后回车：

![填写 OpenRouter API Key](https://xmsumi.com/storage/picture/20260414/133855f13bc9d06f510eafb142303032.jpeg)

然后选择默认模型。列表中有很多免费模型，这里选择 `nvidia/nemotron-3-super-120b-a12b:free` ，这个模型完全免费且效果不错：

![选择默认模型](https://xmsumi.com/storage/picture/20260414/133858af7662a84cc0f25c0ac2201156.jpeg)

### 配置消息平台

接下来配置消息平台，选择 **Set up messaging now** ：

<iframe width="788" height="280" frameborder="0" allow="attribution-reporting; run-ad-auction" src="https://googleads.g.doubleclick.net/pagead/ads?client=ca-pub-0165002410112171&amp;output=html&amp;h=280&amp;num_ads=1&amp;adk=1624051043&amp;adf=426014504&amp;abgtt=6&amp;w=788&amp;fwrn=4&amp;fwrnh=100&amp;lmt=1783003874&amp;rafmt=1&amp;armr=3&amp;sem=mc&amp;pwprc=1331672177&amp;ad_type=text_image&amp;format=788x280&amp;url=https%3A%2F%2Fwww.xmsumi.com%2Fdetail%2F2945&amp;fwr=0&amp;pra=3&amp;rh=197&amp;rw=788&amp;rpe=1&amp;resp_fmts=3&amp;asro=0&amp;aimartd=4&amp;aieuf=1&amp;aicrs=1&amp;fa=27&amp;uach=WyJXaW5kb3dzIiwiMTkuMC4wIiwieDg2IiwiIiwiMTQ3LjAuMzkxMi42MCIsbnVsbCwwLG51bGwsIjY0IixbWyJNaWNyb3NvZnQgRWRnZSIsIjE0Ny4wLjM5MTIuNjAiXSxbIk5vdC5BL0JyYW5kIiwiOC4wLjAuMCJdLFsiQ2hyb21pdW0iLCIxNDcuMC43NzI3LjU2Il1dLDBd&amp;dt=1783003874672&amp;bpp=2&amp;bdt=3169&amp;idt=2&amp;shv=r20260701&amp;mjsv=m202607010101&amp;ptt=9&amp;saldr=aa&amp;abxe=1&amp;cookie_enabled=1&amp;eoidce=1&amp;prev_fmts=0x0%2C1200x280%2C788x280%2C788x280%2C788x280%2C788x280&amp;nras=7&amp;correlator=2084598702418&amp;frm=20&amp;pv=1&amp;u_tz=480&amp;u_his=1&amp;u_h=1080&amp;u_w=1920&amp;u_ah=1032&amp;u_aw=1920&amp;u_cd=32&amp;u_sd=1&amp;dmc=32&amp;adx=381&amp;ady=3499&amp;biw=1897&amp;bih=914&amp;scr_x=0&amp;scr_y=0&amp;eid=42532523%2C95395662%2C31099532&amp;oid=2&amp;pvsid=3805794066289450&amp;tmod=1578985471&amp;uas=0&amp;nvt=1&amp;ref=https%3A%2F%2Fcn.bing.com%2F&amp;fc=1408&amp;brdim=0%2C0%2C0%2C0%2C1920%2C0%2C1920%2C1032%2C1912%2C914&amp;vis=1&amp;rsz=%7C%7Cs%7C&amp;abl=NS&amp;fu=128&amp;bc=31&amp;plas=307x721_l%7C307x721_r&amp;bz=1&amp;ifi=7&amp;uci=a!7&amp;btvi=5&amp;fsb=1&amp;dtd=34" title="Advertisement" aria-label="Advertisement"></iframe>

![配置消息平台](https://xmsumi.com/storage/picture/20260414/133859bd23deb0fabde53f0817101466.jpeg)

选择 Telegram，粘贴 Bot Token，然后回车确认：

短信和即时消息

![填写 Telegram Token](https://xmsumi.com/storage/picture/20260414/133900ff6fe2f3b46e4dc4dcc8406313.jpeg)

然后设置 Allowed user IDs（填写你自己的 Telegram 数字 ID，不填则任何人都可以使用你的 Bot），Home Channel ID 可以留空后续再配置。

最后，系统会询问是否将 Hermes 安装为系统服务（launchd），选择 Y 可以实现开机自启、后台常驻：

<iframe width="788" height="280" frameborder="0" allow="attribution-reporting; run-ad-auction" src="https://googleads.g.doubleclick.net/pagead/ads?client=ca-pub-0165002410112171&amp;output=html&amp;h=280&amp;num_ads=1&amp;adk=1624051043&amp;adf=402190399&amp;abgtt=6&amp;w=788&amp;fwrn=4&amp;fwrnh=100&amp;lmt=1783003875&amp;rafmt=1&amp;armr=3&amp;sem=mc&amp;pwprc=1331672177&amp;ad_type=text_image&amp;format=788x280&amp;url=https%3A%2F%2Fwww.xmsumi.com%2Fdetail%2F2945&amp;fwr=0&amp;pra=3&amp;rh=197&amp;rw=788&amp;rpe=1&amp;resp_fmts=3&amp;asro=0&amp;aimartd=4&amp;aieuf=1&amp;aicrs=1&amp;fa=27&amp;uach=WyJXaW5kb3dzIiwiMTkuMC4wIiwieDg2IiwiIiwiMTQ3LjAuMzkxMi42MCIsbnVsbCwwLG51bGwsIjY0IixbWyJNaWNyb3NvZnQgRWRnZSIsIjE0Ny4wLjM5MTIuNjAiXSxbIk5vdC5BL0JyYW5kIiwiOC4wLjAuMCJdLFsiQ2hyb21pdW0iLCIxNDcuMC43NzI3LjU2Il1dLDBd&amp;dt=1783003874679&amp;bpp=2&amp;bdt=3176&amp;idt=2&amp;shv=r20260701&amp;mjsv=m202607010101&amp;ptt=9&amp;saldr=aa&amp;abxe=1&amp;cookie=ID%3D2909f03fc0b2f8cd%3AT%3D1783003874%3ART%3D1783003874%3AS%3DALNI_MZF5j0vCqpEuRryIY0L7W3ocd1V7w&amp;gpic=UID%3D0000140e8c84275a%3AT%3D1783003874%3ART%3D1783003874%3AS%3DALNI_MYHgTKbchtHjBDkNlb5_hZKRHITRA&amp;eo_id_str=ID%3D842e80595e3ef4cd%3AT%3D1783003874%3ART%3D1783003874%3AS%3DAA-AfjZxsrOzUebtvTEuMIQlAzfl&amp;prev_fmts=0x0%2C1200x280%2C788x280%2C788x280%2C788x280%2C788x280%2C788x280%2C1005x124&amp;nras=9&amp;correlator=2084598702418&amp;frm=20&amp;pv=1&amp;u_tz=480&amp;u_his=1&amp;u_h=1080&amp;u_w=1920&amp;u_ah=1032&amp;u_aw=1920&amp;u_cd=32&amp;u_sd=1&amp;dmc=32&amp;adx=381&amp;ady=3650&amp;biw=1897&amp;bih=914&amp;scr_x=0&amp;scr_y=0&amp;eid=42532523%2C95395662%2C31099532&amp;oid=2&amp;pvsid=3805794066289450&amp;tmod=1578985471&amp;uas=0&amp;nvt=1&amp;ref=https%3A%2F%2Fcn.bing.com%2F&amp;fc=1408&amp;brdim=0%2C0%2C0%2C0%2C1920%2C0%2C1920%2C1032%2C1912%2C914&amp;vis=1&amp;rsz=%7C%7Cs%7C&amp;abl=NS&amp;fu=128&amp;bc=31&amp;plas=307x721_l%7C307x721_r&amp;bz=1&amp;ifi=8&amp;uci=a!8&amp;btvi=7&amp;fsb=1&amp;dtd=533" title="Advertisement" aria-label="Advertisement"></iframe>

![完成 Telegram 配置](https://xmsumi.com/storage/picture/20260414/133902ab2ad5ee122cdf3537b2602381.jpeg)

### 获取 Telegram Bot Token

- 在 Telegram 中搜索 @BotFather
- 发送 `/newbot` 命令，并按提示为你的 Bot 取名（用户名必须以 bot 结尾）
- 获取 Bot Token，格式类似于 `123456789:AAxxxxxxxx`

**查询自己的 Telegram 数字 ID** ：在 Telegram 中给 @userinfobot 发任意消息，它会回复你的 ID。

## 启动测试

配置完成后，运行 `hermes` 启动，欢迎页将显示，说明一切正常：

![Hermes 启动成功](https://xmsumi.com/storage/picture/20260414/133904d63d331e749b597fff90b02625.jpeg)

打开 Telegram，找到你的 Bot 并发送消息进行测试：

![Telegram 测试成功](https://xmsumi.com/storage/picture/20260414/1339067ad37bbc94e0363b057dc09012.jpeg)

## 手动安装（可选）

手动挡和自动挡的用法完全相同，适合那些想要修改源码或使用固定版本的用户。

电子邮件与即时消息

### 克隆项目

```
git clone https://github.com/nousresearch/hermes-agent.git
cd hermes-agent
```

### 安装依赖

```
pip install -r requirements.txt
```

### 运行

```
python -m hermes
```

## 常用命令

| 命令 | 说明 |
| --- | --- |
| `hermes` | 启动交互式对话 |
| `hermes model` | 选择模型提供商和模型 |
| `hermes tools` | 配置启用哪些工具 |
| `hermes config set` | 设置单个配置项 |
| `hermes gateway` | 启动消息网关（Telegram、Discord 等） |
| `hermes setup` | 重新运行完整配置向导 |
| `hermes claw migrate` | 从 OpenClaw 迁移配置 |
| `hermes update` | 更新到最新版本 |
| `hermes doctor` | 诊断问题 |

## 常见问题

### Q: 提示 API call failed after 3 retries: HTTP 400: No models provided

这是配置文件编码问题（Windows 上常见）。让 Claude 帮你修复，告诉他报错信息，它会自动定位到配置文件中的 `open()` 调用并加上 `encoding="utf-8"` 参数。

![Windows 编码报错修复](https://xmsumi.com/storage/picture/20260414/133908bbcb526dad53e299e982005228.jpeg)

### Q: Telegram Bot 没有响应

没有设置 UserId，手动设置或者让 Claude 设置一下即可。

机器学习与人工智能

## 配置 OpenRouter（推荐）

Hermes 支持多种模型提供商，推荐先配置 OpenRouter——它提供大量免费模型，白嫖入门最方便。

1. 打开 OpenRouter，点击 Create Key，名称填 hermes，然后直接点击 Create
2. Key 只显示一次，立即复制并保存好

> **项目地址** ： [https://github.com/nousresearch/hermes-agent](https://github.com/nousresearch/hermes-agent)

## 总结

Hermes 还有许多玩法尚未展开：定时任务、自建 Slack……后续会继续探索。

声明：本站原创文章文字版权归本站所有，转载务必注明作者和出处；本站转载文章仅仅代表原作者观点，不代表本站立场，图文版权归原作者所有。如有侵权，请联系我们删除。