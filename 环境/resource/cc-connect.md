---
title: "3 分钟上手 cc-connect：把 Claude Code 接入微信和飞书"
source: "https://juejin.cn/post/7669024144831234054"
author:
  - "[[予枫]]"
published: 2026-08-02
created: 2026-10-12
description: "最近有同学问我： 最开始我想到的是自己写一个机器人，通过 WebSocket 把聊天消息转发给本地的 Claude Code。但深入了解后，我发现已经有一个相对完整的开源方案——cc-connect。> 不用守在电脑前，通过微信、飞书或钉钉，随时远程指挥 Claude Code、Codex、Gemini CLI 等本地"
tags:
  - "clippings"
---
> 不用守在电脑前，通过微信、飞书或钉钉，随时远程指挥 Claude Code、Codex、Gemini CLI 等本地 AI Agent 干活。

最近有同学问我：

> 能不能在企业微信或者飞书里使用 Claude Code？

最开始我想到的是自己写一个机器人，通过 WebSocket 把聊天消息转发给本地的 Claude Code。但深入了解后，我发现已经有一个相对完整的开源方案—— **cc-connect** 。

它不仅支持 Claude Code，还可以接入 Codex、Gemini CLI、Cursor Agent 等多种 AI 编程工具；聊天平台方面，则覆盖微信、飞书、钉钉、Telegram、Slack、Discord 等常用工具。

本文将介绍：

- cc-connect 是什么；
- 它解决了哪些问题；
- 如何完成本地安装；
- 如何接入飞书和微信；
- 如何设置工作目录、权限和访问控制；
- 如何配置后台运行与开机自启；
- 日常使用中有哪些常用命令。

如果你希望把本地 AI Agent 变成一个随时可调用的“远程开发助手”，可以按照本文一步一步完成配置。

---

## 一、cc-connect 是什么？

cc-connect 是一个连接 **AI Agent** 和 **即时通讯工具** 的桥接器，也可以理解为一个通信中枢。

