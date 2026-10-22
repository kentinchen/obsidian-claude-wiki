# CC-Switch Agent 配置指南

本文档整理了如何在 CC-Switch 中配置常用 AI Agent（Claude Code, OpenAI Codex, OpenCode）。

**假设条件：**
- **后端 API 地址**: `http://localhost:13004`（本地 SGLang 服务，实际加载模型 `Qwen3.8-27B-FP8`）
- **API Key**: 任意值即可（SGLang 本地服务不校验；走 CC-Switch 代理时统一由代理托管，Agent 侧填 `PROXY_MANAGED`）
- **CC-Switch 本地代理地址**: `http://127.0.0.1:15721/v1`

---

## 1. 核心概念

本地 SGLang 服务 (`localhost:13004`) 同时提供多协议端点：

- **Anthropic Messages**（`/v1/messages`）：SGLang 原生支持，Claude Code 可直连；推荐经 CC-Switch 代理以获得请求改写、故障转移等能力。
- **OpenAI Responses**（`/v1/responses`）：Codex 需要，经 CC-Switch 代理转发。
- **OpenAI Chat Completions**（`/v1/chat/completions`）：OpenCode 等标准 OpenAI 客户端可直连。

> 注意：上游对 effort（推理力度）参数支持不完整，Claude 侧与 Codex 侧的配置都有讲究，详见第 6 节实战案例。

---

## 2. Claude Code 配置

**协议需求**: Anthropic Messages (需要代理转换)

### 步骤 1：在 CC-Switch 中添加提供商
1. 进入 **Claude** 标签页。
2. 点击 **Add Provider**，填写：
   - **Name**: `Qwen3.8-27B`
   - **Base URL**: `http://localhost:13004` (SGLang 上游真实地址，代理会自动转发)
   - **API Key**: 任意值（本地服务不校验）
   - **Model**: `Qwen3.8-27B`（四个档位 Opus/Sonnet/Haiku/Fable 全部映射到它）
   - **API Format**: `Anthropic`（SGLang 原生支持 /v1/messages，无需协议转换）。

### 步骤 2：设置代理路由
1. 在 **Settings** 中确保 **Local Proxy** 已开启。
2. 在 **Claude** 标签页，将刚才添加的提供商设为 **Current**。
3. **关键步骤**：打开 `C:\Users\<用户名>\.claude\settings.json`，修改环境变量指向本地代理（以下为当前实际生效的配置）：
   ```json
   {
     "env": {
       "ANTHROPIC_BASE_URL": "http://127.0.0.1:15721",
       "ANTHROPIC_AUTH_TOKEN": "PROXY_MANAGED",
       "ANTHROPIC_DEFAULT_OPUS_MODEL": "claude-opus-5",
       "ANTHROPIC_DEFAULT_SONNET_MODEL": "claude-sonnet-5",
       "ANTHROPIC_DEFAULT_HAIKU_MODEL": "claude-haiku-5-5",
       "ANTHROPIC_DEFAULT_FABLE_MODEL": "claude-fable-5",
       "ANTHROPIC_DEFAULT_OPUS_MODEL_NAME": "Qwen3.8-27B",
       "ANTHROPIC_DEFAULT_SONNET_MODEL_NAME": "Qwen3.8-27B",
       "ANTHROPIC_DEFAULT_HAIKU_MODEL_NAME": "Qwen3.8-27B",
       "ANTHROPIC_DEFAULT_FABLE_MODEL_NAME": "Qwen3.8-27B",
       "CLAUDE_CODE_SUBAGENT_MODEL": "Qwen3.8-27B",
       "CLAUDE_CODE_EFFORT_LEVEL": "low",
       "CLAUDE_CODE_AUTO_MODE_SERVER": "0"
     }
   }
   ```
   > 代理接管模式下，`*_MODEL` 是发给代理的档位名（代理再映射到 Qwen3.8-27B），`*_MODEL_NAME` 仅作显示。
   > `CLAUDE_CODE_EFFORT_LEVEL=low` 用于规避上游 effort 不兼容问题（见 6.1），也可以改用 CC-Switch 请求体改写方案。

---

## 3. OpenAI Codex 配置

**协议需求**: OpenAI Responses API
*注：经 CC-Switch 代理转发到上游 `/v1/responses`。*

### 步骤 1：在 CC-Switch 中添加提供商
1. 进入 **Codex** 标签页。
2. 点击 **Add Provider**，填写：
   - **Name**: `Qwen3.8-27B`
   - **Base URL**: `http://localhost:13004/v1`
   - **API Key**: 任意值（本地服务不校验）
   - **Model**: `Qwen3.8-27B`
   - **API Format**: `OpenAI`。

### 步骤 2：修改 Codex 配置
1. 编辑 `C:\Users\<用户名>\.codex\config.toml`（以下为当前实际生效的配置）：
   ```toml
   model = "Qwen3.8-27B"
   model_provider = "custom"
   model_reasoning_effort = "medium"   # 上游只支持 xhigh/medium/low，填 high 会报 400
   disable_response_storage = true

   [model_providers]

   [model_providers.custom]
   name = "custom"
   wire_api = "responses"
   requires_openai_auth = false
   base_url = "http://127.0.0.1:15721/v1"
   experimental_bearer_token = "PROXY_MANAGED"
   ```
3. **保持两处一致**：CC-Switch 中该 Codex 供应商的 config 片段里 `model_reasoning_effort` 也必须是 `medium`（目前已同步）。若只改 `config.toml` 不改 CC-Switch，下次切换供应商时会被覆盖回旧值。

---

## 4. OpenCode 配置

**协议需求**: OpenAI Chat Completions (支持直连)

