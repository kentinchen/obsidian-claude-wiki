---
title: "tashfeenahmed/freellmapi: OpenAI-compatible proxy that stacks the free tiers of 16 LLM providers (~1.7B tokens/month) behind one /v1 endpoint — plus any custom OpenAI-compatible endpoint. Smart routing, automatic failover, encrypted keys. Personal experimentation only."
source: "https://github.com/tashfeenahmed/freellmapi"
author:
published:
created: 2026-07-02
description: "OpenAI-compatible proxy that stacks the free tiers of 16 LLM providers (~1.7B tokens/month) behind one /v1 endpoint — plus any custom OpenAI-compatible endpoint. Smart routing, automatic failover, encrypted keys. Personal experimentation only. - tashfeenahmed/freellmapi"
tags:
  - "clippings"
---
## FreeLLMAPI

**One OpenAI-compatible endpoint. 18 free LLM providers. 161 free models. ~1.7B tokens per month.**

Aggregate the free tiers from Google, Groq, Cerebras, NVIDIA, Mistral, OpenRouter, GitHub Models, Cohere, Cloudflare, HuggingFace, Z.ai (Zhipu), Ollama, Kilo, Pollinations, LLM7, OVH AI Endpoints, OpenCode Zen, and AI Horde, plus custom OpenAI-compatible chat, embedding, image, and audio endpoints, behind a single `/v1` API. Keys are stored encrypted. A router picks the best available model for each request, falls over to the next provider when one is rate-limited, and tracks per-key usage so you stay under every free-tier cap.

