---
title: "Claude Code + LM Studio + CC-Switch 本地自动化编程部署指南 - hey99 知识搜索引擎"
source: "https://www.hey99.cn/shot/CSDN_161371267"
author:
published: 2026-06-08
created: 2026-07-02
description: "CC-Switch 是一个带 GUI 的代理工具，让 Claude Code 能一键切换不同模型供应商（本地 LM Studio、Kimi、DeepSeek 等）。@dataclass\"\"\"1000Hz，来自六自由度积分器\"\"\"yaw: float@dataclass\"\"\"200Hz，来自传感器组件\"\"\"@dataclass\"\"\"50Hz，来自制导律\"\"\"@dataclass\"\"\"200Hz，来自驾驶仪\"\"\"@dataclass\"\"\"1000Hz，来自舵机动力学\"\"\""
tags:
  - "clippings"
---
## Claude Code + LM Studio + CC-Switch 本地自动化编程部署指南

> 本指南汇总了在 Windows 本地环境下，使用 Claude Code 配合 LM Studio 本地模型、CC-Switch 代理进行自动化编程开发的完整配置方案。

---

### 目录

### 一、硬件与模型选型

#### 1.1 硬件参考（RTX 3060 Ti 12GB）

| 指标 | 推荐配置 |
| --- | --- |
| GPU | RTX 3060 Ti 12GB |
| 显存可用 | 约 10~11 GB（系统预留 1~2GB） |
| 适合模型规模 | 7B~14B（Q4\_K\_M 量化） |

#### 1.2 模型推荐（按编码能力排序）

##### 首选：Qwen2.5-Coder-14B-Instruct

| 项目 | 详情 |
| --- | --- |
| **量化推荐** | `Q4_K_M` （约 8.5GB）或 `Q5_K_S` （约 9.5GB） |
| **显存占用** | 8.5 ~ 9.5 GB |
| **编码能力** | 当前开源编码最强之一，支持 92 种编程语言 |
| **3060Ti 速度** | Q4\_K\_M 约 **18-28 tok/s** |
| **LM Studio 搜索** | `Qwen2.5-Coder-14B-Instruct-GGUF` |

##### 备选：Qwen3-14B

| 项目 | 详情 |
| --- | --- |
| **量化推荐** | `Q4_K_M` （约 8.4GB） |
| **特点** | 全能型，支持 Thinking / Non-thinking 双模式 |
| **3060Ti 速度** | 约 **20-30 tok/s** |

##### 极速版：Qwen2.5-Coder-7B

| 项目 | 详情 |
| --- | --- |
| **量化推荐** | `Q6_K` （约 6GB） |
| **特点** | 显存占用低，响应极快 |
| **3060Ti 速度** | 约 **40-60 tok/s** |

#### 1.3 量化选择优先级

```
Q4_K_M  → 平衡首选（推荐）
Q5_K_S  → 质量稍好，14B 在 12GB 下仍安全
Q6_K    → 7B 模型可以上，14B 不建议（太紧张）
```

---

### 二、LM Studio 本地模型部署

#### 2.1 下载与加载模型

1. 打开 **LM Studio**
2. 左侧 **Search** → 搜索模型名称（如 `Qwen2.5-Coder-14B-Instruct-GGUF` ）
3. 选择 `lmstudio-community` 发布的版本
4. 下载 `Q4_K_M` 或 `Q5_K_S` 量化版本
5. 加载模型

#### 2.2 启动本地 API 服务

1. 点击左侧 **Developer** → **Start Server**
2. 关键配置：

| 配置项 | 值 | 说明 |
| --- | --- | --- |
| **Port** | `1234` | 默认端口 |
| **Enable CORS** | ✅ **必须打开** | Claude Code 跨域需要 |
| **API Key** | 留空或 `lm-studio` | 本地通常不强制校验 |

3. 确认端点可用：
```
http://localhost:1234/v1
```
4. 验证模型列表（浏览器访问）：
```
http://localhost:1234/v1/models
```

#### 2.3 性能优化设置

加载模型后，右侧设置：

| 配置项 | 推荐值 |
| --- | --- |
| **Context Length** | `4096` 或 `8192` （编码任务不需要太长） |
| **GPU Offload** | **Max** （全部层放 GPU） |
| **Batch Size** | 512 或 1024 |

> ⚠️ 如果显存紧张，Context Length 降到 4096。

---

### 三、CC-Switch 代理配置

#### 3.1 CC-Switch 简介

