---
title: "DayuanJiang/next-ai-draw-io: A next.js web application that integrates AI capabilities with draw.io diagrams. This app allows you to create, modify, and enhance diagrams through natural language commands and AI-assisted visualization."
source: "https://github.com/DayuanJiang/next-ai-draw-io"
author:
published:
created: 2026-04-16
description: "A next.js web application that integrates AI capabilities with draw.io diagrams. This app allows you to create, modify, and enhance diagrams through natural language commands and AI-assisted visualization. - DayuanJiang/next-ai-draw-io"
tags:
  - "clippings"
---
## Next AI Draw.io

**AI-Powered Diagram Creation Tool - Chat, Draw, Visualize**

English | [中文](https://github.com/DayuanJiang/next-ai-draw-io/blob/main/docs/cn/README_CN.md) | [日本語](https://github.com/DayuanJiang/next-ai-draw-io/blob/main/docs/ja/README_JA.md)

[![TrendShift](https://camo.githubusercontent.com/ec4b3309820c4b14f597ea030e9862302565220813e8a60e181505117468e6e7/68747470733a2f2f7472656e6473686966742e696f2f6170692f62616467652f7265706f7369746f726965732f3135343439)](https://next-ai-drawio.jiang.jp/)

[![Live Demo](https://github.com/DayuanJiang/next-ai-draw-io/raw/main/public/live-demo-button.svg)](https://next-ai-drawio.jiang.jp/)

A Next.js web application that integrates AI capabilities with draw.io diagrams. Create, modify, and enhance diagrams through natural language commands and AI-assisted visualization.

> Note: Thanks to [ByteDance Doubao](https://www.volcengine.com/activity/codingplan?ac=MMAP8JTTCAQ2&rc=Z9Z3LDTJ&utm_campaign=drawio&utm_content=drawio&utm_medium=devrel&utm_source=OWO&utm_term=drawio) sponsorship, the demo site now uses the powerful glm-4.7 model!

20251211\_drawio.mp4<video src="https://private-user-images.githubusercontent.com/34411969/525172622-9d60a3e8-4a1c-4b5e-acbb-26af2d3eabd1.mp4?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNDQzNDgsIm5iZiI6MTc3NjM0NDA0OCwicGF0aCI6Ii8zNDQxMTk2OS81MjUxNzI2MjItOWQ2MGEzZTgtNGExYy00YjVlLWFjYmItMjZhZjJkM2VhYmQxLm1wND9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDEyNTQwOFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWRjYjk1ZDQ5M2VhYzA4NzY5N2UwY2YzZTM3NWVkZmMyNDY5ZDliMzA4N2ViMzQzNjgyNjg2OTgzZWMxMzJjOTgmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT12aWRlbyUyRm1wNCJ9.MY0wBObcLKTFpRbRbgw-D5B3ZIV8KGOV4vAMQjD0Iz4" controls="controls"></video>

## Table of Contents

- [Next AI Draw.io](#next-ai-drawio)
	- [Table of Contents](#table-of-contents)
		- [Examples](#examples)
		- [Features](#features)
		- [MCP Server](#mcp-server)
		- [Claude Code CLI](#claude-code-cli)
		- [Getting Started](#getting-started)
		- [Try it Online](#try-it-online)
				- [Desktop Application](#desktop-application)
				- [Run with Docker](#run-with-docker)
				- [Installation](#installation)
		- [Deployment](#deployment)
		- [Deploy to EdgeOne Pages](#deploy-to-edgeone-pages)
				- [Deploy on Vercel](#deploy-on-vercel)
				- [Deploy on Cloudflare Workers](#deploy-on-cloudflare-workers)
		- [Multi-Provider Support](#multi-provider-support)
		- [How It Works](#how-it-works)
		- [Support & Contact](#support--contact)
		- [FAQ](#faq)
		- [Star History](#star-history)

## Examples

Here are some example prompts and their generated diagrams:

<table width="100%"><tbody><tr><td colspan="2" align="center"><strong>Animated transformer connectors</strong><br><p><strong>Prompt:</strong> Give me a **animated connector** diagram of transformer's architecture.</p><a href="https://github.com/DayuanJiang/next-ai-draw-io/blob/main/public/animated_connectors.svg"><img src="https://github.com/DayuanJiang/next-ai-draw-io/raw/main/public/animated_connectors.svg" width="480"></a></td></tr><tr><td width="50%"><strong>RAG Technique Diagram</strong><br><p><strong>Prompt:</strong> Generate a RAG architecture diagram for **chat application**. Use connected diagram for data ingestion</p><a href="https://github.com/DayuanJiang/next-ai-draw-io/blob/main/public/rag_prod.svg"><img src="https://github.com/DayuanJiang/next-ai-draw-io/raw/main/public/rag_prod.svg" width="480"></a></td><td width="50%"><strong>Authentication using React and AWS</strong><br><p><strong>Prompt:</strong> Generate authentication process using React with **AWS**. Use Serverless architecture.</p><a href="https://github.com/DayuanJiang/next-ai-draw-io/blob/main/public/auth.svg"><img src="https://github.com/DayuanJiang/next-ai-draw-io/raw/main/public/auth.svg" width="480"></a></td></tr><tr><td width="50%"><strong>Open Innovation</strong><br><p><strong>Prompt:</strong> Create visualization of Henry Chesbrough's Open Innovation model.</p><a href="https://github.com/DayuanJiang/next-ai-draw-io/blob/main/public/inno.svg"><img src="https://github.com/DayuanJiang/next-ai-draw-io/raw/main/public/inno.svg" width="480"></a></td><td width="50%"><strong>Cat sketch</strong><br><p><strong>Prompt:</strong> Draw a cute cat for me.</p><a href="https://github.com/DayuanJiang/next-ai-draw-io/blob/main/public/cat_demo.svg"><img src="https://github.com/DayuanJiang/next-ai-draw-io/raw/main/public/cat_demo.svg" width="240"></a></td></tr></tbody></table>

## Features

- **LLM-Powered Diagram Creation**: Leverage Large Language Models to create and manipulate draw.io diagrams directly through natural language commands
- **Image-Based Diagram Replication**: Upload existing diagrams or images and have the AI replicate and enhance them automatically
- **PDF & Text File Upload**: Upload PDF documents and text files to extract content and generate diagrams from existing documents
- **AI Reasoning Display**: View the AI's thinking process for supported models (OpenAI o1/o3, Gemini, Claude, etc.)
- **Diagram History**: Comprehensive version control that tracks all changes, allowing you to view and restore previous versions of your diagrams before the AI editing.
- **Interactive Chat Interface**: Communicate with AI to refine your diagrams in real-time
- **Cloud Architecture Diagram Support**: Specialized support for generating cloud architecture diagrams (AWS, GCP, Azure)
- **Animated Connectors**: Create dynamic and animated connectors between diagram elements for better visualization

## MCP Server

Use Next AI Draw.io with AI agents like Claude Desktop, Cursor, and VS Code via MCP (Model Context Protocol).

```
{
  "mcpServers": {
    "drawio": {
      "command": "npx",
      "args": ["@next-ai-drawio/mcp-server@latest"]
    }
  }
}
```

### Claude Code CLI

```
claude mcp add drawio -- npx @next-ai-drawio/mcp-server@latest
```

Then ask Claude to create diagrams:

> "Create a flowchart showing user authentication with login, MFA, and session management"

The diagram appears in your browser in real-time!

See the [MCP Server README](https://github.com/DayuanJiang/next-ai-draw-io/blob/main/packages/mcp-server/README.md) for VS Code, Cursor, and other client configurations.

## Getting Started

### Try it Online

No installation needed! Try the app directly on our demo site:

[![Live Demo](https://github.com/DayuanJiang/next-ai-draw-io/raw/main/public/live-demo-button.svg)](https://next-ai-drawio.jiang.jp/)

> **Bring Your Own API Key**: You can use your own API key to bypass usage limits on the demo site. Click the Settings icon in the chat panel to configure your provider and API key. Your key is stored locally in your browser and is never stored on the server.

### Desktop Application

Download the native desktop app for your platform from the [Releases page](https://github.com/DayuanJiang/next-ai-draw-io/releases):

Supported platforms: Windows, macOS, Linux.

### Run with Docker

[Go to Docker Guide](https://github.com/DayuanJiang/next-ai-draw-io/blob/main/docs/en/docker.md)

### Installation

1. Clone the repository:
```
git clone https://github.com/DayuanJiang/next-ai-draw-io
cd next-ai-draw-io
npm install
cp env.example .env.local
```

See the [Provider Configuration Guide](https://github.com/DayuanJiang/next-ai-draw-io/blob/main/docs/en/ai-providers.md) for detailed setup instructions for each provider.

1. Run the development server:
```
npm run dev
```
1. Open [http://localhost:6002](http://localhost:6002/) in your browser to see the application.

## Deployment

### Deploy to EdgeOne Pages

You can deploy with one click using [Tencent EdgeOne Pages](https://pages.edgeone.ai/).

Deploy by this button:

Check out the [Tencent EdgeOne Pages documentation](https://pages.edgeone.ai/document/deployment-overview) for more details.

Additionally, deploying through Tencent EdgeOne Pages will also grant you a [daily free quota for DeepSeek models](https://pages.edgeone.ai/document/edge-ai).

### Deploy on Vercel

The easiest way to deploy is using [Vercel](https://vercel.com/new), the creators of Next.js. Be sure to **set the environment variables** in the Vercel dashboard as you did in your local `.env.local` file.

See the [Next.js deployment documentation](https://nextjs.org/docs/app/building-your-application/deploying) for more details.

### Deploy on Cloudflare Workers

[Go to Cloudflare Deploy Guide](https://github.com/DayuanJiang/next-ai-draw-io/blob/main/docs/en/cloudflare-deploy.md)

## Multi-Provider Support

- [ByteDance Doubao](https://www.volcengine.com/activity/codingplan?ac=MMAP8JTTCAQ2&rc=Z9Z3LDTJ&utm_campaign=drawio&utm_content=drawio&utm_medium=devrel&utm_source=OWO&utm_term=drawio)
- AWS Bedrock (default)
- OpenAI
- Anthropic
- Google AI
- Google Vertex AI
- Azure OpenAI
- Ollama
- OpenRouter
- DeepSeek
- SiliconFlow
- ModelScope
- SGLang
- Vercel AI Gateway

All providers except AWS Bedrock and OpenRouter support custom endpoints.

📖 **[Detailed Provider Configuration Guide](https://github.com/DayuanJiang/next-ai-draw-io/blob/main/docs/en/ai-providers.md)** - See setup instructions for each provider.

### Server-Side Multi-Model Configuration

Administrators can configure multiple server-side models that are available to all users without requiring personal API keys. Configure via `AI_MODELS_CONFIG` environment variable (JSON string) or `ai-models.json` file.

**Model Requirements**: This task requires strong model capabilities for generating long-form text with strict formatting constraints (draw.io XML). Recommended models include Claude Sonnet 4.5, GPT-5.1, Gemini 3 Pro, and DeepSeek V3.2/R1.

Note that the `claude` series has been trained on draw.io diagrams with cloud architecture logos like AWS, Azure, GCP. So if you want to create cloud architecture diagrams, this is the best choice.

## How It Works

The application uses the following technologies:

- **Next.js**: For the frontend framework and routing
- **Vercel AI SDK** (`ai` + `@ai-sdk/*`): For streaming AI responses and multi-provider support
- **react-drawio**: For diagram representation and manipulation

Diagrams are represented as XML that can be rendered in draw.io. The AI processes your commands and generates or modifies this XML accordingly.

## Support & Contact

**Special thanks to [ByteDance Doubao](https://www.volcengine.com/activity/codingplan?ac=MMAP8JTTCAQ2&rc=Z9Z3LDTJ&utm_campaign=drawio&utm_content=drawio&utm_medium=devrel&utm_source=OWO&utm_term=drawio) for sponsoring the API token usage of the demo site!** Register on the ARK platform to get 500K free tokens for all models!

If you find this project useful, please consider [sponsoring](https://github.com/sponsors/DayuanJiang) to help me host the live demo site!

For support or inquiries, please open an issue on the GitHub repository or contact the maintainer at:

- Email: me\[at\]jiang.jp

## FAQ

See [FAQ](https://github.com/DayuanJiang/next-ai-draw-io/blob/main/docs/en/FAQ.md) for common issues and solutions.

[![Star History Chart](https://camo.githubusercontent.com/2bef6d2d565dd45362999ff4b905c00ddf5d934fecbc5a38a2dceb87c6594056/68747470733a2f2f6170692e737461722d686973746f72792e636f6d2f7376673f7265706f733d44617975616e4a69616e672f6e6578742d61692d647261772d696f26747970653d64617465266c6567656e643d746f702d6c656674)](https://www.star-history.com/#DayuanJiang/next-ai-draw-io&type=date&legend=top-left)