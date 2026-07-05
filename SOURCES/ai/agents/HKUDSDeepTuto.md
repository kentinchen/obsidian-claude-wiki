---
title: "HKUDS/DeepTutor: \"DeepTutor: Agent-Native Personalized Learning Assistant\""
source: "https://github.com/HKUDS/DeepTutor"
author:
published:
created: 2026-04-16
description: "\"DeepTutor: Agent-Native Personalized Learning Assistant\" - HKUDS/DeepTutor"
tags:
  - "clippings"
---
[![DeepTutor](https://github.com/HKUDS/DeepTutor/raw/main/assets/logo-ver2.png)](https://github.com/HKUDS/DeepTutor/blob/main/assets/logo-ver2.png)

## DeepTutor: Agent-Native Personalized Tutoring

[![HKUDS%2FDeepTutor | Trendshift](https://camo.githubusercontent.com/4478c222a38c05ec704e04c89a2980cbd0eaf01bce2d6a398760e2d0ec6c72b8/68747470733a2f2f7472656e6473686966742e696f2f6170692f62616467652f7265706f7369746f726965732f3137303939)](https://trendshift.io/repositories/17099)

[Features](#-key-features) · [Get Started](#-get-started) · [Explore](#-explore-deeptutor) · [TutorBot](#-tutorbot--persistent-autonomous-ai-tutors) · [CLI](#%EF%B8%8F-deeptutor-cli--agent-native-interface) · [Community](#-community--ecosystem)

[🇨🇳 中文](https://github.com/HKUDS/DeepTutor/blob/main/assets/README/README_CN.md) · [🇯🇵 日本語](https://github.com/HKUDS/DeepTutor/blob/main/assets/README/README_JA.md) · [🇪🇸 Español](https://github.com/HKUDS/DeepTutor/blob/main/assets/README/README_ES.md) · [🇫🇷 Français](https://github.com/HKUDS/DeepTutor/blob/main/assets/README/README_FR.md) · [🇸🇦 العربية](https://github.com/HKUDS/DeepTutor/blob/main/assets/README/README_AR.md) · [🇷🇺 Русский](https://github.com/HKUDS/DeepTutor/blob/main/assets/README/README_RU.md) · [🇮🇳 हिन्दी](https://github.com/HKUDS/DeepTutor/blob/main/assets/README/README_HI.md) · [🇵🇹 Português](https://github.com/HKUDS/DeepTutor/blob/main/assets/README/README_PT.md)

---

### 📦 Releases

> **\[2026.4.15\]** [v1.1.0](https://github.com/HKUDS/DeepTutor/releases/tag/v1.1.0) — LaTeX block math parsing overhaul, LLM diagnostic probe agents.yaml configuration, extra headers forwarding in LLM factory, SaveToNotebookModal UUID fix, Docker + local LLM guidance, and expanded test suite.

> **\[2026.4.14\]** [v1.1.0-beta](https://github.com/HKUDS/DeepTutor/releases/tag/v1.1.0-beta) — URL-based chat routing with bookmarkable sessions, Snow theme, WebSocket heartbeat & auto-reconnect with resume, ChatComposer performance optimization, embedding provider registry overhaul, Serper search provider, streaming idle timeout, and expanded test suite.

> **\[2026.4.13\]** [v1.0.3](https://github.com/HKUDS/DeepTutor/releases/tag/v1.0.3) — Question Notebook for unified quiz review with bookmarks & categories, Mermaid diagram support in Visualize, embedding model mismatch detection, system message merging for Qwen/vLLM compatibility, LM Studio & llama.cpp provider support, and Glass theme.

> **\[2026.4.11\]** [v1.0.2](https://github.com/HKUDS/DeepTutor/releases/tag/v1.0.2) — Search consolidation simplification with SearXNG fallback, provider switch fix, explicit runtime config in test runner, and frontend resource leak fixes.

> **\[2026.4.10\]** [v1.0.1](https://github.com/HKUDS/DeepTutor/releases/tag/v1.0.1) — New Visualize capability with Chart.js/SVG rendering pipeline, quiz duplicate prevention with generation history, o4-mini model support, and server logging improvements.

> **\[2026.4.10\]** [v1.0.0-beta.4](https://github.com/HKUDS/DeepTutor/releases/tag/v1.0.0-beta.4) — Embedding progress tracking with HTTP 429 rate limit retry, cross-platform start tour dependency management, and case-insensitive MIME validation fix.

> **\[2026.4.8\]** [v1.0.0-beta.3](https://github.com/HKUDS/DeepTutor/releases/tag/v1.0.0-beta.3) — Remove litellm dependency with native OpenAI/Anthropic SDK providers, Windows Math Animator compatibility, robust JSON parsing for LLM outputs, Guided Learning KaTeX & navigation fixes, and full i18n coverage for Chinese.

> **\[2026.4.7\]** [v1.0.0-beta.2](https://github.com/HKUDS/DeepTutor/releases/tag/v1.0.0-beta.2) — Runtime cache invalidation for hot settings reload, MinerU nested output support, mimic WebSocket fix, Python 3.11+ minimum, and CI improvements.

> **\[2026.4.4\]** [v1.0.0-beta.1](https://github.com/HKUDS/DeepTutor/releases/tag/v1.0.0-beta.1) — Agent-native architecture rewrite (～200k lines) with two-layer plugin model (Tools + Capabilities), CLI & SDK entry points, TutorBot multi-channel bot agent, Co-Writer, Guided Learning, and persistent memory.

**Past releases**

> **\[2026.1.23\]** [v0.6.0](https://github.com/HKUDS/DeepTutor/releases/tag/v0.6.0) — Session persistence, incremental document upload, flexible RAG pipeline import, and full Chinese localization.

> **\[2026.1.18\]** [v0.5.2](https://github.com/HKUDS/DeepTutor/releases/tag/v0.5.2) — Docling support for RAG-Anything, logging system optimization, and bug fixes.

> **\[2026.1.15\]** [v0.5.0](https://github.com/HKUDS/DeepTutor/releases/tag/v0.5.0) — Unified service configuration, RAG pipeline selection per knowledge base, question generation overhaul, and sidebar customization.

> **\[2026.1.9\]** [v0.4.0](https://github.com/HKUDS/DeepTutor/releases/tag/v0.4.0) — Multi-provider LLM & embedding support, new home page, RAG module decoupling, and environment variable refactor.

> **\[2026.1.5\]** [v0.3.0](https://github.com/HKUDS/DeepTutor/releases/tag/v0.3.0) — Unified PromptManager architecture, GitHub Actions CI/CD, and pre-built Docker images on GHCR.

> **\[2026.1.2\]** [v0.2.0](https://github.com/HKUDS/DeepTutor/releases/tag/v0.2.0) — Docker deployment, Next.js 16 & React 19 upgrade, WebSocket security hardening, and critical vulnerability fixes.

### 📰 News

> **\[2026.4.4\]** Long time no see! ✨ DeepTutor v1.0.0 is finally here — an agent-native evolution featuring a ground-up architecture rewrite, TutorBot, and flexible mode switching under the Apache-2.0 license. A new chapter begins, and our story continues!

> **\[2026.2.6\]** 🚀 We've reached 10k stars in just 39 days! A huge thank you to our incredible community for the support!

> **\[2026.1.1\]** Happy New Year! Join our [Discord](https://discord.gg/eRsjPgMU4t), [WeChat](https://github.com/HKUDS/DeepTutor/issues/78), or [Discussions](https://github.com/HKUDS/DeepTutor/discussions) — let's shape the future of DeepTutor together!

> **\[2025.12.29\]** DeepTutor is officially released!

## ✨ Key Features

- **Unified Chat Workspace** — Five modes, one thread. Chat, Deep Solve, Quiz Generation, Deep Research, and Math Animator share the same context — start a conversation, escalate to multi-agent problem solving, generate quizzes, then deep-dive into research, all without losing a single message.
- **Personal TutorBots** — Not chatbots — autonomous tutors. Each TutorBot lives in its own workspace with its own memory, personality, and skill set. They set reminders, learn new abilities, and evolve as you grow. Powered by [nanobot](https://github.com/HKUDS/nanobot).
- **AI Co-Writer** — A Markdown editor where AI is a first-class collaborator. Select text, rewrite, expand, or summarize — drawing from your knowledge base and the web. Every piece feeds back into your learning ecosystem.
- **Guided Learning** — Turn your materials into structured, visual learning journeys. DeepTutor designs multi-step plans, generates interactive pages for each knowledge point, and lets you discuss alongside each step.
- **Knowledge Hub** — Upload PDFs, Markdown, and text files to build RAG-ready knowledge bases. Organize insights across sessions in color-coded notebooks. Your documents don't just sit there — they actively power every conversation.
- **Persistent Memory** — DeepTutor builds a living profile of you: what you've studied, how you learn, and where you're heading. Shared across all features and TutorBots, it gets sharper with every interaction.
- **Agent-Native CLI** — Every capability, knowledge base, session, and TutorBot is one command away. Rich terminal output for humans, structured JSON for AI agents and pipelines. Hand DeepTutor a [`SKILL.md`](https://github.com/HKUDS/DeepTutor/blob/main/SKILL.md) and your agents can operate it autonomously.

---

## 🚀 Get Started

A **single interactive script** that walks you through everything: dependency installation, environment configuration, live connection testing, and launch. No manual `.env` editing needed.

```
git clone https://github.com/HKUDS/DeepTutor.git
cd DeepTutor

# Create a Python environment
conda create -n deeptutor python=3.11 && conda activate deeptutor
# Or: python -m venv .venv && source .venv/bin/activate

# Launch the guided tour
python scripts/start_tour.py
```

The tour asks how you'd like to use DeepTutor:

- **Web mode** (recommended) — Picks a dependency profile, installs everything (pip + npm), then spins up a temporary server and opens the **Settings** page in your browser. A four-step guided tour walks you through LLM, Embedding, and Search provider setup with live connection testing. Once complete, DeepTutor restarts automatically with your configuration.
- **CLI mode** — A fully interactive terminal flow: choose a dependency profile, install dependencies, configure providers, verify connections, and apply — all without leaving the shell.

Either way, you end up with a running DeepTutor at [http://localhost:3782](http://localhost:3782/).

### Option B — Manual Local Install

If you prefer full control, install and configure everything yourself.

**1\. Install dependencies**

```
git clone https://github.com/HKUDS/DeepTutor.git
cd DeepTutor

conda create -n deeptutor python=3.11 && conda activate deeptutor
pip install -e ".[server]"

# Frontend
cd web && npm install && cd ..
```

**2\. Configure environment**

```
cp .env.example .env
```

Edit `.env` and fill in at least the required fields:

```
# LLM (Required)
LLM_BINDING=openai
LLM_MODEL=gpt-4o-mini
LLM_API_KEY=sk-xxx
LLM_HOST=https://api.openai.com/v1

# Embedding (Required for Knowledge Base)
EMBEDDING_BINDING=openai
EMBEDDING_MODEL=text-embedding-3-large
EMBEDDING_API_KEY=sk-xxx
EMBEDDING_HOST=https://api.openai.com/v1
EMBEDDING_DIMENSION=3072
```
**Supported LLM Providers**

| Provider | Binding | Default Base URL |
| --- | --- | --- |
| AiHubMix | `aihubmix` | `https://aihubmix.com/v1` |
| Anthropic | `anthropic` | `https://api.anthropic.com/v1` |
| Azure OpenAI | `azure_openai` | — |
| BytePlus | `byteplus` | `https://ark.ap-southeast.bytepluses.com/api/v3` |
| BytePlus Coding Plan | `byteplus_coding_plan` | `https://ark.ap-southeast.bytepluses.com/api/coding/v3` |
| Custom (OpenAI-compat) | `custom` | — |
| DashScope (Qwen) | `dashscope` | `https://dashscope.aliyuncs.com/compatible-mode/v1` |
| DeepSeek | `deepseek` | `https://api.deepseek.com` |
| Gemini | `gemini` | `https://generativelanguage.googleapis.com/v1beta/openai/` |
| GitHub Copilot | `github_copilot` | `https://api.githubcopilot.com` |
| Groq | `groq` | `https://api.groq.com/openai/v1` |
| llama.cpp | `llama_cpp` | `http://localhost:8080/v1` |
| LM Studio | `lm_studio` | `http://localhost:1234/v1` |
| MiniMax | `minimax` | `https://api.minimax.io/v1` |
| Mistral | `mistral` | `https://api.mistral.ai/v1` |
| Moonshot (Kimi) | `moonshot` | `https://api.moonshot.ai/v1` |
| Ollama | `ollama` | `http://localhost:11434/v1` |
| OpenAI | `openai` | `https://api.openai.com/v1` |
| OpenAI Codex | `openai_codex` | `https://chatgpt.com/backend-api` |
| OpenRouter | `openrouter` | `https://openrouter.ai/api/v1` |
| OpenVINO Model Server | `ovms` | `http://localhost:8000/v3` |
| Qianfan (Ernie) | `qianfan` | `https://qianfan.baidubce.com/v2` |
| SiliconFlow | `siliconflow` | `https://api.siliconflow.cn/v1` |
| Step Fun | `stepfun` | `https://api.stepfun.com/v1` |
| vLLM | `vllm` | `http://localhost:8000/v1` |
| VolcEngine | `volcengine` | `https://ark.cn-beijing.volces.com/api/v3` |
| VolcEngine Coding Plan | `volcengine_coding_plan` | `https://ark.cn-beijing.volces.com/api/coding/v3` |
| Xiaomi MIMO | `xiaomi_mimo` | `https://api.xiaomimimo.com/v1` |
| Zhipu AI (GLM) | `zhipu` | `https://open.bigmodel.cn/api/paas/v4` |

**Supported Embedding Providers**

| Provider | Binding | Model Example | Default Dim |
| --- | --- | --- | --- |
| OpenAI | `openai` | `text-embedding-3-large` | 3072 |
| Azure OpenAI | `azure_openai` | deployment name | — |
| Cohere | `cohere` | `embed-v4.0` | 1024 |
| Jina | `jina` | `jina-embeddings-v3` | 1024 |
| Ollama | `ollama` | `nomic-embed-text` | 768 |
| vLLM / LM Studio | `vllm` | Any embedding model | — |
| Any OpenAI-compatible | `custom` | — | — |

OpenAI-compatible providers (DashScope, SiliconFlow, etc.) work via the `custom` or `openai` binding.

**Supported Web Search Providers**

| Provider | Env Key | Notes |
| --- | --- | --- |
| Brave | `BRAVE_API_KEY` | Recommended, free tier available |
| Tavily | `TAVILY_API_KEY` |  |
| Jina | `JINA_API_KEY` |  |
| SearXNG | — | Self-hosted, no API key needed |
| DuckDuckGo | — | No API key needed |
| Perplexity | `PERPLEXITY_API_KEY` | Requires API key |

**3\. Start services**

```
# Backend (FastAPI)
python -m deeptutor.api.run_server

# Frontend (Next.js) — in a separate terminal
cd web && npm run dev -- -p 3782
```

| Service | Default Port |
| --- | --- |
| Backend | `8001` |
| Frontend | `3782` |

Open [http://localhost:3782](http://localhost:3782/) and you're ready to go.

### Option C — Docker Deployment

Docker wraps the backend and frontend into a single container — no local Python or Node.js required. Two options depending on your preference:

**1\. Configure environment variables** (required for both options)

```
git clone https://github.com/HKUDS/DeepTutor.git
cd DeepTutor
cp .env.example .env
```

Edit `.env` and fill in at least the required fields (same as [Option B](#option-b--manual-local-install) above).

**2a. Pull official image (recommended)**

Official images are published to [GitHub Container Registry](https://github.com/HKUDS/DeepTutor/pkgs/container/deeptutor) on every release, built for `linux/amd64` and `linux/arm64`.

```
docker compose -f docker-compose.ghcr.yml up -d
```

To pin a specific version, edit the image tag in `docker-compose.ghcr.yml`:

```
image: ghcr.io/hkuds/deeptutor:1.0.0  # or :latest
```

**2b. Build from source**

```
docker compose up -d
```

This builds the image locally from `Dockerfile` and starts the container.

**3\. Verify & manage**

Open [http://localhost:3782](http://localhost:3782/) once the container is healthy.

```
docker compose logs -f   # tail logs
docker compose down       # stop and remove container
```
**Cloud / remote server deployment**

When deploying to a remote server, the browser needs to know the public URL of the backend API. Add one more variable to your `.env`:

```
# Set to the public URL where the backend is reachable
NEXT_PUBLIC_API_BASE_EXTERNAL=https://your-server.com:8001
```

The frontend startup script applies this value at runtime — no rebuild needed.

**Development mode (hot-reload)**

Layer the dev override to mount source code and enable hot-reload for both services:

```
docker compose -f docker-compose.yml -f docker-compose.dev.yml up
```

Changes to `deeptutor/`, `deeptutor_cli/`, `scripts/`, and `web/` are reflected immediately.

**Custom ports**

Override the default ports in `.env`:

```
BACKEND_PORT=9001
FRONTEND_PORT=4000
```

Then restart:

```
docker compose up -d     # or docker compose -f docker-compose.ghcr.yml up -d
```
**Data persistence**

User data and knowledge bases are persisted via Docker volumes mapped to local directories:

| Container path | Host path | Content |
| --- | --- | --- |
| `/app/data/user` | `./data/user` | Settings, memory, workspace, sessions, logs |
| `/app/data/knowledge_bases` | `./data/knowledge_bases` | Uploaded documents & vector indices |

These directories survive `docker compose down` and are reused on the next `docker compose up`.

**Environment variables reference**

| Variable | Required | Description |
| --- | --- | --- |
| `LLM_BINDING` | **Yes** | LLM provider (`openai`, `anthropic`, etc.) |
| `LLM_MODEL` | **Yes** | Model name (e.g. `gpt-4o`) |
| `LLM_API_KEY` | **Yes** | Your LLM API key |
| `LLM_HOST` | **Yes** | API endpoint URL |
| `EMBEDDING_BINDING` | **Yes** | Embedding provider |
| `EMBEDDING_MODEL` | **Yes** | Embedding model name |
| `EMBEDDING_API_KEY` | **Yes** | Embedding API key |
| `EMBEDDING_HOST` | **Yes** | Embedding endpoint |
| `EMBEDDING_DIMENSION` | **Yes** | Vector dimension |
| `SEARCH_PROVIDER` | No | Search provider (`tavily`, `jina`, `serper`, `perplexity`, etc.) |
| `SEARCH_API_KEY` | No | Search API key |
| `BACKEND_PORT` | No | Backend port (default `8001`) |
| `FRONTEND_PORT` | No | Frontend port (default `3782`) |
| `NEXT_PUBLIC_API_BASE_EXTERNAL` | No | Public backend URL for cloud deployment |
| `DISABLE_SSL_VERIFY` | No | Disable SSL verification (default `false`) |

### Option D — CLI Only

If you just want the CLI without the web frontend:

```
pip install -e ".[cli]"
deeptutor chat                                   # Interactive REPL
deeptutor run chat "Explain Fourier transform"   # One-shot capability
deeptutor run deep_solve "Solve x^2 = 4"         # Multi-agent problem solving
deeptutor kb create my-kb --doc textbook.pdf     # Build a knowledge base
```

> See [DeepTutor CLI](#%EF%B8%8F-deeptutor-cli--agent-native-interface) for the full feature guide and command reference.

---

## 📖 Explore DeepTutor

[![DeepTutor Architecture](https://github.com/HKUDS/DeepTutor/raw/main/assets/figs/deeptutor-architecture.png)](https://github.com/HKUDS/DeepTutor/blob/main/assets/figs/deeptutor-architecture.png)

### 💬 Chat — Unified Intelligent Workspace

[![Chat Workspace](https://github.com/HKUDS/DeepTutor/raw/main/assets/figs/dt-chat.png)](https://github.com/HKUDS/DeepTutor/blob/main/assets/figs/dt-chat.png)

Five distinct modes coexist in a single workspace, bound by a **unified context management system**. Conversation history, knowledge bases, and references persist across modes — switch between them freely within the same topic, whenever the moment calls for it.

| Mode | What It Does |
| --- | --- |
| **Chat** | Fluid, tool-augmented conversation. Choose from RAG retrieval, web search, code execution, deep reasoning, brainstorming, and paper search — mix and match as needed. |
| **Deep Solve** | Multi-agent problem solving: plan, investigate, solve, and verify — with precise source citations at every step. |
| **Quiz Generation** | Generate assessments grounded in your knowledge base, with built-in validation. |
| **Deep Research** | Decompose a topic into subtopics, dispatch parallel research agents across RAG, web, and academic papers, and produce a fully cited report. |
| **Math Animator** | Turn mathematical concepts into visual animations and storyboards powered by Manim. |

Tools are **decoupled from workflows** — in every mode, you decide which tools to enable, how many to use, or whether to use any at all. The workflow orchestrates the reasoning; the tools are yours to compose.

> Start with a quick chat question, escalate to Deep Solve when it gets hard, generate quiz questions to test yourself, then launch a Deep Research to go deeper — all in one continuous thread.

### ✍️ Co-Writer — AI Inside Your Editor

[![Co-Writer](https://github.com/HKUDS/DeepTutor/raw/main/assets/figs/dt-cowriter.png)](https://github.com/HKUDS/DeepTutor/blob/main/assets/figs/dt-cowriter.png)

Co-Writer brings the intelligence of Chat directly into a writing surface. It is a full-featured Markdown editor where AI is a first-class collaborator — not a sidebar, not an afterthought.

Select any text and choose **Rewrite**, **Expand**, or **Shorten** — optionally drawing context from your knowledge base or the web. The editing flow is non-destructive with full undo/redo, and every piece you write can be saved straight to your notebooks, feeding back into your learning ecosystem.

### 🎓 Guided Learning — Visual, Step-by-Step Mastery

[![Guided Learning](https://github.com/HKUDS/DeepTutor/raw/main/assets/figs/dt-guide.png)](https://github.com/HKUDS/DeepTutor/blob/main/assets/figs/dt-guide.png)

Guided Learning turns your personal materials into structured, multi-step learning journeys. Provide a topic, optionally link notebook records, and DeepTutor will:

1. **Design a learning plan** — Identify 3–5 progressive knowledge points from your materials.
2. **Generate interactive pages** — Each point becomes a rich visual HTML page with explanations, diagrams, and examples.
3. **Enable contextual Q&A** — Chat alongside each step for deeper exploration.
4. **Summarize your progress** — Upon completion, receive a learning summary of everything you've covered.

Sessions are persistent — pause, resume, or revisit any step at any time.

### 📚 Knowledge Management — Your Learning Infrastructure

[![Knowledge Management](https://github.com/HKUDS/DeepTutor/raw/main/assets/figs/dt-knowledge.png)](https://github.com/HKUDS/DeepTutor/blob/main/assets/figs/dt-knowledge.png)

Knowledge is where you build and manage the document collections that power everything else in DeepTutor.

- **Knowledge Bases** — Upload PDF, TXT, or Markdown files to create searchable, RAG-ready collections. Add documents incrementally as your library grows.
- **Notebooks** — Organize learning records across sessions. Save insights from Chat, Guided Learning, Co-Writer, or Deep Research into categorized, color-coded notebooks.

Your knowledge base is not passive storage — it actively participates in every conversation, every research session, and every learning path you create.

### 🧠 Memory — DeepTutor Learns As You Learn

[![Memory](https://github.com/HKUDS/DeepTutor/raw/main/assets/figs/dt-memory.png)](https://github.com/HKUDS/DeepTutor/blob/main/assets/figs/dt-memory.png)

DeepTutor maintains a persistent, evolving understanding of you through two complementary dimensions:

- **Summary** — A running digest of your learning progress: what you've studied, which topics you've explored, and how your understanding has developed.
- **Profile** — Your learner identity: preferences, knowledge level, goals, and communication style — automatically refined through every interaction.

Memory is shared across all features and all your TutorBots. The more you use DeepTutor, the more personalized and effective it becomes.

---

### 🦞 TutorBot — Persistent, Autonomous AI Tutors

[![TutorBot Architecture](https://github.com/HKUDS/DeepTutor/raw/main/assets/figs/tutorbot-architecture.png)](https://github.com/HKUDS/DeepTutor/blob/main/assets/figs/tutorbot-architecture.png)

TutorBot is not a chatbot — it is a **persistent, multi-instance agent** built on [nanobot](https://github.com/HKUDS/nanobot). Each TutorBot runs its own agent loop with independent workspace, memory, and personality. Create a Socratic math tutor, a patient writing coach, and a rigorous research advisor — all running simultaneously, each evolving with you.

[![TutorBot](https://github.com/HKUDS/DeepTutor/raw/main/assets/figs/tb.png)](https://github.com/HKUDS/DeepTutor/blob/main/assets/figs/tb.png)

- **Soul Templates** — Define your tutor's personality, tone, and teaching philosophy through editable Soul files. Choose from built-in archetypes (Socratic, encouraging, rigorous) or craft your own — the soul shapes every response.
- **Independent Workspace** — Each bot has its own directory with separate memory, sessions, skills, and configuration — fully isolated yet able to access DeepTutor's shared knowledge layer.
- **Proactive Heartbeat** — Bots don't just respond — they initiate. The built-in Heartbeat system enables recurring study check-ins, review reminders, and scheduled tasks. Your tutor shows up even when you don't.
- **Full Tool Access** — Every bot reaches into DeepTutor's complete toolkit: RAG retrieval, code execution, web search, academic paper search, deep reasoning, and brainstorming.
- **Skill Learning** — Teach your bot new abilities by adding skill files to its workspace. As your needs evolve, so does your tutor's capability.
- **Multi-Channel Presence** — Connect bots to Telegram, Discord, Slack, Feishu, WeChat Work, DingTalk, Email, and more. Your tutor meets you wherever you are.
- **Team & Sub-Agents** — Spawn background sub-agents or orchestrate multi-agent teams within a single bot for complex, long-running tasks.
```
deeptutor bot create math-tutor --persona "Socratic math teacher who uses probing questions"
deeptutor bot create writing-coach --persona "Patient, detail-oriented writing mentor"
deeptutor bot list                  # See all your active tutors
```

---

### ⌨️ DeepTutor CLI — Agent-Native Interface

[![DeepTutor CLI Architecture](https://github.com/HKUDS/DeepTutor/raw/main/assets/figs/cli-architecture.png)](https://github.com/HKUDS/DeepTutor/blob/main/assets/figs/cli-architecture.png)

DeepTutor is fully CLI-native. Every capability, knowledge base, session, memory, and TutorBot is one command away — no browser required. The CLI serves both humans (with rich terminal rendering) and AI agents (with structured JSON output).

Hand the [`SKILL.md`](https://github.com/HKUDS/DeepTutor/blob/main/SKILL.md) at the project root to any tool-using agent ([nanobot](https://github.com/HKUDS/nanobot), or any LLM with tool access), and it can configure and operate DeepTutor autonomously.

**One-shot execution** — Run any capability directly from the terminal:

```
deeptutor run chat "Explain the Fourier transform" -t rag --kb textbook
deeptutor run deep_solve "Prove that √2 is irrational" -t reason
deeptutor run deep_question "Linear algebra" --config num_questions=5
deeptutor run deep_research "Attention mechanisms in transformers"
```

**Interactive REPL** — A persistent chat session with live mode switching:

```
deeptutor chat --capability deep_solve --kb my-kb
# Inside the REPL: /cap, /tool, /kb, /history, /notebook, /config to switch on the fly
```

**Knowledge base lifecycle** — Build, query, and manage RAG-ready collections entirely from the terminal:

```
deeptutor kb create my-kb --doc textbook.pdf       # Create from document
deeptutor kb add my-kb --docs-dir ./papers/         # Add a folder of papers
deeptutor kb search my-kb "gradient descent"        # Search directly
deeptutor kb set-default my-kb                      # Set as default for all commands
```

**Dual output mode** — Rich rendering for humans, structured JSON for pipelines:

```
deeptutor run chat "Summarize chapter 3" -f rich    # Colored, formatted output
deeptutor run chat "Summarize chapter 3" -f json    # Line-delimited JSON events
```

**Session continuity** — Resume any conversation right where you left off:

```
deeptutor session list                              # List all sessions
deeptutor session open <id>                         # Resume in REPL
```
**Full CLI command reference**

**Top-level**

| Command | Description |
| --- | --- |
| `deeptutor run <capability> <message>` | Run any capability in a single turn (`chat`, `deep_solve`, `deep_question`, `deep_research`, `math_animator`) |
| `deeptutor chat` | Interactive REPL with optional `--capability`, `--tool`, `--kb`, `--language` |
| `deeptutor serve` | Start the DeepTutor API server |

**`deeptutor bot`**

| Command | Description |
| --- | --- |
| `deeptutor bot list` | List all TutorBot instances |
| `deeptutor bot create <id>` | Create and start a new bot (`--name`, `--persona`, `--model`) |
| `deeptutor bot start <id>` | Start a bot |
| `deeptutor bot stop <id>` | Stop a bot |

**`deeptutor kb`**

| Command | Description |
| --- | --- |
| `deeptutor kb list` | List all knowledge bases |
| `deeptutor kb info <name>` | Show knowledge base details |
| `deeptutor kb create <name>` | Create from documents (`--doc`, `--docs-dir`) |
| `deeptutor kb add <name>` | Add documents incrementally |
| `deeptutor kb search <name> <query>` | Search a knowledge base |
| `deeptutor kb set-default <name>` | Set as default KB |
| `deeptutor kb delete <name>` | Delete a knowledge base (`--force`) |

**`deeptutor memory`**

| Command | Description |
| --- | --- |
| `deeptutor memory show [file]` | View memory (`summary`, `profile`, or `all`) |
| `deeptutor memory clear [file]` | Clear memory (`--force`) |

**`deeptutor session`**

| Command | Description |
| --- | --- |
| `deeptutor session list` | List sessions (`--limit`) |
| `deeptutor session show <id>` | View session messages |
| `deeptutor session open <id>` | Resume session in REPL |
| `deeptutor session rename <id>` | Rename a session (`--title`) |
| `deeptutor session delete <id>` | Delete a session |

**`deeptutor notebook`**

| Command | Description |
| --- | --- |
| `deeptutor notebook list` | List notebooks |
| `deeptutor notebook create <name>` | Create a notebook (`--description`) |
| `deeptutor notebook show <id>` | View notebook records |
| `deeptutor notebook add-md <id> <path>` | Import markdown as record |
| `deeptutor notebook replace-md <id> <rec> <path>` | Replace a markdown record |
| `deeptutor notebook remove-record <id> <rec>` | Remove a record |

**`deeptutor config` / `plugin` / `provider`**

| Command | Description |
| --- | --- |
| `deeptutor config show` | Print current configuration summary |
| `deeptutor plugin list` | List registered tools and capabilities |
| `deeptutor plugin info <name>` | Show tool or capability details |
| `deeptutor provider login <provider>` | Provider auth (`openai-codex` OAuth login; `github-copilot` validates an existing Copilot auth session) |

## 🗺️ Roadmap

| Status | Milestone |
| --- | --- |
| 🎯 | **Authentication & Login** — Optional login page for public deployments with multi-user support |
| 🎯 | **Themes & Appearance** — Diverse theme options and customizable UI appearance |
| 🎯 | **Interaction Improvement** — optimize icon design and interaction details |
| 🔜 | **Better Memories** — integrating better memory management |
| 🔜 | **LightRAG Integration** — Integrate [LightRAG](https://github.com/HKUDS/LightRAG) as an advanced knowledge base engine |
| 🔜 | **Documentation Site** — Comprehensive docs page with guides, API reference, and tutorials |

> If you find DeepTutor useful, [give us a star](https://github.com/HKUDS/DeepTutor/stargazers) — it helps us keep going!

---

## 🌐 Community & Ecosystem

DeepTutor stands on the shoulders of outstanding open-source projects:

| Project | Role in DeepTutor |
| --- | --- |
| [**nanobot**](https://github.com/HKUDS/nanobot) | Ultra-lightweight agent engine powering TutorBot |
| [**LlamaIndex**](https://github.com/run-llama/llama_index) | RAG pipeline and document indexing backbone |
| [**ManimCat**](https://github.com/Wing900/ManimCat) | AI-driven math animation generation for Math Animator |

**From the HKUDS ecosystem:**

| [⚡ LightRAG](https://github.com/HKUDS/LightRAG) | [🤖 AutoAgent](https://github.com/HKUDS/AutoAgent) | [🔬 AI-Researcher](https://github.com/HKUDS/AI-Researcher) | [🧬 nanobot](https://github.com/HKUDS/nanobot) |
| --- | --- | --- | --- |
| Simple & Fast RAG | Zero-Code Agent Framework | Automated Research | Ultra-Lightweight AI Agent |

## 🤝 Contributing

We hope DeepTutor becomes a gift for the community. 🎁

[![Contributors](https://camo.githubusercontent.com/35d234040bdf1c3a7bcf124360d904d94ca7fd6b96a6bf3ff8eef5788a60efd2/68747470733a2f2f636f6e747269622e726f636b732f696d6167653f7265706f3d484b5544532f446565705475746f72266d61783d393939)](https://github.com/HKUDS/DeepTutor/graphs/contributors)

See [CONTRIBUTING.md](https://github.com/HKUDS/DeepTutor/blob/main/CONTRIBUTING.md) for guidelines on setting up your development environment, code standards, and pull request workflow.

## ⭐ Star History

[![Star History Chart](https://camo.githubusercontent.com/aa953925439f8ada60483d7610f4b6b9124542ee31ffe85fb6541f70818dbd63/68747470733a2f2f6170692e737461722d686973746f72792e636f6d2f7376673f7265706f733d484b5544532f446565705475746f7226747970653d74696d656c696e65266c6567656e643d746f702d6c656674)](https://www.star-history.com/#HKUDS/DeepTutor&type=timeline&legend=top-left)

[![Star History Rank](https://camo.githubusercontent.com/4b932d5b94d1458b62d898e4b7ab119c646bf790285177a29fcb1aa72e50cacf/68747470733a2f2f6170692e737461722d686973746f72792e636f6d2f62616467653f7265706f3d484b5544532f446565705475746f72)](https://www.star-history.com/hkuds/deeptutor)

[⭐ Star us](https://github.com/HKUDS/DeepTutor/stargazers) · [🐛 Report a bug](https://github.com/HKUDS/DeepTutor/issues) · [💬 Discussions](https://github.com/HKUDS/DeepTutor/discussions)

---

Licensed under the [Apache License 2.0](https://github.com/HKUDS/DeepTutor/blob/main/LICENSE).

[![Views](https://camo.githubusercontent.com/a89fd08b11b32227be8bdf029e4aa1f95d144e66570bc3b7078f791c72ff5b21/68747470733a2f2f76697369746f722d62616467652e6c616f62692e6963752f62616467653f706167655f69643d484b5544532e446565705475746f72267374796c653d666f722d7468652d626164676526636f6c6f723d303064346666)](https://camo.githubusercontent.com/a89fd08b11b32227be8bdf029e4aa1f95d144e66570bc3b7078f791c72ff5b21/68747470733a2f2f76697369746f722d62616467652e6c616f62692e6963752f62616467653f706167655f69643d484b5544532e446565705475746f72267374796c653d666f722d7468652d626164676526636f6c6f723d303064346666)