它负责把聊天软件中的消息转发给运行在本地电脑上的 AI Agent，再把 Agent 的执行结果发送回聊天软件。 ![在这里插入图片描述](https://p3-xtjj-sign.byteimg.com/tos-cn-i-73owjymdk6/b579b4dcba284919bb0ad383653eeca7~tplv-73owjymdk6-jj-mark-v1:0:0:0:0:5o6Y6YeR5oqA5pyv56S-5Yy6IEAg5LqI5p6r:q75.awebp?rk3s=f64ab15b&x-expires=1792302609&x-signature=Xbd2gVWXH7BLeM5tEsG4N0HssQI%3D)

项目地址：

[github.com/chenhg5/cc-…](https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2Fchenhg5%2Fcc-connect "https://github.com/chenhg5/cc-connect")

整体链路非常简单：

<svg aria-roledescription="flowchart-v2" role="graphics-document document" viewBox="-8 -8 278.21875 312" style="max-width: 278.21875px;" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns="http://www.w3.org/2000/svg" width="100%" id="bytemd-mermaid-1791814696349-0"><g><marker orient="auto" markerHeight="12" markerWidth="12" markerUnits="userSpaceOnUse" refY="5" refX="10" viewBox="0 0 12 20" id="flowchart-pointEnd"><path style="stroke-width: 1; stroke-dasharray: 1, 0;" d="M 0 0 L 10 5 L 0 10 z"></path></marker><marker orient="auto" markerHeight="12" markerWidth="12" markerUnits="userSpaceOnUse" refY="5" refX="0" viewBox="0 0 10 10" id="flowchart-pointStart"><path style="stroke-width: 1; stroke-dasharray: 1, 0;" d="M 0 5 L 10 10 L 10 0 z"></path></marker><marker orient="auto" markerHeight="11" markerWidth="11" markerUnits="userSpaceOnUse" refY="5" refX="11" viewBox="0 0 10 10" id="flowchart-circleEnd"><circle style="stroke-width: 1; stroke-dasharray: 1, 0;" r="5" cy="5" cx="5"></circle></marker><marker orient="auto" markerHeight="11" markerWidth="11" markerUnits="userSpaceOnUse" refY="5" refX="-1" viewBox="0 0 10 10" id="flowchart-circleStart"><circle style="stroke-width: 1; stroke-dasharray: 1, 0;" r="5" cy="5" cx="5"></circle></marker><marker orient="auto" markerHeight="11" markerWidth="11" markerUnits="userSpaceOnUse" refY="5.2" refX="12" viewBox="0 0 11 11" id="flowchart-crossEnd"><path style="stroke-width: 2; stroke-dasharray: 1, 0;" d="M 1,1 l 9,9 M 10,1 l -9,9"></path></marker><marker orient="auto" markerHeight="11" markerWidth="11" markerUnits="userSpaceOnUse" refY="5.2" refX="-1" viewBox="0 0 11 11" id="flowchart-crossStart"><path style="stroke-width: 2; stroke-dasharray: 1, 0;" d="M 1,1 l 9,9 M 10,1 l -9,9"></path></marker><g><g></g><g><path marker-end="url(#flowchart-pointEnd)" style="fill:none;" id="L-A-B-0" d="M126.727,39L125.791,43.167C124.855,47.333,122.982,55.667,123.038,64C123.094,72.333,125.078,80.667,126.07,84.833L127.062,89" stroke="currentColor"></path><path marker-end="url(#flowchart-pointEnd)" style="fill:none;" id="L-B-C-0" d="M127.062,123L126.07,127.167C125.078,131.333,123.094,139.667,123.094,148C123.094,156.333,125.078,164.667,126.07,168.833L127.062,173" stroke="currentColor"></path><path marker-end="url(#flowchart-pointEnd)" style="fill:none;" id="L-C-D-0" d="M127.062,207L126.07,211.167C125.078,215.333,123.094,223.667,123.038,232C122.982,240.333,124.855,248.667,125.791,252.833L126.727,257" stroke="currentColor"></path><path marker-end="url(#flowchart-pointEnd)" style="fill:none;" id="L-D-C-0" d="M135.491,257L136.428,252.833C137.364,248.667,139.237,240.333,139.181,232C139.125,223.667,137.141,215.333,136.149,211.167L135.157,207" stroke="currentColor"></path><path marker-end="url(#flowchart-pointEnd)" style="fill:none;" id="L-C-B-0" d="M135.157,173L136.149,168.833C137.141,164.667,139.125,156.333,139.125,148C139.125,139.667,137.141,131.333,136.149,127.167L135.157,123" stroke="currentColor"></path><path marker-end="url(#flowchart-pointEnd)" style="fill:none;" id="L-B-A-0" d="M135.157,89L136.149,84.833C137.141,80.667,139.125,72.333,139.181,64C139.237,55.667,137.364,47.333,136.428,43.167L135.491,39" stroke="currentColor"></path></g><g><g><g transform="translate(0, 0)"></g></g><g><g transform="translate(0, 0)"></g></g><g><g transform="translate(0, 0)"></g></g><g><g transform="translate(0, 0)"></g></g><g><g transform="translate(0, 0)"></g></g><g><g transform="translate(0, 0)"></g></g></g><g><g transform="translate(131.109375, 19.5)" id="flowchart-A-24"><rect height="39" width="230.5" y="-19.5" x="-115.25" ry="0" rx="0" style="" fill="none" stroke="currentColor"></rect><g transform="translate(-107.75, -12)" style=""><foreignObject height="24" width="215.5"><div style="display: inline-block; white-space: nowrap;" xmlns="http://www.w3.org/1999/xhtml">微信 / 飞书 / 钉钉 / Telegram</div></foreignObject></g></g><g transform="translate(131.109375, 106)" id="flowchart-B-25"><rect height="34" width="93.703125" y="-17" x="-46.8515625" ry="0" rx="0" style="" fill="none" stroke="currentColor"></rect><g transform="translate(-39.3515625, -9.5)" style=""><foreignObject height="19" width="78.703125"><div style="display: inline-block; white-space: nowrap;" xmlns="http://www.w3.org/1999/xhtml">cc-connect</div></foreignObject></g></g><g transform="translate(131.109375, 190)" id="flowchart-C-27"><rect height="34" width="262.21875" y="-17" x="-131.109375" ry="0" rx="0" style="" fill="none" stroke="currentColor"></rect><g transform="translate(-123.609375, -9.5)" style=""><foreignObject height="19" width="247.21875"><div style="display: inline-block; white-space: nowrap;" xmlns="http://www.w3.org/1999/xhtml">Claude Code / Codex / Gemini CLI</div></foreignObject></g></g><g transform="translate(131.109375, 276.5)" id="flowchart-D-29"><rect height="39" width="191" y="-19.5" x="-95.5" ry="0" rx="0" style="" fill="none" stroke="currentColor"></rect><g transform="translate(-88, -12)" style=""><foreignObject height="24" width="176"><div style="display: inline-block; white-space: nowrap;" xmlns="http://www.w3.org/1999/xhtml">本地代码仓库与操作系统</div></foreignObject></g></g></g></g></g></svg>

换句话说，你可以把原本只能在终端里使用的 Claude Code，变成微信或飞书里的聊天机器人。

例如，你在手机上发送：

```
代码解读复制代码检查一下今天提交的代码，看看有没有明显的安全问题。
```

家里或者办公室电脑上的 Claude Code 可以自动：

1. 进入指定项目目录；
2. 执行 `git diff` ；
3. 阅读修改过的代码；
4. 分析潜在问题；
5. 把检查结果返回到微信或飞书。

整个过程中，你不需要远程连接电脑，也不需要一直守在终端前。

---

## 二、cc-connect 解决了什么问题？

Claude Code、Codex、Gemini CLI 等 AI 编程工具已经非常强大，但它们通常存在几个使用限制：

- 主要在终端中运行；
- 必须连接开发机器；
- 离开电脑后不方便继续操作；
- 长任务执行过程中不容易随时补充要求；
- 多台设备之间缺少统一的交互入口。

cc-connect 的核心价值，就是把 AI Agent 的操作入口从终端扩展到手机聊天软件。

### 场景一：远程检查代码

下班以后，你突然想到今天提交的代码可能存在问题，可以直接在微信中发送：

```
代码解读复制代码检查今天的代码改动，重点关注 SQL 注入、权限校验和敏感信息泄露。
```

Claude Code 可以在本地仓库中执行：

```bash
代码解读复制代码git diff
git status
```

然后阅读相关文件并返回分析报告。

### 场景二：让 AI 持续执行长任务

你可以在路上发送：

```
代码解读复制代码分析这个仓库的整体架构，整理主要模块、调用关系和潜在技术债，生成一份 Markdown 报告。
```

Agent 可以继续在电脑上完成：

- 搜索代码；
- 阅读项目文档；
- 分析目录结构；
- 执行必要的命令；
- 生成分析报告。

任务完成后，结果会直接返回聊天软件。

### 场景三：远程排查故障

在飞书中发送：

```
代码解读复制代码帮我检查最近一次 CI 为什么失败，不要修改代码，先给出原因和解决方案。
```

Agent 可以读取日志、检查构建脚本和依赖配置，再把排查结果返回。

### 场景四：远程推进写作和调研任务

cc-connect 不只能用于写代码。

只要 Agent 能完成的工作，都可以通过聊天软件发起，例如：

- 整理技术方案；
- 阅读和总结资料；
- 生成博客初稿；
- 分析数据文件；
- 更新项目文档；
- 执行自动化脚本；
- 汇总每日工作进度。

---

## 三、cc-connect 有哪些特点？

### 1\. 支持多种 AI Agent

根据项目提供的能力，cc-connect 可以连接多种主流 AI 编程工具，例如：

| AI Agent | 支持情况 |
| --- | --- |
| Claude Code | ✅ |
| Codex | ✅ |
| Gemini CLI | ✅ |
| Cursor Agent | ✅ |
| Kimi CLI | ✅ |
| OpenCode | ✅ |
| Qoder CLI | ✅ |
| Pi Agent | ✅ |
| Devin（ACP） | ✅ |
| 其他 ACP Agent | ✅ |

这意味着你不必被限制在某一个模型或某一个编程工具中。

你甚至可以给不同 Agent 分配不同职责：

```
代码解读复制代码@Claude 分析代码逻辑
@Gemini 评审技术方案
@Codex 给出修复建议
```

### 2\. 支持多种聊天平台

cc-connect 支持的聊天平台包括：

- 微信；
- 飞书；
- 钉钉；
- 企业微信；
- Telegram；
- Slack；
- Discord；
- LINE；
- QQ；
- QQ 官方机器人；
- 微博私信；
- WPS 协作。

具体支持范围和接入方式可能随项目版本变化，建议以项目最新文档为准。

### 3\. 多数场景不要求公网 IP

很多传统机器人方案需要准备：

- 公网服务器；
- HTTPS 证书；
- Webhook 地址；
- 独立域名；
- 反向代理。

cc-connect 在部分平台中可以使用 WebSocket、长轮询或 Socket Mode 建立连接，因此可以直接运行在：

- 家里的 Mac Mini；
- 办公室电脑；
- Linux 主机；
- NAS；
- 常驻在线的开发机。

对于个人开发者来说，这可以明显降低部署门槛。

### 4\. 支持多会话管理

cc-connect 提供了多会话管理能力。

你可以为不同任务创建独立会话：

```
代码解读复制代码/new 修复登录接口超时问题
```

再通过命令查看或切换会话：

```
代码解读复制代码/list
/switch 2
/current
/history 10
```

比较推荐的习惯是： **一个任务对应一个会话** 。

不要使用“临时”“测试”这种难以识别的名字，而是直接描述任务，例如：

```
代码解读复制代码/new 分析订单服务内存泄漏
/new 重构用户权限模块
/new 整理本周技术周报
```

### 5\. 支持切换工作目录

你可以通过聊天命令切换 Agent 当前操作的目录：

```
代码解读复制代码/dir ~/workspace/project-a
```

也可以查看当前目录：

```
代码解读复制代码/dir
```

恢复到配置文件中的默认目录：

```
代码解读复制代码/dir reset
```

### 6\. 支持定时任务

例如，你可以让 Agent：

- 每天早上汇总 GitHub Trending；
- 每晚整理当天提交记录；
- 每周生成项目进展报告；
- 定期检查服务日志；
- 定时执行代码质量检查。

本质上，是把聊天指令、AI Agent 和系统任务调度组合在了一起。

### 7\. 支持图片、文件和语音

部分平台可以向 Agent 发送：

- 图片；
- 截图；
- 文档；
- 代码文件；
- 语音消息。

例如，线上系统报错时，可以直接把截图发给机器人：

```
代码解读复制代码分析一下截图里的报错，告诉我可能的原因和排查步骤。
```

语音输入也非常适合移动场景。提前设置好目录、权限和项目后，走在路上也可以直接通过语音推进任务。

### 8\. 提供 Web 管理后台

可以通过下面的命令启动管理界面：

```bash
代码解读复制代码cc-connect web
```

在浏览器中完成：

- 项目管理；
- Agent 管理；
- Provider 管理；
- 聊天平台配置；
- 定时任务配置；
- 会话监控；
- 网页聊天。

需要注意：

> `cc-connect web` 主要用于配置和管理，不等于启动桥接服务。

配置完成后，仍然需要运行：

```bash
代码解读复制代码cc-connect
```

或者通过 daemon 模式启动后台服务。

---

## 四、本地安装 cc-connect

### 方式一：让 Claude Code 自动安装

如果你已经安装了 Claude Code，可以直接把下面这段话发给它：

```
代码解读复制代码请参考下面的安装文档，帮我安装和配置 cc-connect：

https://raw.githubusercontent.com/chenhg5/cc-connect/refs/heads/main/INSTALL.md
```

Claude Code 会根据官方文档检查环境并执行安装。

这种方式最省事，也更适合不想手动处理依赖的用户。

### 方式二：使用 npm 安装

手动安装可以执行：

```bash
代码解读复制代码npm install -g cc-connect
```

安装完成后检查版本：

```bash
代码解读复制代码cc-connect --version
```

如果能够正常输出版本号，说明安装成功。

### 方式三：在 macOS 上使用 Homebrew

macOS 用户也可以使用 Homebrew：

```bash
代码解读复制代码brew install cc-connect
```

同样可以通过下面的命令检查：

```bash
代码解读复制代码cc-connect --version
```

> “3 分钟部署”主要指本地安装和启动流程。创建飞书应用、扫码授权以及权限审批所需时间，取决于具体平台和账号环境。

---

## 五、接入飞书机器人

### 第一步：创建飞书应用

打开飞书开放平台：

[open.feishu.cn/app](https://link.juejin.cn/?target=https%3A%2F%2Fopen.feishu.cn%2Fapp "https://open.feishu.cn/app")

创建一个机器人或智能体应用。

建议按照接入的 Agent 命名，例如：

- Home Claude；
- Claude Code Bot；
- Codex Assistant；
- Dev Agent。

创建完成后，记录应用的：

- `App ID` ；
- `App Secret` 。

> 配图建议：飞书开放平台创建应用页面。

### 第二步：执行配置命令

在本地终端中执行：

```bash
代码解读复制代码cc-connect feishu setup \
 --project home-claude \
 --app cli_xxx:sec_xxx
```

其中：

- `home-claude` 是项目名称；
- `cli_xxx` 替换为飞书 App ID；
- `sec_xxx` 替换为飞书 App Secret。

### 第三步：重启服务

```bash
代码解读复制代码cc-connect daemon restart
```

然后在飞书中给机器人发送：

```
代码解读复制代码/help
```

如果机器人能够正常回复，说明飞书已经接入成功。

---

## 六、接入微信

个人微信可以通过对应的 setup 命令完成配置：

```bash
代码解读复制代码cc-connect weixin setup --project home-claude
```

执行后，终端通常会显示：

- 登录二维码；
- 可复制的授权地址；
- 当前登录状态。

使用手机微信扫码或者打开授权地址，完成登录确认。

认证信息会被写入配置文件：

```
代码解读复制代码~/.cc-connect/config.toml
```

完成授权后重启服务：

```bash
代码解读复制代码cc-connect daemon restart
```

然后在微信中向机器人发送一条测试消息，例如：

```
代码解读复制代码/help
```

能够正常回复，就说明连接成功。

> 个人微信接入方式可能受到平台规则、账号状态和项目版本影响。需要更高稳定性时，建议优先选择飞书、钉钉或企业微信等官方机器人通道。

---

## 七、配置项目工作空间

cc-connect 的主要配置文件位于：

```
代码解读复制代码~/.cc-connect/config.toml
```

第一次运行时，程序会自动生成配置模板。

也可以使用 Web 管理后台配置：

```bash
代码解读复制代码cc-connect web
```

一个基础项目配置示例如下：

```toml
代码解读复制代码[[projects]]
name = "home-claude"

[projects.agent]
type = "claudecode"

[projects.agent.options]
work_dir = "/Users/you/Workspace/your-project"
mode = "default"
```

其中， `work_dir` 决定 Agent 默认在哪个目录工作。

配置完成后，即使你人在外面，Agent 也会直接进入正确的项目目录，不需要每次手动切换。

### 为不同项目创建独立配置

建议给每个常用项目创建独立的 project：

```toml
代码解读复制代码[[projects]]
name = "main-project"

[projects.agent]
type = "claudecode"

[projects.agent.options]
work_dir = "/Users/you/Workspace/main-project"
mode = "default"

[[projects]]
name = "blog"

[projects.agent]
type = "claudecode"

[projects.agent.options]
work_dir = "/Users/you/Workspace/blog"
mode = "default"
```

这样可以避免多个项目之间的上下文、工作目录和任务互相干扰。

---

## 八、权限模式怎么选？

权限配置是远程使用 cc-connect 时最需要关注的部分。

常见模式包括：

| 模式 | 说明 |
| --- | --- |
| `default` | 工具调用通常需要确认 |
| `acceptEdits` | 文件编辑自动通过，其他高风险操作仍需确认 |
| `plan` | 只生成方案，不直接执行 |
| `bypassPermissions` / `yolo` | 自动通过全部操作 |

远程使用时，建议默认配置为：

```toml
代码解读复制代码[projects.agent.options]
mode = "default"
```

因为在手机上很难完整查看 Agent 的每一步操作，长期使用全自动权限存在较高风险。

对于明确、低风险的任务，可以临时切换：

```
代码解读复制代码/mode yolo
```

任务完成后立即切回：

```
代码解读复制代码/mode default
```

以下任务不建议使用全自动模式：

- 删除大量文件；
- 修改生产配置；
- 执行数据库变更；
- 提交或推送代码；
- 安装来源不明的软件包；
- 运行无法确认内容的脚本；
- 操作生产服务器。

---

## 九、配置访问控制

远程 Agent 能够读取文件、执行命令，因此一定要限制使用者。

示例配置：

```toml
代码解读复制代码[[projects]]
name = "home-claude"
admin_from = "你的用户ID"

[projects.platforms.options]
allow_from = "你的用户ID或可信群ID"
```

其中：

- `allow_from` ：控制哪些用户或群可以给机器人发送指令；
- `admin_from` ：控制哪些用户可以执行切目录、Shell、重启等高风险操作。

不要这样配置：

```toml
代码解读复制代码admin_from = "*"
```

推荐原则：

> `allow_from` 可以配置为可信群或可信成员， `admin_from` 最好只配置自己的用户 ID。

如果机器人加入了多人群聊，还要注意提示词注入和误操作风险，不要让陌生成员能够直接执行系统命令。

---

## 十、敏感信息不要写死在配置文件中

API Key、App Secret 等敏感信息，建议通过环境变量引用：

```toml
代码解读复制代码api_key = "${ANTHROPIC_API_KEY}"
app_id = "${FEISHU_APP_ID}"
app_secret = "${FEISHU_APP_SECRET}"
```

然后在系统环境中设置变量：

```bash
代码解读复制代码export ANTHROPIC_API_KEY="你的 API Key"
export FEISHU_APP_ID="你的飞书 App ID"
export FEISHU_APP_SECRET="你的飞书 App Secret"
```

相比直接写入配置文件，这种方式可以降低密钥被误提交到 Git 仓库的风险。

同时建议将以下文件加入 `.gitignore` ：

```gitignore
代码解读复制代码.cc-connect/
config.toml
.env
```

---

## 十一、后台运行与开机自启

远程使用不能依赖手动打开终端，所以需要把 cc-connect 配置为后台服务。

执行：

```bash
代码解读复制代码cc-connect daemon install --config ~/.cc-connect/config.toml
cc-connect daemon start
```

在不同系统中，后台服务可能会使用：

- macOS： `launchd` ；
- Linux： `systemd` 。

常用管理命令如下：

```bash
代码解读复制代码# 查看服务状态
cc-connect daemon status

# 实时查看日志
cc-connect daemon logs -f

# 重启服务
cc-connect daemon restart

# 停止服务
cc-connect daemon stop
```

出门前建议完成两项检查：

```bash
代码解读复制代码cc-connect daemon status
```

确认后台服务正常后，再在飞书或微信中发送：

```
代码解读复制代码/help
```

机器人能够正常回复，就可以远程使用了。

---

## 十二、常用命令整理

### 1\. 会话管理

创建新会话：

```
代码解读复制代码/new 修复登录接口超时
```

查看已有会话：

```
代码解读复制代码/list
```

切换到指定会话：

```
代码解读复制代码/switch 2
```

查看当前会话：

```
代码解读复制代码/current
```

查看最近消息：

```
代码解读复制代码/history 10
```

### 2\. 工作目录与模型

查看当前工作目录：

```
代码解读复制代码/dir
```

切换目录：

```
代码解读复制代码/dir ~/workspace/project-a
```

恢复默认目录：

```
代码解读复制代码/dir reset
```

查看当前模型：

```
代码解读复制代码/model
```

切换模型：

```
代码解读复制代码/model switch sonnet
```

查看权限模式：

```
代码解读复制代码/mode
```

临时启用自动执行：

```
代码解读复制代码/mode yolo
```

恢复默认权限：

```
代码解读复制代码/mode default
```

### 3\. 任务控制

立即停止当前任务：

```
代码解读复制代码/stop
```

向正在运行的任务追加要求：

```
代码解读复制代码/ps 不要提交代码，只生成修改方案
```

远程执行 Shell 命令：

```
代码解读复制代码/shell git status
```

查看文件：

```
代码解读复制代码/show README.md
```

### 4\. 系统管理

查看帮助：

```
代码解读复制代码/help
```

查看运行状态：

```
代码解读复制代码/status
```

运行诊断：

```
代码解读复制代码/doctor
```

远程重启服务：

```
代码解读复制代码/restart
```

---

## 十三、几个实用的远程指令模板

### 代码检查

```
代码解读复制代码检查当前仓库最近一次提交，重点关注安全漏洞、异常处理和兼容性问题。不要修改代码，先输出检查报告。
```

### 故障排查

```
代码解读复制代码分析最近一次 CI 失败的原因。先查看日志和相关配置，不要直接修改文件。给出原因、影响范围和修复建议。
```

### 项目分析

```
代码解读复制代码阅读当前仓库，整理项目架构、主要模块、启动流程和外部依赖，生成 docs/architecture.md。
```

### 安全模式修改代码

```
代码解读复制代码修复登录接口的超时问题。修改前先说明计划，完成后运行测试，但不要执行 git commit 和 git push。
```

### 生成日报

```
代码解读复制代码根据今天的 Git 提交和项目文档，整理一份开发日报，包括完成事项、遇到的问题和明天的计划。
```

### 检查服务状态

```
代码解读复制代码查看当前服务运行状态和最近 200 行日志，判断是否存在异常。不要执行重启操作。
```

一条好的远程指令，最好同时包含：

1. 要完成的目标；
2. 可以读取或操作的范围；
3. 是否允许修改文件；
4. 是否允许执行命令；
5. 是否允许提交代码；
6. 最终需要返回什么结果。

---

## 十四、使用 cc-connect 时的安全建议

cc-connect 让手机可以远程操作本地 Agent，也意味着一条聊天消息可能最终变成文件修改或 Shell 命令。

因此建议至少做到以下几点：

1. 默认使用 `default` 或 `plan` 模式；
2. 不要长期启用 `yolo` ；
3. 严格限制 `allow_from` 和 `admin_from` ；
4. 不要将管理员权限开放给整个群；
5. API Key 和 Secret 使用环境变量；
6. 不要让 Agent 默认进入包含大量敏感文件的目录；
7. 重要项目启用 Git，并定期提交；
8. 生产环境操作必须保留人工确认；
9. 不要允许陌生人直接向机器人发送命令；
10. 定期检查 daemon 日志和会话记录。

对于高风险任务，推荐先让 Agent 只输出计划：

```
代码解读复制代码先分析问题并给出执行方案，不要修改文件，也不要运行有副作用的命令。
```

确认方案无误后，再让它继续执行。

---

## 十五、实际使用体验

这类工具最大的价值，并不是让模型突然变得更聪明，而是降低了调度 AI 的阻力。

以前使用 Claude Code，通常需要：

1. 回到电脑前；
2. 打开终端；
3. 进入项目目录；
4. 找到之前的会话；
5. 输入新的任务要求。

接入 cc-connect 后，入口变成了每天都会打开的微信或飞书。

突然想到一个需求时，可以直接发一条消息；任务执行过程中需要调整方向，也可以随时追加要求；离开电脑后，仍然可以查看执行进展和最终结果。

尤其是在飞书和微信中使用语音输入时，操作成本会更低。

例如走在路上直接说：

```
代码解读复制代码检查订单服务今天的修改，重点看看并发问题。不要提交代码，先给我一份分析报告。
```

语音转成文字后发送给 Agent，任务就会在远程电脑上开始执行。

很多原本需要“回家再处理”或者“回到工位再看”的事情，现在可以立刻推进。

---

## 总结

cc-connect 可以理解为：

> 把 Claude Code、Codex、Gemini CLI、Cursor Agent 等本地 AI Agent，变成微信、飞书、钉钉或 Telegram 里的聊天机器人。

它解决的不是模型能力问题，而是 AI Agent 的使用入口问题。

通过 cc-connect，你可以：

- 在手机上远程检查代码；
- 查看长任务执行进度；
- 随时补充和修改要求；
- 远程排查日志和 CI 故障；
- 管理多个 Agent 和多个会话；
- 通过语音推进开发、写作和调研工作。

最简单的安装方式，是直接让 Claude Code 阅读官方安装文档并完成配置：

```
代码解读复制代码请参考下面的安装文档，帮我安装和配置 cc-connect：

https://raw.githubusercontent.com/chenhg5/cc-connect/refs/heads/main/INSTALL.md
```

手动安装则可以执行：

```bash
代码解读复制代码npm install -g cc-connect
cc-connect web
cc-connect
```

需要特别注意：

- `cc-connect web` 用于配置管理；
- `cc-connect` 或 `cc-connect daemon start` 才是启动桥接服务；
- 远程使用时不要忽视权限、访问控制和密钥安全；
- 涉及生产环境、代码提交和文件删除时，始终保留人工确认。

当 AI Agent 的入口从终端变成手机聊天软件后，你获得的不只是一个机器人，而是一个随时可以调度的远程工作节点。