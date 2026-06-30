---
title: "Claude Desktop Windows版本国内网络环境完全&quot;离线&quot;安装方法"
source: "https://www.cnblogs.com/lijiext/p/20186706"
author:
  - "[[codesucks]]"
published: 2026-05-27
created: 2026-06-29
description: "效果 软件包下载 也可以下载我的存档：Claude Desktop Windows 安装包(1.9255.0) 链接: https://pan.baidu.com/s/1FDVMR0n5bb5BuFUNMAojyQ?pwd=9d8a 提取码: 9d8a 1. Claude Desktop桌面版安装包"
tags:
  - "clippings"
---
## 效果## 软件包下载

也可以下载我的存档：Claude Desktop Windows 安装包(1.9255.0) 链接: [https://pan.baidu.com/s/1FDVMR0n5bb5BuFUNMAojyQ?pwd=9d8a](https://pan.baidu.com/s/1FDVMR0n5bb5BuFUNMAojyQ?pwd=9d8a) 提取码: 9d8a

### 1\. Claude Desktop桌面版安装包claude.msix

需要首先在能访问claude的网络环境下下载好安装包，msix格式，官网下载地址： [https://claude.ai/api/desktop/win32/x64/msix/latest/redirect](https://claude.ai/api/desktop/win32/x64/msix/latest/redirect)

### 2\. Claude Code执行文件claude.exe

然后下载对应版本的claude code，例如 [https://downloads.claude.ai/claude-code-releases/2.1.149/win32-x64/claude.exe](https://downloads.claude.ai/claude-code-releases/2.1.149/win32-x64/claude.exe)

### 3\. API转换器

国内使用需要准备好第三方的API接口转换工具，这里使用cc desktop switch，也下载好： [https://github.com/lonr-6/cc-desktop-switch/releases/download/v1.0.25/CC-Desktop-Switch-v1.0.25-Windows-x64.exe](https://github.com/lonr-6/cc-desktop-switch/releases/download/v1.0.25/CC-Desktop-Switch-v1.0.25-Windows-x64.exe)

将上面的三个文件拷贝到需要安装的电脑上

## 安装

1. 使用管理员权限打开powershell，执行 `Add-AppxPackage -Path "Claude.msix"`
2. 拷贝claude.exe到C:\\Users<用户名>\\AppData\\Local\\Claude-3p\\claude-code\\2.1.149目录
3. 打开cc desktop switch，配置API和KEY，并点击一键应用到claude桌面版，然后启动（天线按钮）
4. 打开claude desktop，cowork可能需要开启虚拟化功能需重启
5. 安装完成，可以进行测试

## 提示

1. claude.msix和claude.exe的版本是一一对应的（因为假设需要安装的机器完全无法访问anthropic，所以会使用自带的默认版本，不知道默认版本你可能至少需要安装一次打开程序后查看C:\\Users<用户名>\\AppData\\Local\\Claude-3p\\logs\\main.log中的日志，获取版本信息）
2. 如果你需要中文汉化版本可以参考： [https://github.com/javaht/claude-desktop-zh-cn](https://github.com/javaht/claude-desktop-zh-cn)

作者：lijiext

出处： [https://www.cnblogs.com/lijiext/p/20186706](https://www.cnblogs.com/lijiext/p/20186706)

版权：本作品采用「 [署名-非商业性使用-相同方式共享 4.0 国际](https://creativecommons.org/licenses/by-nc-sa/4.0/) 」许可协议进行许可。

本人文章禁止转载，博客地址：https://www.cnblogs.com/lijiext