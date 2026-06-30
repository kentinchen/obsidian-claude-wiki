---
title: "安装说明 | V2Fly中文站"
source: "https://v2fly.com.cn/guide-install.html"
author:
published:
created: 2026-06-30
description: "V2Ray 全平台安装指南：Linux 脚本安装、macOS Homebrew、Windows 绿色包、Docker 容器及源码编译安装方式"
tags:
  - "clippings"
---
## Linux / macOS

推荐使用官方安装脚本：

```
# 安装最新版本
bash <(curl -L https://raw.githubusercontent.com/v2fly/fhs-install-v2ray/master/install-release.sh)

# 安装指定版本
bash <(curl -L https://raw.githubusercontent.com/v2fly/fhs-install-v2ray/master/install-release.sh) -v v5.0.0
```

### 手动安装

从 [GitHub Releases](https://github.com/v2fly/v2ray-core/releases) 下载对应平台的压缩包，解压到目标目录即可。

```
# 示例：下载并解压 Linux 64 位版本
wget https://github.com/v2fly/v2ray-core/releases/latest/download/v2ray-linux-64.zip
unzip v2ray-linux-64.zip -d /usr/local/v2ray
chmod +x /usr/local/v2ray/v2ray
```

### 包管理器安装

```
# macOS (Homebrew)
brew install v2ray

# Debian/Ubuntu
sudo apt update && sudo apt install v2ray

# Arch Linux
sudo pacman -S v2ray

# Fedora
sudo dnf install v2ray
```

## Windows

从 GitHub Releases 下载 Windows 版本的 zip 包，解压后即可使用。

- 下载 `v2ray-windows-64.zip` （64位系统）或 `v2ray-windows-32.zip` （32位系统）
- 解压到指定目录（如 `C:\v2ray\` ）
- 使用命令行运行： `v2ray.exe run -c config.json`

也可以使用 [Chocolatey](https://chocolatey.org/packages/v2ray) 安装：

```
choco install v2ray
```

## Docker

使用 Docker 运行 V2Ray：

```
# 拉取镜像
docker pull v2fly/v2fly-core

# 运行容器
docker run -d --name v2ray \
  -v /path/to/config.json:/etc/v2ray/config.json \
  -p 1080:1080 \
  v2fly/v2fly-core

# 使用 docker-compose
version: '3'
services:
  v2ray:
    image: v2fly/v2fly-core
    container_name: v2ray
    restart: always
    volumes:
      - ./config.json:/etc/v2ray/config.json
    ports:
      - 1080
```

## 验证安装

安装完成后，运行以下命令验证：

```
v2ray version
# 输出示例：
# V2Ray 5.0.0 (V2Fly) ...
```

> ⚠️ 注意：请确保配置文件路径正确，并根据需要修改端口映射。