**[freellmapi.co](https://freellmapi.co/)** · browse all 161 free models on the live catalog

Your router updates its own model catalog. Free installs get each new model 30 days after it ships; **[Premium gets it the day it lands, and is 79 models ahead right now](https://freellmapi.co/?utm_source=github&utm_medium=readme#pricing)** ($19/yr, 30-day refund).

[![Fallback chain with per-provider token budget](https://github.com/tashfeenahmed/freellmapi/raw/main/repo-assets/fallback-chain.png)](https://github.com/tashfeenahmed/freellmapi/blob/main/repo-assets/fallback-chain.png)

---

## Contents

## Why this exists

Every serious AI lab now offers a free tier — a few million tokens a month, a few thousand requests a day. On its own each tier is a toy. Stacked together, they add up to roughly **1.7 billion tokens per month** of working inference capacity, across 160+ models from small-and-fast to reasonably capable.

The problem is that stacking them by hand is painful: eighteen different SDKs, eighteen different rate limits, eighteen places a request can fail. FreeLLMAPI collapses that into one OpenAI-compatible endpoint. Point any OpenAI client library at your local server, and it routes transparently across whichever providers you've added keys for.

And the free-tier landscape shifts weekly: providers launch models, retire them, and change quotas without notice. FreeLLMAPI tracks all of that for you. The router pulls a signed model catalog from [freellmapi.co](https://freellmapi.co/) on its own, so your install keeps up without a `git pull`. See [Premium (live catalog)](#premium-live-catalog) for how fast it keeps up.

## Supported providers

| [**Google**   Gemini 2.5 Flash · 3.x previews](https://ai.google.dev/) | [**Groq**   Llama 3.3, Llama 4, GPT-OSS, Qwen3](https://groq.com/) | [**Cerebras**   Qwen3 235B](https://cerebras.ai/) | [**OpenCode Zen**   DeepSeek V4 Flash · Nemotron (promo)](https://opencode.ai/zen) |
| --- | --- | --- | --- |
| [**Mistral**   Large 3 · Medium 3.5 · Codestral · Devstral](https://mistral.ai/) | [**OpenRouter**   21 free-tier models](https://openrouter.ai/) | [**GitHub Models**   GPT-4.1 · GPT-4o](https://github.com/marketplace/models) | [**Cloudflare**   Kimi K2 · GLM-4.7 · GPT-OSS · Granite 4](https://developers.cloudflare.com/workers-ai) |
| [**Cohere**   Command R+ · Command-A (trial)](https://cohere.com/) | [**Z.ai (Zhipu)**   GLM-4.5 · GLM-4.7 Flash](https://docs.z.ai/) | [**NVIDIA**   NIM · 40 RPM free (eval-only ToS)](https://build.nvidia.com/) | [**HuggingFace**   Router → DeepSeek V4 · Kimi K2.6 · Qwen3](https://huggingface.co/docs/inference-providers) |
| [**Ollama Cloud**   GLM-4.7 · Kimi K2 · gpt-oss · Qwen3](https://ollama.com/) | [**Kilo Gateway**   :free routes (anon ok)](https://kilo.ai/) | [**Pollinations**   GPT-OSS 20B (anon ok)](https://pollinations.ai/) | [**LLM7**   GPT-OSS · Llama 3.1 · GLM (anon ok)](https://llm7.io/) |
| [**OVH AI Endpoints**   Qwen3.5 397B · GPT-OSS · Llama 3.3 (anon ok)](https://endpoints.ai.cloud.ovh.net/) | [**AI Horde**   Community Llama · Gemma · Cydonia (anon ok, slow)](https://aihorde.net/) |  |  |

Plus a **custom** provider — point chat, embedding, image, or audio models at any OpenAI-compatible endpoint (llama.cpp, LM Studio, vLLM, a local Ollama, or a remote gateway) from the Keys page.

The full, always-current list lives at **[freellmapi.co/models](https://freellmapi.co/models.html)** with per-model rate limits, context windows, and free-token budgets.

## Features

- **OpenAI-compatible** — `POST /v1/chat/completions` and `GET /v1/models` work with the official OpenAI SDKs and any OpenAI-compatible client (LangChain, LlamaIndex, Continue, Hermes, etc.). Just change `base_url`.
- **Responses API** — `POST /v1/responses` (the wire format current Codex CLI versions require) is implemented as a translating shim over the same router, with full streaming events and tool calls.
- **Editor autocomplete** — `POST /v1/completions` translates legacy prompt/suffix requests into the same router, so VS Code ghost-text clients such as Continue can use FreeLLMAPI for inline suggestions.
- **Anthropic Messages API** — `POST /v1/messages` (plus `/v1/messages/count_tokens`) speaks Anthropic's wire format over the same router, so **Claude Code** and the official Anthropic SDKs run against your free pool. `GET /v1/models` is content-negotiated (Anthropic shape when the client sends `anthropic-version`, OpenAI shape otherwise), and Claude families (`opus` / `sonnet` / `haiku` / `default`) map to `auto` or a pinned model on the Keys page. See [Anthropic / Claude clients](#anthropic--claude-clients).
- **Image generation & text-to-speech** — `POST /v1/images/generations` and `POST /v1/audio/speech` route across the providers that serve media models, including custom OpenAI-compatible media endpoints. Browse and toggle them on the dashboard's **Models → Image / Audio** tabs.
- **Self-updating model catalog** — the router syncs a signed catalog from freellmapi.co twice a day: new models, quota changes, and provider quirk fixes land in your install automatically. See [Premium (live catalog)](#premium-live-catalog).
- **Streaming and non-streaming** — Server-Sent Events for `stream: true`, JSON response otherwise. Every provider adapter implements both.
- **Tool calling** — OpenAI-style `tools` / `tool_choice` requests are passed through, and assistant `tool_calls` + `tool` role follow-up messages round-trip across providers.
- **Embeddings** — `/v1/embeddings` with family-based routing, including custom OpenAI-compatible embedding endpoints: failover only ever happens between providers serving the *same* model (vectors from different models are incompatible), never across models. See [Embeddings](#embeddings).
- **Automatic fallover** — If the chosen provider returns a 429, 5xx, or times out, the router skips it, puts the key on a short cooldown, and retries on the next model in your fallback chain (up to 20 attempts).
- **Per-key rate tracking** — RPM, RPD, TPM, and TPD counters per `(platform, model, key)` so the router always picks a key that's under its caps.
- **Sticky sessions** — Multi-turn conversations keep talking to the same model for 30 minutes to avoid the hallucination spike that comes from mid-conversation model switches.
- **Encrypted key storage** — API keys are encrypted with AES-256-GCM before hitting SQLite; decryption happens in-memory just before a request.
- **Unified API key** — Clients authenticate to your proxy with a single `freellmapi-…` bearer token. You never expose upstream provider keys to your apps.
- **Dashboard login** — The admin UI and all `/api/*` routes are gated behind an email + password account (scrypt-hashed, session-token auth), set on first run. The `/v1` proxy keeps its own unified-key auth for apps.
- **Health checks** — Periodic probes mark keys as `healthy`, `rate_limited`, `invalid`, or `error` so the router skips dead ones automatically.
- **Admin dashboard** — React + Vite UI to manage keys, reorder the fallback chain, inspect analytics, and run prompts in a playground. Dark mode included.
- **Analytics** — Per-request logging with latency, token counts, success rate, and per-provider breakdowns.
- **Context handoff on model switch** — Optional. When a session falls over to a different model, injects one compact system message so the new model knows it is continuing an existing task. Disabled by default; enable with `FREELLMAPI_CONTEXT_HANDOFF=on_model_switch`. See [Context Handoff](#context-handoff).
- **Runs anywhere Node 20+ runs** — Windows, macOS, Linux servers, or a small ARM SBC (Raspberry Pi included). ~40 MB RSS at idle behind PM2 / systemd / whatever supervisor you prefer.

## Not yet supported

The scope is deliberately narrow. If a feature isn't on this list and isn't below, assume it isn't there yet.

- **Moderation** (`/v1/moderations`)
- **`n > 1`** (multiple completions per request)
- **Per-user billing / multi-tenant auth** — single-user by design

PRs that add any of these are very welcome. See [Contributing](#contributing).

## Quick start

**One-liner** (Docker required — sets up `~/freellmapi`, generates an encryption key, pulls the image, and starts the container):

```
curl -fsSL https://freellmapi.co/install.sh | bash
```

Prefer to read before you pipe to bash? [The script is here](https://freellmapi.co/install.sh). Re-running it is safe: your `.env` (and encryption key) is preserved and the container updates to `:latest`. Override the defaults with `FREELLMAPI_DIR`, `PORT`, or `HOST_BIND` env vars.

On Windows, the easiest path is the desktop **[`.exe` installer from Releases](https://github.com/tashfeenahmed/freellmapi/releases/latest)** (below); the Docker steps work in WSL or any bash shell.

**Or manually with Docker Compose.** It runs the API and dashboard together on port 3001 and persists SQLite in a named volume.

**Prerequisites:** Docker, Docker Compose, OpenSSL.

```
git clone https://github.com/tashfeenahmed/freellmapi.git
cd freellmapi

# Generate an encryption key for at-rest key storage
ENCRYPTION_KEY="$(openssl rand -hex 32)"
printf "ENCRYPTION_KEY=%s\nPORT=3001\n" "$ENCRYPTION_KEY" > .env

docker compose up -d
```

Open [http://localhost:3001](http://localhost:3001/), add your provider keys on the **Keys** page, reorder the **Fallback Chain** to taste, and grab your unified API key from the **Keys** page header. That unified key is what you point your OpenAI SDK at.

Your fresh install ships with the free catalog snapshot (82 models today) and keeps itself updated from there. Everything the live feed adds on top is listed at [freellmapi.co/models](https://freellmapi.co/models.html).

> **Reaching it from another machine?** By default the container is published only on `127.0.0.1`, so `http://<server-ip>:3001` won't load from another device (the page just hangs). To expose it on your LAN — e.g. a Raspberry Pi at `http://192.168.1.x:3001` — start it with `HOST_BIND=0.0.0.0`:
> 
> ```
> HOST_BIND=0.0.0.0 docker compose up -d
> ```
> 
> Only do this on a trusted network: the proxy is single-user and guarded only by the unified API key.

### Local development

**Prerequisites:** Node.js 20+, npm.

```
git clone https://github.com/tashfeenahmed/freellmapi.git
cd freellmapi
npm install
cp .env.example .env
ENCRYPTION_KEY="$(node -e 'console.log(require("crypto").randomBytes(32).toString("hex"))')"
printf "ENCRYPTION_KEY=%s\nPORT=3001\n" "$ENCRYPTION_KEY" > .env
npm run dev
```

`ENCRYPTION_KEY` is required for startup. The server only falls back to a database-stored development key when `DEV_MODE=true` and `NODE_ENV` is not `production`; do not use that fallback with real provider keys.

Request analytics are retained for 90 days or 100000 request rows by default, whichever limit prunes first. Set `REQUEST_ANALYTICS_RETENTION_DAYS=0` or `REQUEST_ANALYTICS_MAX_ROWS=0` in `.env` to disable either retention limit.

Open [http://localhost:5173](http://localhost:5173/) (the Vite dev UI), add your provider keys on the **Keys** page, reorder the **Fallback Chain** to taste, and grab your unified API key from the **Keys** page header. That unified key is what you point your OpenAI SDK at.

### Declarative startup config

For repeatable Docker/server installs, FreeLLMAPI can apply a JSON config on every boot. Set `FREEAPI_CONFIG_PATH=/path/to/freellmapi.config.json` or put the same JSON in `FREEAPI_CONFIG_JSON`. The config is idempotent: existing keys, custom providers, model edits, fallback rows, and routing settings are updated instead of duplicated.

```
{
  "keys": [
    { "platform": "groq", "key": "gsk_...", "label": "main" },
    { "platform": "google", "key": "AIza...", "enabled": true }
  ],
  "customProviders": [
    {
      "baseUrl": "http://host.docker.internal:11434/v1",
      "label": "Ollama",
      "models": [
        { "model": "llama3.1:8b", "displayName": "Local Llama", "supportsTools": true }
      ]
    }
  ],
  "models": [
    {
      "platform": "groq",
      "modelId": "llama-3.3-70b-versatile",
      "displayName": "Llama 3.3 70B",
      "supportsTools": true,
      "fallbackEnabled": true
    }
  ],
  "routing": { "strategy": "balanced" }
}
```

> **Reaching the dev UI from another device on your LAN?** Use `npm run dev:lan` — it passes `--host` through to Vite, which then prints a `Network: http://<your-ip>:5173` URL you can open from a phone or another machine. (Plain `npm run dev -- --host` does *not* work here: the root `dev` script is a `concurrently` wrapper, so the flag never reaches Vite.) API calls go through Vite's dev proxy, so no extra server config is needed.

For a production build without Docker:

```
npm run build
node server/dist/index.js     # server + dashboard both served on :3001
```

## Docker

FreeLLMAPI publishes a single production image that contains the Express server and the built React dashboard:

```
docker pull ghcr.io/tashfeenahmed/freellmapi:latest   # or pin a release, e.g. :v1.2.3
```

The image is multi-arch (`linux/amd64` + `linux/arm64`, so it runs on a Raspberry Pi). Published tags: `latest` (default branch), `v*.*.*` (git release tags), and `sha-<commit>`.

The included `docker-compose.yml` is the recommended install path:

```
docker compose up -d
docker compose logs -f freellmapi
```

By default the container's port is bound to `127.0.0.1` (localhost only). To reach the dashboard/API from another machine on your network, publish it on all interfaces with `HOST_BIND=0.0.0.0 docker compose up -d` — only on a trusted LAN, since the proxy is single-user.

SQLite data is stored in the `freellmapi-data` volume at `/app/server/data`. Keep the same `.env` `ENCRYPTION_KEY` and volume when upgrading, because provider keys are encrypted at rest. If your host only persists a specific directory, set `FREEAPI_DB_PATH=/that/path/freellmapi.db`.

On hosts with ephemeral disks, configure an encrypted backup target:

```
FREEAPI_DB_BACKUP_PATH=/app/server/data/freellmapi.db.backup
# or:
FREEAPI_DB_BACKUP_URL=https://example.com/freellmapi.db.backup
FREEAPI_DB_BACKUP_TOKEN=optional-bearer-token
FREEAPI_DB_BACKUP_KEY=64-char-hex-backup-key
FREEAPI_DB_BACKUP_INTERVAL_MS=300000
```

When the database file is missing at startup, FreeLLMAPI restores the backup before migrations run. While the server is running it uploads a fresh encrypted backup periodically. If `FREEAPI_DB_BACKUP_KEY` is omitted, the app uses `ENCRYPTION_KEY` for the backup envelope too.

More Docker operations and examples live in [docker/README.md](https://github.com/tashfeenahmed/freellmapi/blob/main/docker/README.md).

## Desktop app

A native menu-bar app lives in [`desktop/`](https://github.com/tashfeenahmed/freellmapi/blob/main/desktop): the entire router + dashboard running locally from your tray, with a glass popover showing live request stats.

[![FreeLLMAPI desktop app](https://github.com/tashfeenahmed/freellmapi/raw/main/repo-assets/desktop.png)](https://github.com/tashfeenahmed/freellmapi/blob/main/repo-assets/desktop.png)

**[Download from Releases](https://github.com/tashfeenahmed/freellmapi/releases/latest)** — the macOS `.dmg` and the Windows `.exe` installer are built and attached to every release by the [`desktop-release`](https://github.com/tashfeenahmed/freellmapi/blob/main/.github/workflows/desktop-release.yml) workflow. Or build it from this repo in a few minutes:

```
npm install
npm run desktop:dist        # macOS  → desktop/dist-electron/FreeLLMAPI-…-arm64.dmg
npm run desktop:dist:win    # Windows → "desktop/dist-electron/FreeLLMAPI Setup ….exe"
```

> Locally built apps are unsigned, so Windows SmartScreen may warn on first run ("More info" → "Run anyway"); the macOS build launches without Gatekeeper prompts. Full instructions in [desktop/README.md](https://github.com/tashfeenahmed/freellmapi/blob/main/desktop/README.md).

### Credentials and where your data lives

The desktop app has **no username or password to set up**. Unlike the server (which gates its dashboard behind an email + password account), the desktop build signs the dashboard in automatically with a hidden local account, so you're never prompted for credentials and never need one.

The only credential you need is your **unified API key** — the `freellmapi-…` token your OpenAI/Anthropic client points at. Get it from:

- the tray popover — click the tray icon, then **Copy Key**, or
- the dashboard **Keys** page header (tray → **Open Dashboard**).

You do not need to open or edit `freeapi.db` by hand.

Your settings and data live in one folder per OS (copy it to migrate to another machine or into a container):

| OS | Location |
| --- | --- |
| Windows | `%APPDATA%\FreeLLMAPI\` (e.g. `C:\Users\<you>\AppData\Roaming\FreeLLMAPI\`) |
| macOS | `~/Library/Application Support/FreeLLMAPI/` |
| Linux | `~/.config/FreeLLMAPI/` |

That folder holds `freeapi.db` (all keys, models, settings, encrypted at rest) and `config.json` (window/theme/port/LAN preferences). Copy both to move an install. For the server (non-desktop) deployment, the equivalent state is the `.env` file and the SQLite DB at `server/data/freeapi.db` (or wherever `FREEAPI_DB_PATH` points).

## Languages

The dashboard and the desktop tray ship in 6 languages. The UI auto-detects your browser/system language on first load and you can switch any time from the **⋯** menu; the choice is remembered.

| Language | Locale |
| --- | --- |
| English | `en` |
| 中文 (简体) | `zh-CN` |
| Français | `fr` |
| Español | `es` |
| Português (Brasil) | `pt-BR` |
| Italiano | `it` |

Translations live in [`client/src/i18n/locales/`](https://github.com/tashfeenahmed/freellmapi/blob/main/client/src/i18n/locales) as flat JSON files. To add a language, copy `en.json`, translate the values, and register the locale in `client/src/i18n/I18nProvider.tsx` (and `desktop/src/i18n.ts` for the tray strings) — PRs welcome.

## Works with OB-1 and other clients

FreeLLMAPI is the free tier for **[OB-1](https://github.com/Overbrilliant/ob-1)**: the OB-1 CLI can clone, configure, start, health-check, and wire this proxy into its settings automatically. A new OB-1 user can pick **Start free** and reach a working OpenAI-compatible endpoint before creating any hosted account.

It is also useful on its own. Any client that can target an OpenAI-compatible base URL can use FreeLLMAPI:

- **OB-1**: managed automatically by the CLI, including anonymous providers.
- **opencode, aider, Continue, LangChain, LlamaIndex**: set `base_url` to `http://localhost:3001/v1` and use the unified key from the dashboard.
- **Claude Code / Anthropic SDKs**: use the Anthropic-compatible `/v1/messages` surface and the `ANTHROPIC_AUTH_TOKEN` flow documented below.
- **Local GPU boxes**: add custom OpenAI-compatible endpoints for Ollama, llama.cpp, LM Studio, vLLM, or an internal gateway.

FreeLLMAPI is local-first and single-user by design. Your provider keys stay in your SQLite database, encrypted at rest, and requests go from your machine to the upstream providers you enabled.

## Premium (live catalog)

The router keeps its model catalog fresh on its own: it pulls a signed catalog from [freellmapi.co](https://freellmapi.co/) twice a day and applies new models, quota changes, and provider quirk fixes to your local DB. Your own enable/disable choices and custom providers are never touched, and every download is verified against a pinned Ed25519 key before it is applied.

The catalog comes in two feeds:

|  | Free | Premium |
| --- | --- | --- |
| Price | $0, forever | **$19/yr** or **$49 lifetime** |
| Models served today (July 2026) | 82 | **161** |
| New free models | 30 days after each one ships | **the day it ships** |
| Quota changes and quirk fixes | on the same 30-day trail | within 2-3 days |
| Activation | nothing to do | one key, all your devices |

The gap is not hypothetical. Right now the live feed is **79 models ahead** of free installs, including Kimi K2.7 Code, GLM-5.2, MiniMax M3, Qwen3.5 397B, and Nemotron 3 Ultra 550B with a 1M-token context window. Each of those reaches free installs about a month after it shipped; Premium routers were already serving them on day one. Browse exactly what you're missing at **[freellmapi.co/models](https://freellmapi.co/models.html)**.

Thirty days is a long time in this market. When a provider launches a strong new free model, quietly tightens a quota, or breaks a wire format, live-feed routers are patched within days while free installs wait for the model to age in. If you use your router every day, Premium is the difference between riding the free-tier wave and reading about it.

**[Go live at freellmapi.co →](https://freellmapi.co/?utm_source=github&utm_medium=readme#pricing)**

- $19/year or $49 once, lifetime. Stripe checkout, 30-day no-questions refund.
- One `fla_` key covers every router you run: desktop, homelab, Raspberry Pi.
- Activate in the dashboard under **Premium**; cancel or manage billing self-serve at [freellmapi.co/manage](https://freellmapi.co/manage).
- The router itself stays MIT-licensed and fully free, forever. Premium is only the live feed, and it's what funds the daily model testing and catalog maintenance that keep both tiers working.

The catalog server never sees your prompts, completions, or provider keys — the router stays fully self-hosted either way.

## Using the API

Any OpenAI-compatible client works (Anthropic / Claude clients too — see [Anthropic / Claude clients](#anthropic--claude-clients)). Examples:

**Python**

```
from openai import OpenAI

client = OpenAI(
    base_url="http://localhost:3001/v1",
    api_key="freellmapi-your-unified-key",
)

resp = client.chat.completions.create(
    model="auto",  # let the router pick; or specify e.g. "gemini-2.5-flash"
    messages=[{"role": "user", "content": "Summarise the fall of Rome in one sentence."}],
)
print(resp.choices[0].message.content)
print("Routed via:", resp.headers.get("x-routed-via"))
```

**curl**

```
curl http://localhost:3001/v1/chat/completions \
  -H "Authorization: Bearer freellmapi-your-unified-key" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "auto",
    "messages": [{"role": "user", "content": "hi"}]
  }'
```

**Streaming**

```
stream = client.chat.completions.create(
    model="auto",
    messages=[{"role": "user", "content": "Stream me a haiku about SQLite."}],
    stream=True,
)
for chunk in stream:
    print(chunk.choices[0].delta.content or "", end="", flush=True)
```

**VS Code ghost-text autocomplete (Continue)**

FreeLLMAPI exposes `/v1/completions` for editor autocomplete clients that send legacy OpenAI prompt/suffix requests. Example Continue config:

```
models:
  - name: FreeLLMAPI Autocomplete
    provider: openai
    model: auto
    apiBase: http://localhost:3001/v1
    apiKey: freellmapi-your-unified-key
    useLegacyCompletionsEndpoint: true
    roles:
      - autocomplete
```

**Tool calling**

Pass OpenAI-style `tools` and `tool_choice`; the assistant response round-trips back through the proxy exactly like the OpenAI API. Multi-step flows (assistant `tool_calls` → `tool` role follow-up → final answer) work across every provider the router can reach.

```
tools = [{
    "type": "function",
    "function": {
        "name": "get_weather",
        "description": "Get current weather for a city.",
        "parameters": {
            "type": "object",
            "properties": {"city": {"type": "string"}},
            "required": ["city"],
        },
    },
}]

# 1. Model asks for a tool call
first = client.chat.completions.create(
    model="auto",
    messages=[{"role": "user", "content": "What's the weather in Karachi?"}],
    tools=tools,
    tool_choice="required",
)
call = first.choices[0].message.tool_calls[0]

# 2. You execute the tool, feed the result back
final = client.chat.completions.create(
    model="auto",
    messages=[
        {"role": "user", "content": "What's the weather in Karachi?"},
        first.choices[0].message,
        {"role": "tool", "tool_call_id": call.id, "content": '{"temp_c": 32, "cond": "sunny"}'},
    ],
    tools=tools,
)
print(final.choices[0].message.content)
```

**Gemini Google Search grounding**

Google's models can ground their answers in live Google Search results. Since the OpenAI wire format has no way to express that, request a tool named `google_search` and the Google provider translates it into Gemini's native grounding tool. It can be sent on its own or alongside your normal function tools.

```
resp = client.chat.completions.create(
    model="gemini-2.5-flash",  # pin a Google model so the request routes there
    messages=[{"role": "user", "content": "Who won the F1 race this weekend?"}],
    tools=[{"type": "function", "function": {"name": "google_search", "parameters": {}}}],
)
print(resp.choices[0].message.content)
```

**Vision / image input**

Send images with the standard OpenAI `image_url` content blocks (base64 `data:` URLs or `http(s)` URLs). When a request contains an image, the router restricts itself to **vision-capable models** and ignores text-only ones. Vision models are tagged with a **Vision** badge on the Fallback Chain page; the current set includes Gemini (2.5 / 3.x), Llama 4 Scout/Maverick (Groq, NVIDIA), GLM-4.6V Flash (Z.ai), Nemotron Nano 12B VL (OpenRouter), and GitHub's GPT-4o / GPT-4.1.

```
resp = client.chat.completions.create(
    model="auto",  # auto-routes to a vision model
    messages=[{
        "role": "user",
        "content": [
            {"type": "text", "text": "What's in this image?"},
            {"type": "image_url", "image_url": {"url": "data:image/png;base64,<...>"}},
        ],
    }],
)
print(resp.choices[0].message.content)
```

If no vision-capable model is enabled in your Fallback Chain, an image request returns a clear `422` (`code: "no_vision_model"`) rather than silently dropping the image. (Image input on `/v1/responses` isn't supported yet — use `/v1/chat/completions`.)

Works with `stream=True` as well — you'll get `delta.tool_calls` chunks followed by a `finish_reason: "tool_calls"` close. Under the hood, OpenAI-compatible providers (Groq, Cerebras, Mistral, OpenRouter, GitHub Models, HuggingFace, Cloudflare, Cohere compat) get the request passed through; Gemini requests get translated into Google's `functionDeclarations` / `functionResponse` shape and the response is translated back.

Every response carries an `X-Routed-Via: <platform>/<model>` header so you can see which provider actually served each call. If a request fell over between providers, you'll also see `X-Fallback-Attempts: N`.

### Embeddings

`/v1/embeddings` is OpenAI-compatible, with one deliberate difference from chat routing: **failover never crosses models.** Vectors from different models live in incompatible spaces — silently switching models would corrupt any vector store built on top of the proxy. So embeddings route by **family** (one model identity + dimension), and failover only walks the providers serving that same family.

```
resp = client.embeddings.create(
    model="auto",          # default family; or a family name like "bge-m3"
    input=["the quick brown fox", "pack my box with five dozen liquor jugs"],
)
print(len(resp.data), "vectors of", len(resp.data[0].embedding), "dims")
```
```
curl http://localhost:3001/v1/embeddings \
  -H "Authorization: Bearer freellmapi-your-unified-key" \
  -H "Content-Type: application/json" \
  -d '{"model": "auto", "input": "hello world"}'
```

`model` accepts `auto` (the configured default family), a family name, or a provider-specific model id (which resolves to its family). Available families:

| Family (`model`) | Dims | Providers (failover order) |
| --- | --- | --- |
| `gemini-embedding-001` *(default)* | 3072 | Google |
| `text-embedding-3-large` | 3072 | GitHub Models |
| `text-embedding-3-small` | 1536 | GitHub Models |
| `embed-v4.0` | 1536 | Cohere |
| `bge-m3` | 1024 | Cloudflare → Hugging Face |
| `qwen3-embedding-0.6b` | 1024 | Cloudflare |
| `nv-embedqa-e5-v5` | 1024 | NVIDIA |
| `llama-nemotron-embed-1b-v2` | 2048 | NVIDIA |
| `llama-nemotron-embed-vl-1b-v2` | 2048 | NVIDIA → OpenRouter |
| `embeddinggemma-300m` | 768 | Cloudflare |

The default family, per-provider toggles, and priorities live on the dashboard's **Models → Embeddings** page. Pick your family once and stick with it for a given vector store — that's the whole point of the family model.

### Anthropic / Claude clients

FreeLLMAPI also speaks Anthropic's Messages API, so anything built for Claude — including **Claude Code** and the official Anthropic SDKs — can run against your free pool. Point the client at your server's **origin** (Anthropic clients append `/v1/messages` themselves) and authenticate with your unified key. Both `x-api-key` and `Authorization: Bearer` are accepted.

```
curl http://localhost:3001/v1/messages \
  -H "x-api-key: freellmapi-your-unified-key" \
  -H "anthropic-version: 2023-06-01" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "claude-sonnet-4-5",
    "max_tokens": 256,
    "messages": [{"role": "user", "content": "hi"}]
  }'
```

Claude model names map to your free pool on the **Keys → Anthropic** tab: each family (`default`, `opus`, `sonnet`, `haiku`) routes to `auto` (the router picks a free model) or a model you pin. `POST /v1/messages/count_tokens` and a content-negotiated `GET /v1/models` (Anthropic shape when `anthropic-version` is sent) are implemented too. Streaming, system prompts, tool use, and image input all translate across the same router as the OpenAI endpoints.

**Claude Code** — point it at your server and start it:

```
export ANTHROPIC_BASE_URL=http://localhost:3001
export ANTHROPIC_AUTH_TOKEN=freellmapi-your-unified-key   # NOT ANTHROPIC_API_KEY
claude
```

> Use `ANTHROPIC_AUTH_TOKEN` (sent as a Bearer token), **not** `ANTHROPIC_API_KEY` — Claude Code treats a set `ANTHROPIC_API_KEY` as a conflicting first-party credential and refuses to start.

## Screenshots

### Keys

Manage provider credentials and grab the unified API key your apps connect with. Each key shows a status dot and when it was last health-checked.

[![Keys page](https://github.com/tashfeenahmed/freellmapi/raw/main/repo-assets/keys.png)](https://github.com/tashfeenahmed/freellmapi/blob/main/repo-assets/keys.png)

### Playground

Send a chat completion through the router and see which provider served it, with the model ID and latency printed right on the message.

[![Playground page](https://github.com/tashfeenahmed/freellmapi/raw/main/repo-assets/playground.png)](https://github.com/tashfeenahmed/freellmapi/blob/main/repo-assets/playground.png)

### Analytics

Request volume, success rate, tokens in and out, average latency, and per-provider breakdowns over 24h / 7d / 30d windows.

[![Analytics page](https://github.com/tashfeenahmed/freellmapi/raw/main/repo-assets/analytics.png)](https://github.com/tashfeenahmed/freellmapi/blob/main/repo-assets/analytics.png)

## How it works

```
┌──────────────────┐   Bearer freellmapi-…   ┌─────────────────────────┐
│  OpenAI SDK /    │ ──────────────────────▶ │  Express proxy (:3001)  │
│  curl / any      │ ◀────────────────────── │  /v1/chat/completions   │
│  OpenAI client   │      streamed tokens    └────────────┬────────────┘
└──────────────────┘                                      │
                                                          ▼
                             ┌────────────────────────────────────────────────┐
                             │  Router                                        │
                             │   1. Pick highest-priority model that          │
                             │      (a) has a healthy key and                 │
                             │      (b) is under all its rate limits.         │
                             │   2. Decrypt key, call provider SDK.           │
                             │   3. On 429/5xx → cooldown + retry next model. │
                             └────────────────────────────────────────────────┘
                                          │
   ┌──────────────┬────────────┬──────────┴─────────┬─────────────┬──────────┐
   ▼              ▼            ▼                    ▼             ▼          ▼
 Google         Groq        Cerebras           OpenRouter        HF       …10 more
```

- **Router** (`server/src/services/router.ts`) — picks a model per request.
- **Rate-limit ledger** (`server/src/services/ratelimit.ts`) — in-memory RPM/RPD/TPM/TPD counters backed by SQLite, with cooldowns on 429s.
- **Provider adapters** (`server/src/providers/*.ts`) — one file per provider, implementing the `Provider` base class: `chatCompletion()` and `streamChatCompletion()`.
- **Health service** (`server/src/services/health.ts`) — periodic probe keeps key status fresh.
- **Dashboard** (`client/`) — React + Vite + shadcn/ui admin surface.
- **Storage** — SQLite (`better-sqlite3`) with AES-256-GCM envelope encryption for keys.

## Context Handoff

When FreeLLMAPI falls over to a different model mid-conversation (quota, rate limit, cooldown), the new model has no idea it is picking up someone else's task. **Context handoff** adds a single compact `system` message to the outbound request that tells the new model exactly that:

```
FreeLLMAPI context handoff:
You are taking over an ongoing conversation from another model (groq:llama-3 → google:gemini-flash).
Continue the user's task using the conversation context already provided in this request.
Do not restart the task, re-ask already answered setup questions, or discard prior tool results.
Respect the user's latest message as the highest-priority instruction.

Recent session summary:
User: …
Assistant: …
```

**Enable it in `.env`:**

```
FREELLMAPI_CONTEXT_HANDOFF=on_model_switch
```

**How it works:**

- Messages per session are stored in memory (TTL: 3 hours).
- Only injected when the selected model changes for a given session key.
- Not injected on the first request, on same-model continuations, or if a handoff message is already present.
- Session key: `X-Session-Id` header if present, otherwise SHA-1 of the first user message (same as sticky sessions).
- Storage is in-memory only. Nothing is written to disk or logged.

> **Important:** Context Handoff improves continuity for conversations routed through FreeLLMAPI. It cannot recover provider-internal hidden state or messages that were never sent to the proxy.

## Limitations

Stacking free tiers has real trade-offs. Be honest with yourself about them:

- **No frontier models.** The free-tier catalog tops out around Llama 3.3 70B, GLM-4.5, Qwen 3 Coder, and Gemini 2.5 Pro. You will not get GPT-5 or Claude Opus class reasoning through this. For hard problems, pay for a real API.
- **Intelligence degrades as the day progresses.** Your top-ranked models (usually Gemini 2.5 Pro, GPT-4o via GitHub Models) have the lowest daily caps. Once they hit their limits, the router falls down your priority chain to smaller/weaker models. Expect the effective intelligence of the endpoint to drop in the late hours of each day — then reset at UTC midnight.
- **Latency is highly variable.** Cerebras and Groq are extremely fast; others are not. You get whichever one is available.
- **Free tiers can change without notice.** Providers regularly tighten, loosen, or remove free tiers. When that happens you'll see 429s or auth errors until the catalog update reaches you — live-feed installs get those fixes within days, free installs on the 30-day trail. Re-seed scripts live in `server/src/scripts/`.
- **No SLA, by definition.** If you need reliability, use a paid provider with a contract.
- **Local-first.** There's no multi-tenant auth. Run this for yourself; don't expose it to the internet.

## Contributing

Contributors very welcome! See [CONTRIBUTING.md](https://github.com/tashfeenahmed/freellmapi/blob/main/CONTRIBUTING.md) for the dev loop, PR expectations, and the policy on AI/LLM-assisted contributions (short version: welcome, same quality bar as any other PR). Good first PRs:

- **Add a provider** — copy `server/src/providers/openai-compat.ts` as a template, wire it into `server/src/providers/index.ts`, seed its models in `server/src/db/index.ts`, add a test in `server/src/__tests__/providers/`.
- **Add an endpoint** — moderations and other OpenAI-compatible surfaces. The provider base class can grow new methods; adapters declare which they support.
- **Improve the router** — cost-aware routing (cheapest-healthy-fastest tradeoffs), better latency-weighted priority, regional pinning.
- **Dashboard polish** — charts on the Analytics page, key rotation UX, batch import of keys from `.env`.
- **Docs** — more examples, client library snippets for Go/Rust/etc., a deployment recipe for Docker or Fly.

**Development loop:**

```
npm install
npm run dev      # server on :3001, dashboard on :5173, both with HMR
npm test         # server vitest; also runs client tests if the workspace adds them
npm run build    # compile server and dashboard
```

PRs should include a test, keep the existing test suite green, and match the `.editorconfig` / tsconfig defaults already in the repo. See [CONTRIBUTING.md](https://github.com/tashfeenahmed/freellmapi/blob/main/CONTRIBUTING.md) for the full contributor workflow.

### Database Migrations

In local development, apply pending migrations with:

```
NODE_ENV=development npm run db:migration:up
```

See [CONTRIBUTING.md](https://github.com/tashfeenahmed/freellmapi/blob/main/CONTRIBUTING.md) for the full migration CLI and workflow.

### Contributors

[![@moaaz12-web](https://camo.githubusercontent.com/b908d81f53567875c977e5113d8c1543ce3a4f2e0ef3425c8d15403c25e21598/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f6d6f61617a31322d7765622e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/moaaz12-web) [![@lukasulc](https://camo.githubusercontent.com/8ffd6a0347bfcd4df989c77b3efd3f9816513e94ffd9820f48fc3a8bd2c2d139/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f6c756b6173756c632e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/lukasulc) [![@VinhPhamAI](https://camo.githubusercontent.com/9f8af5a85872fc1a1c58f373b864935bc1b484287ccbf1e3d84c9884ba57a88b/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f56696e685068616d41492e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/VinhPhamAI) [![@deadc](https://camo.githubusercontent.com/a46107fd4604602b85e7fea31caf48201938e4732ebf561b9823b74e49ce6386/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f64656164632e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/deadc) [![@zhangyu1324](https://camo.githubusercontent.com/a3e37f9ebee8e9516578eaea29a0787acfb1e0ea13bbc623c0850318d107b1f5/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f7a68616e677975313332342e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/zhangyu1324) [![@chongjiazhen](https://camo.githubusercontent.com/2c86652aaa8405861a40a7cb7bbf49ef4e9c3b03a0e404c5e5d9faa2a581f51b/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f63686f6e676a69617a68656e2e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/chongjiazhen) [![@vjsai](https://camo.githubusercontent.com/c47aa621f4e4402b688cffcaebef47473bdf2d8f92e924e200d23a91f6a26bb0/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f766a7361692e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/vjsai) [![@long2ice](https://camo.githubusercontent.com/3dcafd3d1f2cfcd92f9aeb0c3fe5b7093e36b68e225e53829b4a0ea14d1355f0/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f6c6f6e67326963652e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/long2ice) [![@sadesguy](https://camo.githubusercontent.com/a223f3f90566357d2847693e1692549177e5459c7cdbc6852228183419b34fce/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f73616465736775792e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/sadesguy) [![@hodlmybeer69-bit](https://camo.githubusercontent.com/a92c5269d712d9e65cd2c7630605d6b77ab45428e073475624a831f36e1f6e9e/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f686f646c6d796265657236392d6269742e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/hodlmybeer69-bit) [![@phoenixikkifullstack](https://camo.githubusercontent.com/49b6a9096ec45101fb990cb8d56d353e19a4130c23263871a2e11c912c922ae1/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f70686f656e6978696b6b6966756c6c737461636b2e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/phoenixikkifullstack) [![@jtbrennan-git](https://camo.githubusercontent.com/9e517ba274a613286a3cb683c593a28cd582a6aa7db7c1799d6da3ef6a2fd3a1/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f6a746272656e6e616e2d6769742e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/jtbrennan-git) [![@praveenkumarpranjal](https://camo.githubusercontent.com/7522e221d4bd2e6c0c0f477db1032df0c91c23450796ff954678c45877d77c69/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f7072617665656e6b756d61727072616e6a616c2e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/praveenkumarpranjal) [![@nordbyte](https://camo.githubusercontent.com/6f10d8b77aeaeeaccca522dd84115ec242c9daa8c638cabd31f34c22a1cea6ba/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f6e6f7264627974652e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/nordbyte) [![@mybropro](https://camo.githubusercontent.com/3dcc3b7c89f092a65a486488f54f64f902c9a44c760f03a6e07ef86a3824d0ce/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f6d7962726f70726f2e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/mybropro) [![@danscMax](https://camo.githubusercontent.com/8c5e87babe227f9361784ef9768985fdddc55d68c4a0712d099045fdb53fb51f/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f64616e73634d61782e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/danscMax) [![@jhash](https://camo.githubusercontent.com/4e74ce60274d218603707f9b1126a9777a0e660e46acc68a590073c5eaeb6d8b/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f6a686173682e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/jhash) [![@JammyJames1234](https://camo.githubusercontent.com/446fdad618aaf2f6b873b10780cae9223af25c4ba547eac5d0bc2e8efe4d0451/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f4a616d6d794a616d6573313233342e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/JammyJames1234) [![@Sumit4codes](https://camo.githubusercontent.com/ac050edfefeaf631bccbff1111c32f234242ee2a3a0ff2f4a75843d78cb0af2b/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f53756d697434636f6465732e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/Sumit4codes) [![@meliani](https://camo.githubusercontent.com/1a74de1b7414b9f87156db3138a801a10a663eb1eeb0baec40d739b9a4052505/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f6d656c69616e692e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/meliani) [![@thedavidweng](https://camo.githubusercontent.com/5ebf7def3c73cd0dff2ba8801b4fc6f26de6e1482ee0c9dd88b181f1ddc5ab6a/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f746865646176696477656e672e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/thedavidweng) [![@bharvey42](https://camo.githubusercontent.com/582d0939b581a096eaa4e2613a40c6741c55626962aee6dd5ef6c3d72d9c2360/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f6268617276657934322e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/bharvey42) [![@yuvrxj-afk](https://camo.githubusercontent.com/92f4b85333b65b940447d94842d9bf5723766793415b3a3a0d6219cfe3dcdda3/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f79757672786a2d61666b2e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/yuvrxj-afk) [![@Tushar49](https://camo.githubusercontent.com/9e090dd6ab6585a6ce818c000392f124975ebc66029158a49b3855c88923c617/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f54757368617234392e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/Tushar49) [![@nicyoong](https://camo.githubusercontent.com/647ad0b072d1fde05ab84e7637180a043c528f8fcfc07f78159a84f62d5b8177/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f6e6963796f6f6e672e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/nicyoong) [![@Aldo-f](https://camo.githubusercontent.com/c0fb8942a993260069673732b9cb42f49a43e5906829de45dd8c7eefc238a874/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f416c646f2d662e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/Aldo-f) [![@Tazrif-Raim](https://camo.githubusercontent.com/ded5f914cb8a4909fec70a0dbb510104a684d26b551c7fb312c1f916c04f31ac/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f54617a7269662d5261696d2e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/Tazrif-Raim) [![@m1nuzz](https://camo.githubusercontent.com/3949a7e1452e2cd81a623c245f57bc64a8e40e3af8a9590834da6722eb91177a/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f6d316e757a7a2e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/m1nuzz) [![@LoneRifle](https://camo.githubusercontent.com/43f68f762e96380ca67684f8f8a338529bc68efe1bbe1e63278a4a33efba9a2d/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f4c6f6e655269666c652e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/LoneRifle) [![@ita333](https://camo.githubusercontent.com/004de15c613dcdc4a6c3810ce6f47c746c221e7d1169a77377c95e6182221a7a/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f6974613333332e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/ita333) [![@barbotkonv](https://camo.githubusercontent.com/02fb2bf1504b9207eedfdc80d05530b3939fa68c005f3b2f07115111aa8ae350/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f626172626f746b6f6e762e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/barbotkonv) [![@Naster17](https://camo.githubusercontent.com/032c9c52c2a48528d3aeeec5cd1f3440b2b08b3ab016c9607aa5fff060a379f2/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f4e617374657231372e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/Naster17) [![@StealthTensor](https://camo.githubusercontent.com/eaf88d5b7085ace360c730836c726dcf97cc88619c1337e9371cac1acfa674cb/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f537465616c746854656e736f722e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/StealthTensor) [![@EmranAhmed](https://camo.githubusercontent.com/81f74d09a243947e3c21ecab569c324e54d3350949ee48078cc66aad54931b49/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f456d72616e41686d65642e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/EmranAhmed) [![@itsfuad](https://camo.githubusercontent.com/cc681da7f103879147cba654cdf1c92704dc9eac465f3e9132e68e3284802573/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f697473667561642e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/itsfuad) [![@RobinHoodO](https://camo.githubusercontent.com/4346afe843f433cc21a302a91def065f434fd40cb38757b2209a5f6e79dda504/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f526f62696e486f6f644f2e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/RobinHoodO) [![@hmm183](https://camo.githubusercontent.com/82341abe0fc190986d30fa30c8efe93c3c312a74d3000d5d4c7c3f713ac8dedf/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f686d6d3138332e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/hmm183) [![@duemilionidieuro-bot](https://camo.githubusercontent.com/3881827ea70de3d7fb3f08b6d5e916061eb15616a0ac3984734a6ab4203f1d67/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f6475656d696c696f6e6964696575726f2d626f742e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/duemilionidieuro-bot) [![@hjhhoni](https://camo.githubusercontent.com/5380b3f71fc222f01d534fa1e82d37114604b9f598ba46dd104513938e3cf227/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f686a68686f6e692e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/hjhhoni) [![@immanuelsavio](https://camo.githubusercontent.com/e86cf33d571f9a195fcdf044edf0bea5625a175a203f3121bc13c12d2ac4414b/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f696d6d616e75656c736176696f2e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/immanuelsavio) [![@Slyker](https://camo.githubusercontent.com/ab4e31dc6e9212a0cd46fa77caf091356384bfbad85acbe0413e55feb5c5ea41/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f536c796b65722e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/Slyker) [![@wells1013](https://camo.githubusercontent.com/3c92f4e07c6fec79a73f4b171bf979d0d4b69ded50b6bb0a8b4e91683e56e975/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f77656c6c73313031332e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/wells1013) [![@evgkrsk](https://camo.githubusercontent.com/a05f640a0ae4c81c82b41539d66036ddc028ba82b9d7ea1a7214d23090c933f1/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f6576676b72736b2e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/evgkrsk) [![@aaronjmars](https://camo.githubusercontent.com/594e27a20a156ab479a29788c70b1870ba963e9b02d79b26ed007fe73ea04118/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f6161726f6e6a6d6172732e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/aaronjmars) [![@Robs87](https://camo.githubusercontent.com/bb0cc9a2ad62b40a44e5625a02aa0665a2ed4798189e90f31756e5470a4e3441/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f526f627338372e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/Robs87) [![@dashitongzhi](https://camo.githubusercontent.com/f291499eb23b44833fdac76ccb1cf27f2cf8ab507ada08dd88c3549b15ff6cc8/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f6461736869746f6e677a68692e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/dashitongzhi) [![@QingJ01](https://camo.githubusercontent.com/0239f8a07768e2508205cd7620d758e79d114479ec29f4ecc577c3fec8d35604/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f51696e674a30312e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/QingJ01) [![@3215](https://camo.githubusercontent.com/54b319dfdfc8113bd65e4e42957ea30223e83e9956ef590634fcc00c5ac3ca07/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f333231352e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/3215) [![@saifulaiub123](https://camo.githubusercontent.com/c0eb5a93b117a7a22b7bf2504801fb504ee11b6b35ff8b2c157d32148cd53b9d/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f73616966756c616975623132332e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/saifulaiub123) [![@PietFourie](https://camo.githubusercontent.com/dcc0e7164e7197678ed63ff115a58c4345966a8077762df6afe269a51d8aa6f6/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f50696574466f757269652e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/PietFourie) [![@mhmdkrmabd](https://camo.githubusercontent.com/dfb0f446cb1fb1bf5a8798b572f62954573012864dc130824b0a33091420d7a4/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f6d686d646b726d6162642e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/mhmdkrmabd) [![@DemeulemeesterxMaxime](https://camo.githubusercontent.com/c3cccb2e61761781836a5530906e48414fba0be5d72d1bbe7ecf8ad8f3d33bb6/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f44656d65756c656d656573746572784d6178696d652e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/DemeulemeesterxMaxime) [![@HoodBlah](https://camo.githubusercontent.com/01a927cbbca9584a1721d5b67c9dbed03e2ba2df4cb97ab269c0f4009c9e630e/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f486f6f64426c61682e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/HoodBlah) [![@SeanPedersen](https://camo.githubusercontent.com/cd761dbff650e3a1b15f0416a7369b291887242e8b53e2f11cc022257e10b5e7/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f5365616e506564657273656e2e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/SeanPedersen) [![@andersmmg](https://camo.githubusercontent.com/b2d2579cc3139edbfa24df53a7cec95ab462a0efda565eb6beadcae8a17173bb/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f616e646572736d6d672e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/andersmmg) [![@chirag127](https://camo.githubusercontent.com/36481c45c973aed9f24293da5c2e373d2303d37f6d7d7f9b75f7705a6f358b53/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f6368697261673132372e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/chirag127) [![@jasnoorgill](https://camo.githubusercontent.com/41552e97533651537fc8f0d561852d0fb301ff95d81a66af5e8bc8164549003b/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f6a61736e6f6f7267696c6c2e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/jasnoorgill) [![@allababbot](https://camo.githubusercontent.com/f9d6ca43f5b4b201e0818e0f8014a14727d74c52856a468da82711538959f4db/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f616c6c61626162626f742e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/allababbot) [![@johan-droid](https://camo.githubusercontent.com/ec40f93961d9f37c204c6aa9ae6d308c7d28ca9d888ba9c931476edb3dc220e8/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f6a6f68616e2d64726f69642e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/johan-droid) [![@redenfire](https://camo.githubusercontent.com/8f39230d9b35f6a5d4d2621a92f519b5ebb6118e0e84cae3f4b666609898178d/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f726564656e666972652e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/redenfire) [![@itzpingcat](https://camo.githubusercontent.com/f57845dd84a997e965a89d0ad4a385b9a20371d1e372aa0d2b9a197ee0a2b2ab/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f69747a70696e676361742e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/itzpingcat) [![@kairwang01](https://camo.githubusercontent.com/019960b49fe70eecad71b2115e61b60c5e967265c7c6e562c82783b1f88b54ea/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f6b61697277616e6730312e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/kairwang01) [![@gongjurenzhangwei](https://camo.githubusercontent.com/265fa611f16009c0585fde94efe12baf72503f010118ebe192ea0b40353a244e/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f676f6e676a7572656e7a68616e677765692e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/gongjurenzhangwei) [![@jsonring](https://camo.githubusercontent.com/0d7b2101d3a9fd7aeb1874ad8975ea8c3d6fcf95a44888857932028383091ed4/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f6a736f6e72696e672e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/jsonring) [![@1029734570](https://camo.githubusercontent.com/5680f7b3e5a4e5ba7fb212e78b739f5943b9f3708d511faeffb253b46864205e/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f313032393733343537302e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/1029734570) [![@86TheCactus](https://camo.githubusercontent.com/df578965f0fc0ec2d2cee5ba3139cb01e8f4316f69ee8dde6f04507908a1dd04/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f38365468654361637475732e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/86TheCactus) [![@AmiroKD](https://camo.githubusercontent.com/53456e81c4ec9bfe36bfc889f2e6ac31454e164eba106b4857005fa187b4fb50/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f416d69726f4b442e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/AmiroKD) [![@ecryptomillionaire-dev](https://camo.githubusercontent.com/67a17c9d0fff2a41821f0a79fcc95ec502957bfae54a1f03805711a976952c59/68747470733a2f2f696d616765732e7765736572762e6e6c2f3f75726c3d6769746875622e636f6d2f6563727970746f6d696c6c696f6e616972652d6465762e706e6726773d363026683d3630266669743d636f766572266d61736b3d636972636c65)](https://github.com/ecryptomillionaire-dev)

A self-hosted, single-user, personal-use setup was re-reviewed against each provider's ToS (May 2026). Summary:

| Provider | Verdict | Notes |
| --- | --- | --- |
| Google Gemini | ⚠️  Caution | March 2026 ToS narrows scope to *"professional or business purposes, not for consumer use"* — a self-hosted developer proxy is still defensible, but the clause is new. |
| Groq | ✅ Likely OK | GroqCloud Services Agreement permits Customer Application integration. |
| Cerebras | ✅ Likely OK | Permitted; explicitly forbids selling/transferring API keys. |
| Mistral | ✅ Likely OK | APIs allowed for personal/internal business use. |
| OpenRouter | ✅ Likely OK | April 2026 ToS sharpens the no-resale / no-competing-service clause; private single-user proxy still fine. |
| Cloudflare Workers AI | ⚠️  Ambiguous | No anti-proxy clause; covered by general Self-Serve Subscription Agreement. |
| NVIDIA NIM | ⚠️  Caution | Trial ToS §1.2 / §1.4: *"evaluation only, not production."* Free access is a recurring 40 RPM rate limit (the 2025 credit system was discontinued), but the evaluation-only scope stands. |
| GitHub Models | ⚠️  Caution | Free tier explicitly scoped to *"experimentation"* and *"prototyping."* |
| Cohere | ❌ Avoid | Terms §14 still forbids *"personal, family or household purposes."* |
| Zhipu (open.bigmodel.cn) | ✅ Likely OK | Personal/non-commercial research carve-out still in the platform docs. |
| Z.ai (api.z.ai) | ⚠️  Caution | New row — Singapore entity (distinct from Zhipu CN). §III.3(l) anti-traffic-redirect clause could plausibly be read against a proxy; no explicit personal-use carve-out. |
| Ollama Cloud | ✅ Likely OK | New row — Free plan permits cloud-model access (1 concurrent, 5-hour session caps). No anti-proxy / anti-resale clauses found. *(Integration tracked in #14.)* |
| OVH AI Endpoints | ✅ Likely OK | New row (June 2026) — anonymous access is officially documented (2 req/min per IP per model). OVH reserves the right to introduce token/consumption caps. |
| AI Horde | ✅ Likely OK | New row (June 2026) — a free, community-powered commons run by the Haidra non-profit; anonymous use is officially supported (key `0000000000`, lowest queue priority). No anti-proxy / anti-resale clause. The OpenAI proxy is a pilot and may be restricted by usage. *(Integration #345.)* |

Rules of thumb that keep most providers happy: **one account per provider**, **no reselling**, **no sharing your endpoint with other humans**, **don't hammer a free tier as a paid production backend**. This is informational, not legal advice — read each provider's ToS and make your own call.

Removed since the April 2026 review: Hugging Face, Moonshot, and MiniMax direct integrations were dropped from the catalog (HF — tool-call format issues; Moonshot — moved to paid only; MiniMax — superseded by the OpenRouter `minimax/minimax-m2.5:free` route).

## Disclaimer

**This project is for personal experimentation and learning, not production.** Free tiers exist so developers can prototype against them; they aren't a stable, supported inference substrate and shouldn't be treated as one. If you build something real on top of FreeLLMAPI, swap in a paid API before you ship. Your relationship with each upstream provider is governed by the terms you accepted when you created your account — those terms still apply when the traffic is proxied through this project, and you're responsible for complying with them.

## Star History

[![Star History Chart](https://camo.githubusercontent.com/bd61bfaa40622778466aae6c7355020817337411eed4d8391f66140c38d4b781/68747470733a2f2f6170692e737461722d686973746f72792e636f6d2f63686172743f7265706f733d746173686665656e61686d65642f667265656c6c6d61706926747970653d64617465266c6567656e643d746f702d6c656674)](https://www.star-history.com/?repos=tashfeenahmed%2Ffreellmapi&type=date&legend=top-left)

## License

[MIT](https://github.com/tashfeenahmed/freellmapi/blob/main/LICENSE)