CC-Switch 是一个带 GUI 的代理工具，让 Claude Code 能一键切换不同模型供应商（本地 LM Studio、Kimi、DeepSeek 等）。

#### 3.2 添加本地 LM Studio Provider

1. 打开 CC-Switch 桌面应用
2. 点击右上角 **+** → **Add New Provider**
3. 填写参数：

| 字段 | 值 |
| --- | --- |
| Provider Name | `LM-Studio-Local` （自定义） |
| API Endpoint | `http://localhost:1234/v1` |
| API Key | `lm-studio` （或任意占位符） |
| **API 格式** | **`OpenAI 兼容`** ⚠️ **必须选这个！** |
| 认证字段 | `ANTHROPIC_AUTH_TOKEN` （默认） |

> ⚠️ **关键** ：LM Studio 的 `/v1` 端点是 **OpenAI 兼容格式** ，不是 Anthropic 原生格式。如果 CC-Switch 没有 “OpenAI 兼容” 选项，说明该版本不支持本地 OpenAI 模型，需换 `claude-code-router` 或 `LiteLLM` 。

#### 3.3 模型映射填写

本地只有一个模型， **三个角色都填同一个** ：

| 模型角色 | 显示名称 | 实际请求模型 | 声明支持 1M |
| --- | --- | --- | --- |
| **Sonnet** | `Qwen Coder 14B` | `[LM Studio 准确ID]` | ❌ 不勾选 |
| **Opus** | `Qwen Coder 14B` | `[LM Studio 准确ID]` | ❌ 不勾选 |
| **Haiku** | `Qwen Coder 14B` | `[LM Studio 准确ID]` | ❌ 不勾选 |

**获取准确模型 ID** ：

- 浏览器访问 `http://localhost:1234/v1/models`
- 复制 `data[0].id` 字段的值（如 `qwen2.5-coder-14b-instruct` ）
- **必须一字不差** ，包括大小写和连字符

#### 3.4 添加 Kimi Provider（云端备选）

| 字段 | 值 |
| --- | --- |
| Provider Name | `Kimi-Moonshot` |
| API Endpoint | `https://api.moonshot.cn/v1` |
| API 格式 | `OpenAI 兼容` |
| API Key | 你的 `sk-xxx` Moonshot Key |
| Sonnet/Opus 实际模型 | `kimi-k2.6` |
| Haiku 实际模型 | `kimi-k2.5` 或 `kimi-k2-turbo-preview` |

> ⚠️ `kimi-k2.6` 默认 thinking 模式，temperature 锁定为 1.0，不要手动传 temperature 参数。

#### 3.5 启动代理

1. 在 CC-Switch 里启用目标 Provider
2. 确认本地代理已启动（默认 `http://127.0.0.1:15721` ）
3. **完全关闭** CC-Switch 再重新打开（确保配置生效）

---

### 四、Claude Code 配置

#### 4.1 settings.json 配置

文件路径： `~/.claude/settings.json` （Windows 通常是 `C:\Users\你的用户名\.claude\settings.json` ）

**本地模型配置（LM Studio）：**

```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "http://127.0.0.1:15721",
    "ANTHROPIC_AUTH_TOKEN": "PROXY_MANAGED",
    "ANTHROPIC_MODEL": "qwen2.5-coder-14b-instruct",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "qwen2.5-coder-14b-instruct",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "qwen2.5-coder-14b-instruct",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "qwen2.5-coder-14b-instruct",
    "CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC": "1",
    "CLAUDE_CODE_EFFORT_LEVEL": "max"
  }
}
```

**Kimi 云端配置：**

```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "http://127.0.0.1:15721",
    "ANTHROPIC_AUTH_TOKEN": "PROXY_MANAGED",
    "ANTHROPIC_MODEL": "kimi-k2.6",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "kimi-k2.6",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "kimi-k2.6",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "kimi-k2.5",
    "CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC": "1",
    "CLAUDE_CODE_EFFORT_LEVEL": "max"
  }
}
```

#### 4.2 验证连接

1. **完全关闭** 终端和 Claude Code
2. 重新启动 Claude Code
3. 输入：
```
/model
```

确认菜单显示的是你配置的模型名称

4. 测试对话：
```
hello, which model are you using now?
```

---

### 五、自动化编程工作流

#### 5.1 核心思路

让 Claude Code **全自动、零干预** 地实现项目：

- 把设计方案作为永久上下文（CLAUDE.md）
- 分阶段交付
- 提前授权所有操作

#### 5.2 创建 CLAUDE.md 宪法文件

