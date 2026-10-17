# CC-Switch Agent 配置指南

本文档整理了如何在 CC-Switch 中配置常用 AI Agent（Claude Code, OpenAI Codex, OpenCode）。

**假设条件：**
- **后端 API 地址**: `http://172.62.130.33:8080/v1`
- **API Key**: `sk-3ed...ed07`
- **CC-Switch 本地代理地址**: `http://127.0.0.1:15721/v1`

---

## 1. 核心概念

不同 Agent 使用的 API 协议格式不同，而你的后端服务器 (`172.62.130.33:8080`) 仅支持 **OpenAI Chat Completions** 标准。

- **Claude Code**: 使用 Anthropic Messages 格式。需要 CC-Switch 本地代理进行格式转换。
- **OpenAI Codex**: 使用 OpenAI Responses API 格式。如果后端不支持，也需要本地代理进行转换。
- **OpenCode**: 使用标准 OpenAI Chat Completions 格式。可以直连后端。

---

## 2. Claude Code 配置

**协议需求**: Anthropic Messages (需要代理转换)

### 步骤 1：在 CC-Switch 中添加提供商
1. 进入 **Claude** 标签页。
2. 点击 **Add Provider**，填写：
   - **Name**: `Qwen3.6-Claude`
   - **Base URL**: `http://172.62.130.33:8080/v1` (这里填真实后端地址，因为代理会自动转发)
   - **API Key**: `sk-3ed...ed07`
   - **Model**: `Qwen3.6-27B`
   - **API Format**: 确保选择 `OpenAI` (因为后端是 OpenAI 格式)。

### 步骤 2：设置代理路由
1. 在 **Settings** 中确保 **Local Proxy** 已开启。
2. 在 **Claude** 标签页，将刚才添加的提供商设为 **Current**。
3. **关键步骤**：打开 `C:\Users\Administrator\.claude\settings.json`，修改环境变量指向本地代理：
   ```json
   {
     "env": {
       "ANTHROPIC_BASE_URL": "http://127.0.0.1:15721/v1",
       "ANTHROPIC_AUTH_TOKEN": "sk-3ed...ed07",
       "CLAUDE_CODE_AUTO_MODE_SERVER": "0"
     },
     "model": "Qwen3.6-27B"
   }
   ```

---

## 3. OpenAI Codex 配置

**协议需求**: OpenAI Responses API (需要代理转换)
*注：如果你的后端 (`172.62.130.33`) 不支持 `/v1/responses`，必须使用代理转换。*

### 步骤 1：在 CC-Switch 中添加提供商
1. 进入 **Codex** 标签页。
2. 点击 **Add Provider**，填写：
   - **Name**: `Qwen3.6-Codex`
   - **Base URL**: `http://172.62.130.33:8080/v1`
   - **API Key**: `sk-3ed...ed07`
   - **Model**: `Qwen3.6-27B`
   - **API Format**: `OpenAI`。

### 步骤 2：修改 Codex 配置
1. 编辑 `C:\Users\Administrator\.codex\config.toml`。
2. 将 `base_url` 指向 CC-Switch 本地代理：
   ```toml
   model = "Qwen3.6-27B"
   model_provider = "custom"

   [model_providers]

   [model_providers.custom]
   name = "custom"
   wire_api = "responses"
   requires_openai_auth = true
   base_url = "http://127.0.0.1:15721/v1"
   ```
3. 确保终端环境已设置 `OPENAI_API_KEY`。

---

## 4. OpenCode 配置

**协议需求**: OpenAI Chat Completions (支持直连)

### 步骤 1：在 CC-Switch 中添加提供商
1. 进入 **OpenCode** 标签页。
2. 点击 **Add Provider**，填写：
   - **Name**: `Qwen3.6-OpenCode`
   - **Base URL**: `http://172.62.130.33:8080/v1`
   - **API Key**: `sk-3ed...ed07`
   - **Model**: `Qwen3.6-27B`
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
