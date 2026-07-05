---
title: "devenv.com使用方法"
source: "https://blog.51cto.com/u_16099244/14417348"
author:
  - "[[码海舵手之心]]"
published: 2025-12-30
created: 2026-06-28
description: "devenv.com使用方法，Devenv入门教程写代码的时候，最麻烦的事情之一，就是配置开发环境。你换了一台电脑，或者来了一位新同事，甚至只是过了一段时间重装了系统，项目就跑不起来了。报错通常是：\"缺少依赖\"、\"版本不兼容\"、\"环境变量未设置\"。这句话大家应该很熟悉：\"明明在我的机器上是好的。\"为了解决这个问题，业界发明了许多工具。Docker是目前的主流方案，通过容器隔离环境。但是，Docker也有缺点：它太重了，文"
tags:
  - "clippings"
---
转载

***文章标签* [Nix](https://blog.51cto.com/topic/nix.html) [开发环境](https://blog.51cto.com/topic/kaifahuanjing.html) [Docker](https://blog.51cto.com/topic/docker.html) [HarmonyOS](https://edu.51cto.com/lesson/975372.html?utm_platform=pc&utm_medium=51cto&utm_source=shequ&utm_content=bk_article_keyword)** ***文章分类* [HarmonyOS](https://blog.51cto.com/nav/harmonyos) [后端开发](https://blog.51cto.com/nav/program)** ***阅读数* **434****

阿里云AI生产力先锋第二期上线啦！面对如今火热的AI视频浪潮，围绕“超级创作者-AI生产力先锋开辟视觉创作新路径”的议题，来自影视、广告、设计等多行业的AI生产力先锋们将带来精彩分享！如何让AI从Toy到Tool再到真正的生产力，让创作者更快落地AI应用制作视频，还有对时下兴起的AI短剧的讨论，你想了解的tips这里都有！👉 立即点击链接，观看视频： [https://click.aliyun.com/m/1000414743/](https://click.aliyun.com/m/1000414743/)

## Devenv 入门教程

写代码的时候，最麻烦的事情之一，就是配置开发环境。

你换了一台电脑，或者来了一位新同事，甚至只是过了一段时间重装了系统，项目就跑不起来了。报错通常是："缺少依赖"、"版本不兼容"、"环境变量未设置"。

这句话大家应该很熟悉："明明在我的机器上是好的。"

为了解决这个问题，业界发明了许多工具。Docker 是目前的主流方案，通过容器隔离环境。但是，Docker 也有缺点：它太重了，文件系统与宿主机隔离，开发体验不如本地原生流畅，且不仅需要编写 Dockerfile，还需要配置 docker-compose。

有没有一种更轻量、更原生的方式，既能保证环境的一致性，又不需要虚拟化呢？

今天，我介绍一个基于 Nix 的工具： **Devenv** 。

## 一、 Devenv 是什么？

要理解 Devenv，首先要提到 **Nix** 。

Nix 是一个强大的包管理器，也是一种配置语言。它的核心理念是 "声明式"（Declarative）和 "可复现"（Reproducible）。只要你有 Nix 配置文件，无论在 Linux 还是 macOS 上，都能构建出完全一样的二进制环境。

但是，Nix 有一个巨大的门槛：它的配置语言太晦涩了，学习曲线非常陡峭。

Devenv 的出现，就是为了解决这个问题。它的全称是 **Developer Environment** 。

Devenv 是 Nix 的一层封装。它允许你用简单、易读的语法，定义开发环境所需的各种组件（语言、数据库、进程、Git钩子等）。它自动生成底层的 Nix 配置，让你既享受 Nix 的强大，又不必承受 Nix 的痛苦。

简单说，Devenv 的目标是： **让开发环境像代码一样管理（Infrastructure as Code）。**

## 二、 安装

在使用 Devenv 之前，你的机器上需要先安装 Nix。

**1\. 安装 Nix**

如果你还没有安装 Nix，可以使用官方推荐的安装脚本（支持 macOS 和 Linux）：

```
# Linux
sh <(curl -L https://nixos.org/nix/install) --daemon

# mac
curl -L https://github.com/NixOS/experimental-nix-installer/releases/download/0.27.0/nix-installer.sh | sh -s -- install1.2.3.4.5.
```

安装完成后，记得开启 Nix 的 Flakes 功能（这是新版 Nix 的特性），在 `~/.config/nix/nix.conf` 中添加：

```
experimental-features = nix-command flakes1.
```

**2\. 安装 Devenv**

有了 Nix，安装 Devenv 就只需要一行命令：

```
$ nix profile install github:cachix/devenv/latest1.
```

安装完成后，你可以通过下面的命令验证：

```
$ devenv version1.
```

## 三、 快速开始

我们建立一个名为 `my-project` 的目录，尝试初始化一个环境。

```
$ mkdir my-project
$ cd my-project
$ devenv init1.2.3.
```

这个命令会生成一个关键文件： `devenv.nix` 。

打开这个文件，你会发现它非常直观。默认生成的模板大概长这样：

```
{ pkgs, lib, config, inputs, ... }:

{
  # 环境变量
  env.GREET = "devenv";

  # 安装的软件包
  packages = [ pkgs.git pkgs.openssl ];

  # 启用某些脚本
  scripts.hello.exec = "echo hello from $GREET";

  # 开启 shell hook
  enterShell = ''
    hello
    git --version
  '';
}1.2.3.4.5.6.7.8.9.10.11.12.13.14.15.16.17.18.
```

现在，我们进入这个环境：

```
$ devenv shell1.
```

这一步，Devenv 会自动下载 `git` 和 `openssl` （如果缓存里没有的话），并将它们加入当前的 PATH。当你看到命令行前缀发生变化，说明你已经处于隔离的开发环境中。

在该环境中运行 `hello` ，你会看到输出 `hello from devenv` 。

当你输入 `exit` 退出 Shell 后，刚才安装的软件和环境变量就会消失，不会污染你的系统。

## 四、 核心功能

Devenv 不仅仅是安装软件包，它针对开发者的日常需求做了深度集成。

### 1\. 语言支持

配置编程语言环境通常是最头疼的。Devenv 提供了高度封装的接口。

比如，你需要一个 Python 开发环境，包含 Poetry 包管理器：

```
{ pkgs, ... }: {
  languages.python = {
    enable = true;
    version = "3.10";
    poetry.enable = true;
  };
}1.2.3.4.5.6.7.
```

如果你是 Rust 开发者：

```
{ pkgs, ... }: {
  languages.rust = {
    enable = true;
    # 自动使用 rust-overlay 提供的 stable 版本
    channel = "stable";
  };
}1.2.3.4.5.6.7.
```

JavaScript、Go、Haskell 等主流语言都有对应的配置项。

### 2\. 服务（Services）

这是 Devenv 最杀手级的功能。

以前，为了跑一个项目，你可能需要在本地安装 Postgres、Redis，或者用 Docker 起一堆容器。Devenv 允许你直接在 `devenv.nix` 里声明这些服务。

```
{ pkgs, ... }: {
  services.postgres = {
    enable = true;
    initialDatabases = [{ name = "mydb"; }];
    listen_addresses = "127.0.0.1";
  };

  services.redis.enable = true;
}1.2.3.4.5.6.7.8.9.
```

配置好后，不需要 `systemctl` ，也不需要 `docker run` ，只需在项目根目录执行：

```
$ devenv up1.
```

这个命令会在前台启动所有定义的服务，并且将日志聚合输出。这些服务是跟着当前项目走的，数据也是存储在项目目录下的 `.devenv` 文件夹中，完全不用担心端口冲突或数据污染。

### 3\. 进程管理（Processes）

除了数据库，你可能还需要运行后端 API 服务和前端构建脚本。Devenv 允许你定义后台进程：

```
{ pkgs, ... }: {
  processes.backend.exec = "python manage.py runserver";
  processes.frontend.exec = "npm start";
}1.2.3.4.
```

当你运行 `devenv up` 时，这两个进程也会一同启动。这有点像 `foreman` 或 `docker-compose` ，但它是直接运行在宿主机环境里的。

### 4\. 代码质量钩子（Pre-commit Hooks）

为了保证代码质量，我们通常会配置 Git Hooks。Devenv 集成了 pre-commit 框架。

你可以在配置文件中启用各种检查工具：

```
{ pkgs, ... }: {
  pre-commit.hooks = {
    shellcheck.enable = true;      # 检查 Shell 脚本
    nixpkgs-fmt.enable = true;     # 格式化 Nix 文件
    rustfmt.enable = true;         # 格式化 Rust 代码
    black.enable = true;           # 格式化 Python 代码
  };
}1.2.3.4.5.6.7.8.
```

当你执行 `git commit` 时，这些检查会自动运行。如果检查不通过，提交就会被阻止。

## 五、 为什么选择 Devenv？

这时候你可能会问，我已经有 Docker 了，为什么要用 Devenv？

**1\. 性能与原生体验**

Docker 是虚拟化（或容器化），文件 I/O 在某些系统（如 macOS）上存在性能瓶颈。Devenv 则是基于 Nix 的，它仅仅是修改了环境变量（PATH），调用的全是原生二进制文件，速度极快，且能直接使用本地 IDE。

**2\. 声明式配置**

Makefiles 或 Shell 脚本是命令式的（Imperative），你告诉电脑"先做这，再做那"。随着时间推移，脚本变得难以维护。Devenv 是声明式的（Declarative），你只描述"我想要什么"，Nix 负责计算出如何达到那个状态。

**3\. 可组合性**

你可以把 `devenv.nix` 拆分成多个模块，或者引入其他人的配置。这使得配置非常灵活。

## 六、 总结

Devenv 是一个非常现代化的工具。它填补了"简单的 Shell 脚本"和"厚重的 Docker 容器"之间的空白。

它利用 Nix 强大的包管理能力，解决了"依赖地狱"的问题，同时通过友好的配置语法，降低了普通开发者的使用门槛。

如果你厌倦了配置开发环境，或者想让团队的开发环境统一化，不妨试一试 Devenv。

阿里云AI生产力先锋第二期上线啦！面对如今火热的AI视频浪潮，围绕“超级创作者-AI生产力先锋开辟视觉创作新路径”的议题，来自影视、广告、设计等多行业的AI生产力先锋们将带来精彩分享！如何让AI从Toy到Tool再到真正的生产力，让创作者更快落地AI应用制作视频，还有对时下兴起的AI短剧的讨论，你想了解的tips这里都有！👉 立即点击链接，观看视频： [https://click.aliyun.com/m/1000414743/](https://click.aliyun.com/m/1000414743/)

本文章为转载内容，我们尊重原作者对文章享有的著作权。如有内容错误或侵权问题，欢迎原作者联系我们进行内容更正或删除文章。

**相关文章**