在项目根目录创建 `CLAUDE.md` ，Claude Code 启动时会自动读取。

**模板结构：**

```markdown
# 项目名 — 开发宪法

## 技术栈
- Python 3.10+
- numpy, scipy, matplotlib, pytest
- PyQt6（UI层）

## 开发原则（强制执行）
1. **测试驱动**：每写一个模块，必须同时写对应的 pytest 单元测试
2. **零UI依赖**：core/ 目录下的模块不得导入任何 GUI 库
3. **自动安装**：遇到缺失依赖时，自动执行 \`pip install\` 安装
4. **无需询问**：直接执行所有操作，不需要用户确认

## 目录结构（严格遵守）
project/
├── core/        # 模型库（零UI依赖）
├── engine/      # 仿真引擎
├── gui/         # UI可视化
├── tests/       # 单元测试 + 验收测试
└── examples/    # 示例脚本

## 实现顺序（分阶段，禁止跳阶段）
### Phase 1：核心闭环（最高优先级）
- 模块 A + 单元测试
- 模块 B + 单元测试
- 闭环集成测试

### Phase 2：架构完善
...

## 关键参数（不可改动）
- param1 = xxx
- param2 = yyy

## 代码规范
- 使用类型注解
- 所有物理量标注单位
- 角度统一用 rad

## 权限声明
你被授权：
- 读取/写入项目目录下所有文件
- 自动安装 Python 依赖
- 自动创建目录和文件
- 执行 pytest 运行测试
- 不需要询问用户确认，直接执行
```

#### 5.3 分阶段实现策略

**不要一次性让它做完整项目！**

| 会话 | 目标 | 预计时间 |
| --- | --- | --- |
| 第 1 次 | Phase 1：核心算法 + 单元测试 | 30-60 分钟 |
| 第 2 次 | Phase 2：架构 + 集成 | 30-60 分钟 |
| 第 3 次 | Phase 3：扩展功能 | 60-90 分钟 |
| 第 4 次 | Phase 4：可视化 + 最终集成 | 60-90 分钟 |

**每次启动新会话时** ，先让它 `Read CLAUDE.md` 回顾上下文，然后指定当前 Phase。

#### 5.4 一键启动 Prompt

保存为 `prompt.txt` ，每次启动 Claude Code 时粘贴：

```
/read CLAUDE.md

请执行 Phase X（替换为当前阶段）：

1. 自动创建所有目录和文件
2. 严格按设计文档实现代码
3. 每模块配 pytest 测试
4. 运行验收测试并自动修复至通过
5. 数值误差 < 2%
6. 无需询问，直接执行

完成后汇报：文件清单 + 测试结果 + 已知问题
```

---

### 六、TMSim 项目实战模板

#### 6.1 项目架构（四层模型）

```
┌─────────────────────────────────────────┐
│   UI可视化层（PyQt6 + Matplotlib）       │
│   ├─ 参数配置面板                        │
│   ├─ 实时曲线绘制（时域阶跃、频域伯德图）│
│   └─ 根轨迹图                            │
├─────────────────────────────────────────┤
│   仿真引擎层（调度、积分、事件检测）      │
│   ├─ 数值积分器（RK4 定步长）            │
│   ├─ 多速率调度器（1000/200/50 Hz）      │
│   └─ 事件检测（命中、脱靶、舵饱和）      │
├─────────────────────────────────────────┤
│   模型库层（算法核心，零UI依赖）          │
│   ├─ 弹体动力学（线性/非线性）           │
│   ├─ 舵机传感器                          │
│   ├─ 过载驾驶仪（2回路/PI/3回路）        │
│   ├─ 制导律（PN/OPN/LOS）                │
│   └─ 导引头 + 雷达                       │
├─────────────────────────────────────────┤
│   数据管理层（记录、导出、后处理）        │
│   ├─ 时序记录器（HDF5）                  │
│   └─ CSV导出 + 统计分析                  │
└─────────────────────────────────────────┘
```

#### 6.2 标准数据包定义（5大总线）