> **当前状态（2026-10-22 核对）**：`~/.config/opencode/opencode.jsonc` 只有 `$schema` 一行，OpenCode 尚未配置任何后端。以下为需要时的配置方法。

### 步骤 1：在 CC-Switch 中添加提供商
1. 进入 **OpenCode** 标签页。
2. 点击 **Add Provider**，填写：
   - **Name**: `Qwen3.8-27B`
   - **Base URL**: `http://localhost:13004/v1`
   - **API Key**: 任意值（本地服务不校验）
   - **Model**: `Qwen3.8-27B`
   - **API Format**: `OpenAI`。

### 步骤 2：激活配置
1. 将该提供商设为 **Current**。
2. CC-Switch 会自动配置 `OPENAI_BASE_URL` 和 `OPENAI_API_KEY`。
3. 直接运行 `opencode` 即可，无需额外修改配置。

---

## 5. 故障排除

| 错误现象 | 可能原因 | 解决方法 |
| :--- | :--- | :--- |
| **401 Unauthorized** | API Key 错误或未透传 | 检查 CC-Switch 配置中的 Key 是否正确，或 Agent 的 `settings.json` 是否指向了本地代理。 |
| **502 Bad Gateway / 400 Bad Request** | 协议不匹配 (如 Responses vs Chat) | 确认 Agent 是否通过代理访问。如果直连报错，请改为通过代理。 |
| **System message must be at the beginning** | 后端校验严格 | 确保 CC-Switch 开启 **"Strict OpenAI Format"** 或在 Agent 设置中开启严格的格式转换。 |
| **HTTP 500 Internal server error（Claude Code）** | 请求体含上游不支持的参数（如 `output_config.effort: high`） | 见 [6.1](#61-claude-code-持续报-500effort-参数不兼容) |
| **HTTP 400 Unexpected reasoning effort high（Codex）** | `config.toml` 中 `model_reasoning_effort` 取值上游不支持 | 见 [6.2](#62-codex-报-400unexpected-reasoning-effort-high) |

---

## 6. 实战案例：Qwen 上游 effort 参数不兼容（2026-10-22 排查记录）

**背景**：上游为本地 SGLang 服务（`Qwen3.8-27B-FP8`），经 CC-Switch 本地代理（`127.0.0.1:15721`）同时供 Claude Code 与 Codex 使用。上游对"推理力度"（effort）参数的支持不完整，两个 Agent 各踩了一个坑。

**上游 effort 兼容矩阵**（实测）：

| 端点 | low | medium | high | max | xhigh |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `/v1/messages`（Claude Code 走 Anthropic 协议） | ✅ | ✅ | ❌ 500 | ❌ 500 | ❌ 500 |
| `/v1/responses`（Codex 走 Responses 协议） | ✅ | ✅ | ❌ 400 | — | ✅（默认） |

> 排查要点：CC-Switch 日志（`~/.cc-switch/logs/cc-switch.log`）只显示"上游 HTTP 500/400"，看不出具体字段。用 curl 模拟请求逐字段二分定位即可（大 system prompt、tools、cache_control、thinking 等先全部排除，再逐个加回可疑字段）。

### 6.1 Claude Code 持续报 500（effort 参数不兼容）

**现象**：新会话从第一句话起就持续 500 并自动重试，cc-switch 日志刷 `上游 HTTP 500: Internal server error`。**不是模型名映射问题**（模型名不对报的是 400/404）。

**根因**：Claude Code 2.1.308 请求体带 `"output_config": {"effort": "high"}`，上游 SGLang 的 Anthropic 兼容端点解析到 `effort=high` 直接内部错误。

**解决（二选一）**：

1. **CC-Switch 请求体改写（推荐）**：编辑 Claude 供应商 → 请求体重写（body）填：
   ```json
   { "output_config": { "effort": "low" } }
   ```
   CC-Switch（v3.16.4+，实测 4.0.18 可用）对请求体做 JSON 深度合并，会把 `high` 覆盖为 `low`。注意：该功能**只能覆盖/新增字段，不能删除字段**。
2. **改 Claude Code 源头（当前采用）**：在供应商 env 里加 `CLAUDE_CODE_EFFORT_LEVEL=low`，让 Claude Code 从一开始就发 low effort。

**附带发现（同一次排查）**：
- 上游不支持**图片输入**（Qwen3.8-27B 无视觉能力），任何含 image block 的请求直接 500。不要让 Claude Code 读图片/粘贴截图；已污染的会话历史会反复重发图片，需开新会话。
- 上游实际输入上限是 **86449 tokens**（非标称 262144），长会话需及时 `/compact`。
- 代理下模型自报身份不可信：Claude Code 会把"我是 Opus 5"写进上下文让模型复述，真实模型以响应体 `model` 字段为准（此处为 Qwen3.8-27B）。

### 6.2 Codex 报 400（Unexpected reasoning effort high）

**现象**：
```
CC Switch local proxy failed while handling Codex endpoint /responses.
upstream_status: HTTP 400; cause: Unexpected reasoning effort high.
Supported types are xhigh (default), medium, and low.
```

**根因**：`~/.codex/config.toml` 里 `model_reasoning_effort = "high"`，而上游只认 `xhigh` / `medium` / `low`。

**解决**：编辑 `~/.codex/config.toml`：
```diff
- model_reasoning_effort = "high"
+ model_reasoning_effort = "medium"
```
想要更强推理可改为 `"xhigh"`（上游默认值）。修改后新开会话生效。

> 经验：同一上游服务不同协议端点（Anthropic Messages vs OpenAI Responses）对参数的校验规则可能完全不同，Claude 侧和 Codex 侧报错要分别验证，不能想当然套用。