```python
from dataclasses import dataclass
from typing import Optional

@dataclass
class TrueStateBus:
    """1000Hz，来自六自由度积分器"""
    timestamp: float
    pos_x: float; pos_y: float; pos_z: float
    vel_x: float; vel_y: float; vel_z: float
    roll: float; pitch: float; yaw: float
    omega_x: float; omega_y: float; omega_z: float
    los_angle: float; range_: float; range_rate: float

@dataclass
class NavDataBus:
    """200Hz，来自传感器组件"""
    timestamp: float
    accel_y_meas: float
    omega_z_meas: float
    los_angle_rate_est: float

@dataclass
class GuidanceCmdBus:
    """50Hz，来自制导律"""
    timestamp: float
    ay_cmd: float
    az_cmd: float
    gamma_cmd: float
    t_go: Optional[float] = None

@dataclass
class ActuatorCmdBus:
    """200Hz，来自驾驶仪"""
    timestamp: float
    delta_x: float; delta_y: float; delta_z: float

@dataclass
class ForceMomentBus:
    """1000Hz，来自舵机动力学"""
    timestamp: float
    force_x: float; force_y: float; force_z: float
    moment_x: float; moment_y: float; moment_z: float
```

#### 6.3 关键教材参数（不可改动）

```python
# 弹体线性化参数（表4.1-1）
a_alpha = 72.4      # s^-2
a_delta = 471.0     # s^-2
a_omega = 1.5       # s^-2
b_alpha = 1.27      # s^-1
b_delta = 0.477     # s^-1
c = 0.66            # m
V = 1140.0          # m/s

# 驾驶仪参数（两回路）
K_A = 0.00065       # s^2/(m·N)
K_g = 0.0728        # s

# 舵机参数
k_r = -0.0175
tau = 0.0133        # s
```

#### 6.4 验收标准（Week 1）

```python
# 图4.1-8 单位阶跃过载响应
# 条件1：初始下冲（t=0.05s）
assert -0.25 < ay_down < -0.15

# 条件2：稳态值（t>0.4s）
assert 0.78 < ay_ss < 0.80

# 条件3：调节时间
assert t_settle < 0.4

# 条件4：无NaN
assert not np.isnan(ay_array).any()
```

---

### 七、常见问题排查

#### 7.1 CC-Switch 相关问题

| 问题 | 原因 | 解决 |
| --- | --- | --- |
| 没有 “OpenAI 兼容” 选项 | 版本只支持 Anthropic 后端 | 换 `claude-code-router` 或 `LiteLLM` |
| 401 Invalid Authentication | Key 错误或端点混用 | 确认端点和 Key 匹配 |
| 404 Model Not Found | 模型 ID 拼写错误 | 从 `http://localhost:1234/v1/models` 复制准确名称 |
| 400 invalid temperature | kimi-k2.6 默认 thinking 模式锁定 temperature=1.0 | 不传 temperature 参数，或换模型 |

#### 7.2 LM Studio 相关问题

| 问题 | 原因 | 解决 |
| --- | --- | --- |
| CORS 错误 | LM Studio 没开 CORS | Developer → 勾选 Enable CORS |
| 模型加载失败 | 显存不足 | 换更小的量化版本或减小 Context Length |
| 响应极慢 | GPU Offload 不够 | 右侧设置 GPU Offload 拉到 Max |

#### 7.3 Claude Code 相关问题

| 问题 | 原因 | 解决 |
| --- | --- | --- |
| `pip: command not found` | 环境 PATH 问题 | 用 `python -m pip` 代替 |
| 测试一直失败 | 实现逻辑错误 | 暂停测试，先检查数学公式推导 |
| 想改参数让测试通过 | 参数是宪法 | 制止！参数不可改，只能改代码 |
| 上下文溢出 | 文件太多 | 重启会话，基于已有代码继续 |

#### 7.4 本地模型 Tool Calling 问题

Qwen 本地量化版在 Claude Code 的 agentic 模式（自动读写文件、执行命令）下可能不稳定：

```
Failed to parse tool call: Unexpected end of content.
Failed to parse tool call: Expected ""name"", but got ""name" at index 13.
```

**解决：**

- 这是模型输出格式不符合 Claude Code 的 XML tool use 格式
- 换更强的模型（14B 比 7B 稳定）
- 或降低任务复杂度，分步执行

---

### 附录：替代工具

如果 CC-Switch 不满足需求，可考虑：

| 工具 | 定位 | 安装 |
| --- | --- | --- |
| **claude-code-proxy** | Claude Code 专用，原生支持 Kimi Code | `brew install raine/claude-code-proxy/claude-code-proxy` |
| **claude-code-router** | 本地模型专用，支持 LM Studio/Ollama | `npm install -g @musistudio/claude-code-router` |
| **UniClaudeProxy** | 通用全能，支持任意后端 | `pip install uniclaudproxy` |
| **LiteLLM** | 企业网关，100+ 模型 | `pip install litellm` |

---

> 文档版本：v1.0  
> 更新日期：2026-05-24