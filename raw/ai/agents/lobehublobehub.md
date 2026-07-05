---
title: "lobehub/lobehub: The ultimate space for work and life — to find, build, and collaborate with agent teammates that grow with you. We are taking agent harness to the next level — enabling multi-agent collaboration, effortless agent team design, and introducing agents as the unit of work interaction."
source: "https://github.com/lobehub/lobehub"
author:
published:
created: 2026-04-16
description: "The ultimate space for work and life — to find, build, and collaborate with agent teammates that grow with you. We are taking agent harness to the next level — enabling multi-agent collaboration, effortless agent team design, and introducing agents as the unit of work interaction. - lobehub/lobehub"
tags:
  - "clippings"
---

#### TOC

- [👋🏻 Getting Started & Join Our Community](#-getting-started--join-our-community)
- [✨ Features](#-features)
	- [Create: Agents as the Unit of Work](#create-agents-as-the-unit-of-work)
		- [Collaborate: Scale New Forms of Collaboration Networks](#collaborate-scale-new-forms-of-collaboration-networks)
		- [Evolve: Co-evolution of Humans and Agents](#evolve-co-evolution-of-humans-and-agents)
		- [MCP Plugin One-Click Installation](#mcp-plugin-one-click-installation)
		- [MCP Marketplace](#mcp-marketplace)
		- [Desktop App](#desktop-app)
		- [Smart Internet Search](#smart-internet-search)
		- [Chain of Thought](#chain-of-thought)
		- [Branching Conversations](#branching-conversations)
		- [Artifacts Support](#artifacts-support)
		- [File Upload /Knowledge Base](#file-upload-knowledge-base)
		- [Multi-Model Service Provider Support](#multi-model-service-provider-support)
		- [Local Large Language Model (LLM) Support](#local-large-language-model-llm-support)
		- [Model Visual Recognition](#model-visual-recognition)
		- [TTS & STT Voice Conversation](#tts--stt-voice-conversation)
		- [Text to Image Generation](#text-to-image-generation)
		- [Plugin System (Function Calling)](#plugin-system-function-calling)
		- [Agent Market (GPTs)](#agent-market-gpts)
		- [Support Local / Remote Database](#support-local--remote-database)
		- [Support Multi-User Management](#support-multi-user-management)
		- [Progressive Web App (PWA)](#progressive-web-app-pwa)
		- [Mobile Device Adaptation](#mobile-device-adaptation)
		- [Custom Themes](#custom-themes)
		- [`*` What's more](#-whats-more)
- [🛳 Self Hosting](#-self-hosting)
	- [`A` Deploying with Vercel, Zeabur, Sealos or Alibaba Cloud](#a-deploying-with-vercel-zeabur--sealos-or-alibaba-cloud)
		- [`B` Deploying with Docker](#b-deploying-with-docker)
		- [Environment Variable](#environment-variable)
- [📦 Ecosystem](#-ecosystem)
- [🧩 Plugins](#-plugins)
- [⌨️ Local Development](#%EF%B8%8F-local-development)
- [🤝 Contributing](#-contributing)
- [❤️ Sponsor](#%EF%B8%8F-sponsor)
- [🔗 More Products](#-more-products)
  
  
lobehub.webm<video src="https://private-user-images.githubusercontent.com/17870709/540838307-6710ad97-03d0-4175-bd75-adff9b55eca2.webm?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNDU5MTQsIm5iZiI6MTc3NjM0NTYxNCwicGF0aCI6Ii8xNzg3MDcwOS81NDA4MzgzMDctNjcxMGFkOTctMDNkMC00MTc1LWJkNzUtYWRmZjliNTVlY2EyLndlYm0_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwNDE2JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDQxNlQxMzIwMTRaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT0xYzNkYTZjNTU2ZGU4MzU3YmExN2ZkZWIxYTZhOWJiODg2ZDBjOThlMmQ1ODI0Y2ZlNmY3M2I0ZmZiODEzZDQ0JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZyZXNwb25zZS1jb250ZW50LXR5cGU9dmlkZW8lMkZ3ZWJtIn0.Ktv11glgyYWo7sEd7odf_HVHfWJxqG8cJqK2SW3JVyE" controls="controls"></video>

## 👋🏻 Getting Started & Join Our Community

We are a group of e/acc design-engineers, hoping to provide modern design components and tools for AIGC. By adopting the Bootstrapping approach, we aim to provide developers and users with a more open, transparent, and user-friendly product ecosystem.

Whether for users or professional developers, LobeHub will be your AI Agent playground. Please be aware that LobeHub is currently under active development, and feedback is welcome for any [issues](https://img.shields.io/github/issues/lobehub/lobehub.svg?style=flat) encountered.

|  | We are live on Product Hunt! We are thrilled to bring LobeHub to the world. If you believe in a future where humans and agents co-evolve, please support our journey. |
| --- | --- |
|  | Join our Discord community! This is where you can connect with developers and other enthusiastic users of LobeHub. |


[![](https://private-user-images.githubusercontent.com/17870709/540840085-3216e25b-186f-4a54-9cb4-2f124aec0471.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNDU5MTQsIm5iZiI6MTc3NjM0NTYxNCwicGF0aCI6Ii8xNzg3MDcwOS81NDA4NDAwODUtMzIxNmUyNWItMTg2Zi00YTU0LTljYjQtMmYxMjRhZWMwNDcxLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDEzMjAxNFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWMzNjM2ZDQ5YjVmZTUyZTYwNGE5MzdmMDhiOTVjMTJkMDI3ZGRlNzIwOWY3ZDUxZjMxMTE5MmU4NzMxMzI2ZGEmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.nWLBk8bTwP8wi8I00HfPw7PGL-LBB6mY1_oRuojwSoU)](https://github.com/lobehub/lobehub/stargazers)

Star History ![](https://camo.githubusercontent.com/12ebab9ac33bb09bb9d552fe8048ccf29761c37c0e1baf99de8371365a72037b/68747470733a2f2f6170692e737461722d686973746f72792e636f6d2f7376673f7265706f733d6c6f62656875622532466c6f626568756226747970653d44617465) 

## ✨ Features

Today’s agents are one-off, task-driven tools. They lack context, live in isolation, and require manual hand-offs between different windows and models. While some maintain memory, it is often global, shallow, and impersonal. In this mode, users are forced to toggle between fragmented conversations, making it difficult to form structured productivity.

**LobeHub changes everything.**

LobeHub is a work-and-lifestyle space to find, build, and collaborate with agent teammates that grow with you. In LobeHub, we treat **Agents as the unit of work**, providing an infrastructure where humans and agents co-evolve.

[![](https://camo.githubusercontent.com/ec92c61a17a7e5ef21c6f1fb65a23cb458683d8172d0fb13b53db3ca4af88979/68747470733a2f2f6875622d617061632d312e6c6f62656f626a656374732e73706163652f626c6f672f6173736574732f32323034636465323232386662336635383366336632633039306263343966622e77656270)](https://camo.githubusercontent.com/ec92c61a17a7e5ef21c6f1fb65a23cb458683d8172d0fb13b53db3ca4af88979/68747470733a2f2f6875622d617061632d312e6c6f62656f626a656374732e73706163652f626c6f672f6173736574732f32323034636465323232386662336635383366336632633039306263343966622e77656270)

### Create: Agents as the Unit of Work

Building a personalized AI team starts with the **Agent Builder**. You can describe what you need once, and the agent setup starts right away, applying auto-configurations so you can use it instantly.

- **Unified Intelligence**: Seamlessly access any model and any modality—all under your control.
- **10,000+ Skills**: Connect your agents to the skills you use every day with a library of over 10,000 tools and MCP-compatible plugins.

[![](https://camo.githubusercontent.com/299237bd4f2ec879fcc54bc84cd7416f137f5f1ed416f393b90b3bfb204aa401/68747470733a2f2f6875622d617061632d312e6c6f62656f626a656374732e73706163652f626c6f672f6173736574732f37373166663364333062396566393365363565353530323163633433643335362e77656270)](https://camo.githubusercontent.com/299237bd4f2ec879fcc54bc84cd7416f137f5f1ed416f393b90b3bfb204aa401/68747470733a2f2f6875622d617061632d312e6c6f62656f626a656374732e73706163652f626c6f672f6173736574732f37373166663364333062396566393365363565353530323163633433643335362e77656270)

### Collaborate: Scale New Forms of Collaboration Networks

LobeHub introduces **Agent Groups**, allowing you to work with agents like real teammates. The system assembles the right agents for the task, enabling parallel collaboration and iterative improvement.

- **Pages**: Write and refine content with multiple agents in one place with a shared context.
- **Schedule**: Schedule runs and let agents do the work at the right time, even while you are away.
- **Project**: Organize work by project to keep everything structured and easy to track.
- **Workspace**: A shared space for teams to collaborate with agents, ensuring clear ownership and visibility across the organization.

[![](https://camo.githubusercontent.com/df1631d4ee7913de8af8f897eacd5de78cc56291dc3eefc1bd8b2676d7427b48/68747470733a2f2f6875622d617061632d312e6c6f62656f626a656374732e73706163652f626c6f672f6173736574732f66653938656165396663623661636334376338653166623639626462346235302e77656270)](https://camo.githubusercontent.com/df1631d4ee7913de8af8f897eacd5de78cc56291dc3eefc1bd8b2676d7427b48/68747470733a2f2f6875622d617061632d312e6c6f62656f626a656374732e73706163652f626c6f672f6173736574732f66653938656165396663623661636334376338653166623639626462346235302e77656270)

### Evolve: Co-evolution of Humans and Agents

The best AI is one that understands you deeply. LobeHub features **Personal Memory** that builds a clear understanding of your needs.

- **Continual Learning**: Your agents learn from how you work, adapting their behavior to act at the right moment.
- **White-Box Memory**: We believe in transparency. Your agents use structured, editable memory, giving you full control over what they remember.
More Features

[![](https://private-user-images.githubusercontent.com/28616219/463694299-1be85d36-3975-4413-931f-27e05e440995.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNDU5MTQsIm5iZiI6MTc3NjM0NTYxNCwicGF0aCI6Ii8yODYxNjIxOS80NjM2OTQyOTktMWJlODVkMzYtMzk3NS00NDEzLTkzMWYtMjdlMDVlNDQwOTk1LnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDEzMjAxNFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTYyZjQ4MDgwY2EyNmM4ZTI2ZjMxZWNiNDFlNGMyMmIzNTJkZjg3ZWZiYjAyMGJjMzg3MmEyNjZkMGNiNjAyMzUmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.CKHNBrhP1dqL3h9K2fseNYd1LS-qt4QMsTgFha4Hs9Q)](https://private-user-images.githubusercontent.com/28616219/463694299-1be85d36-3975-4413-931f-27e05e440995.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNDU5MTQsIm5iZiI6MTc3NjM0NTYxNCwicGF0aCI6Ii8yODYxNjIxOS80NjM2OTQyOTktMWJlODVkMzYtMzk3NS00NDEzLTkzMWYtMjdlMDVlNDQwOTk1LnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDEzMjAxNFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTYyZjQ4MDgwY2EyNmM4ZTI2ZjMxZWNiNDFlNGMyMmIzNTJkZjg3ZWZiYjAyMGJjMzg3MmEyNjZkMGNiNjAyMzUmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.CKHNBrhP1dqL3h9K2fseNYd1LS-qt4QMsTgFha4Hs9Q)

### MCP Plugin One-Click Installation

**Seamlessly Connect Your AI to the World**

Unlock the full potential of your AI by enabling smooth, secure, and dynamic interactions with external tools, data sources, and services. LobeHub's MCP (Model Context Protocol) plugin system breaks down the barriers between your AI and the digital ecosystem, allowing for unprecedented connectivity and functionality.

Transform your conversations into powerful workflows by connecting to databases, APIs, file systems, and more. Experience the freedom of AI that truly understands and interacts with your world.

[![](https://private-user-images.githubusercontent.com/28616219/463694839-bb114f9f-24c5-4000-a984-c10d187da5a0.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNDU5MTQsIm5iZiI6MTc3NjM0NTYxNCwicGF0aCI6Ii8yODYxNjIxOS80NjM2OTQ4MzktYmIxMTRmOWYtMjRjNS00MDAwLWE5ODQtYzEwZDE4N2RhNWEwLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDEzMjAxNFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTI4ZTI1MGEwMWM2MjA1ZTc4YWNkOWQ0YTVjMjY2YWU0Njg4YzBjZmQ3MTUyNWY5ZGFjN2RhZjBmOTI5YjBmMzgmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.pkNCv5IIYOyifO9etSN2hv3p65Eu2uZaE243UlCqGFI)](https://private-user-images.githubusercontent.com/28616219/463694839-bb114f9f-24c5-4000-a984-c10d187da5a0.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNDU5MTQsIm5iZiI6MTc3NjM0NTYxNCwicGF0aCI6Ii8yODYxNjIxOS80NjM2OTQ4MzktYmIxMTRmOWYtMjRjNS00MDAwLWE5ODQtYzEwZDE4N2RhNWEwLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDEzMjAxNFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTI4ZTI1MGEwMWM2MjA1ZTc4YWNkOWQ0YTVjMjY2YWU0Njg4YzBjZmQ3MTUyNWY5ZGFjN2RhZjBmOTI5YjBmMzgmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.pkNCv5IIYOyifO9etSN2hv3p65Eu2uZaE243UlCqGFI)

### MCP Marketplace

**Discover, Connect, Extend**

Browse a growing library of MCP plugins to expand your AI's capabilities and streamline your workflows effortlessly. Visit [lobehub.com/mcp](https://lobehub.com/mcp) to explore the MCP Marketplace, which offers a curated collection of integrations that enhance your AI's ability to work with various tools and services.

From productivity tools to development environments, discover new ways to extend your AI's reach and effectiveness. Connect with the community and find the perfect plugins for your specific needs.

[![](https://private-user-images.githubusercontent.com/28616219/463695024-a7bac8d3-ea96-4000-bb39-fadc9b610f96.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNDU5MTQsIm5iZiI6MTc3NjM0NTYxNCwicGF0aCI6Ii8yODYxNjIxOS80NjM2OTUwMjQtYTdiYWM4ZDMtZWE5Ni00MDAwLWJiMzktZmFkYzliNjEwZjk2LnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDEzMjAxNFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTE1ZGRjMTBhZTBiOWQ4M2NlZDkzMTBlNmQzNDMyZmUyM2JiNTM0YTdlMGIyOGI2MDNhNGNjYjg4YmZlNWE3OGYmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.5UJivOFUPUelDXpqhdn3n3ADoFN8zAsYUtQabGPWHks)](https://private-user-images.githubusercontent.com/28616219/463695024-a7bac8d3-ea96-4000-bb39-fadc9b610f96.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNDU5MTQsIm5iZiI6MTc3NjM0NTYxNCwicGF0aCI6Ii8yODYxNjIxOS80NjM2OTUwMjQtYTdiYWM4ZDMtZWE5Ni00MDAwLWJiMzktZmFkYzliNjEwZjk2LnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDEzMjAxNFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTE1ZGRjMTBhZTBiOWQ4M2NlZDkzMTBlNmQzNDMyZmUyM2JiNTM0YTdlMGIyOGI2MDNhNGNjYjg4YmZlNWE3OGYmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.5UJivOFUPUelDXpqhdn3n3ADoFN8zAsYUtQabGPWHks)

### Desktop App

**Peak Performance, Zero Distractions**

Get the full LobeHub experience without browser limitations—comprehensive, focused, and always ready to go. Our desktop application provides a dedicated environment for your AI interactions, ensuring optimal performance and minimal distractions.

Experience faster response times, better resource management, and a more stable connection to your AI assistant. The desktop app is designed for users who demand the best performance from their AI tools.

[![](https://private-user-images.githubusercontent.com/28616219/463695530-cfdc48ac-b5f8-4a00-acee-db8f2eba09ad.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNDU5MTQsIm5iZiI6MTc3NjM0NTYxNCwicGF0aCI6Ii8yODYxNjIxOS80NjM2OTU1MzAtY2ZkYzQ4YWMtYjVmOC00YTAwLWFjZWUtZGI4ZjJlYmEwOWFkLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDEzMjAxNFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTkzMzE3NjMxNGIxMDZkMTdkN2JlMzAwMDRiMjdiZjY5NzA5ODg2NDc1ODU0ZTRmMGVkZDdiZjcyNmY4ZjM0ZTQmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.rzCN7qMnabwiNiF9CthupwkWrlAOwvA0XSkdQ_6LoAU)](https://private-user-images.githubusercontent.com/28616219/463695530-cfdc48ac-b5f8-4a00-acee-db8f2eba09ad.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNDU5MTQsIm5iZiI6MTc3NjM0NTYxNCwicGF0aCI6Ii8yODYxNjIxOS80NjM2OTU1MzAtY2ZkYzQ4YWMtYjVmOC00YTAwLWFjZWUtZGI4ZjJlYmEwOWFkLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDEzMjAxNFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTkzMzE3NjMxNGIxMDZkMTdkN2JlMzAwMDRiMjdiZjY5NzA5ODg2NDc1ODU0ZTRmMGVkZDdiZjcyNmY4ZjM0ZTQmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.rzCN7qMnabwiNiF9CthupwkWrlAOwvA0XSkdQ_6LoAU)

### Smart Internet Search

**Online Knowledge On Demand**

With real-time internet access, your AI keeps up with the world—news, data, trends, and more. Stay informed and get the most current information available, enabling your AI to provide accurate and up-to-date responses.

Access live information, verify facts, and explore current events without leaving your conversation. Your AI becomes a gateway to the world's knowledge, always current and comprehensive.

[![](https://private-user-images.githubusercontent.com/17870709/413550607-f74f1139-d115-4e9c-8c43-040a53797a5e.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNDU5MTQsIm5iZiI6MTc3NjM0NTYxNCwicGF0aCI6Ii8xNzg3MDcwOS80MTM1NTA2MDctZjc0ZjExMzktZDExNS00ZTljLThjNDMtMDQwYTUzNzk3YTVlLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDEzMjAxNFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWFiZjIxZTlkOWM1MTUzODFhNTA2YjJjODZiY2Y2MmQ2NWI1YzQxMTM1ZmFiOWMyMWFlMjk5YzU2MjBkM2VmZjQmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.awDiG6q-REyD3JLO3dcxea_smslKSnfvXBtUOJnP7PA)](https://lobehub.com/docs/usage/features/cot)

### Chain of Thought

Experience AI reasoning like never before. Watch as complex problems unfold step by step through our innovative Chain of Thought (CoT) visualization. This breakthrough feature provides unprecedented transparency into AI's decision-making process, allowing you to observe how conclusions are reached in real-time.

By breaking down complex reasoning into clear, logical steps, you can better understand and validate the AI's problem-solving approach. Whether you're debugging, learning, or simply curious about AI reasoning, CoT visualization transforms abstract thinking into an engaging, interactive experience.

[![](https://private-user-images.githubusercontent.com/17870709/413551442-92f72082-02bd-4835-9c54-b089aad7fd41.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNDU5MTQsIm5iZiI6MTc3NjM0NTYxNCwicGF0aCI6Ii8xNzg3MDcwOS80MTM1NTE0NDItOTJmNzIwODItMDJiZC00ODM1LTljNTQtYjA4OWFhZDdmZDQxLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDEzMjAxNFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTQyOTc4MjRmNmM5ZGNiMDI3Y2RkMTdmMzEyZGU3ZTVhN2Y1MDc5ZWU2NWNmZTJkNDNjZmVlMDY4ZWFhYmYzZGYmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.W-xbCpHRqXCLs3jloOyU6Yt5vHzHlTIVz-kLFczxOMk)](https://lobehub.com/docs/usage/features/branching-conversations)

### Branching Conversations

Introducing a more natural and flexible way to chat with AI. With Branch Conversations, your discussions can flow in multiple directions, just like human conversations do. Create new conversation branches from any message, giving you the freedom to explore different paths while preserving the original context.

Choose between two powerful modes:

- **Continuation Mode:** Seamlessly extend your current discussion while maintaining valuable context
- **Standalone Mode:** Start fresh with a new topic based on any previous message

This groundbreaking feature transforms linear conversations into dynamic, tree-like structures, enabling deeper exploration of ideas and more productive interactions.

[![](https://private-user-images.githubusercontent.com/17870709/413551580-7f95fad6-b210-4e6e-84a0-7f39e96f3a00.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNDU5MTQsIm5iZiI6MTc3NjM0NTYxNCwicGF0aCI6Ii8xNzg3MDcwOS80MTM1NTE1ODAtN2Y5NWZhZDYtYjIxMC00ZTZlLTg0YTAtN2YzOWU5NmYzYTAwLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDEzMjAxNFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWIwZGViOGZjY2RiOWQ0NzMwNjlhZDE0OTJiOTMzOGUyZWNjYWY3MGUzZDc4NjRlZmMwMTk1NTJiMTg3Mzk3ZGYmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.hHt2PRyZWpx9GW7oHl1DROJrMSKUD0sdLq3KGFYjpj0)](https://lobehub.com/docs/usage/features/artifacts)

### Artifacts Support

Experience the power of Claude Artifacts, now integrated into LobeHub. This revolutionary feature expands the boundaries of AI-human interaction, enabling real-time creation and visualization of diverse content formats.

Create and visualize with unprecedented flexibility:

- Generate and display dynamic SVG graphics
- Build and render interactive HTML pages in real-time
- Produce professional documents in multiple formats

[![](https://private-user-images.githubusercontent.com/34400653/411257914-7da7a3b2-92fd-4630-9f4e-8560c74955ae.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNDU5MTQsIm5iZiI6MTc3NjM0NTYxNCwicGF0aCI6Ii8zNDQwMDY1My80MTEyNTc5MTQtN2RhN2EzYjItOTJmZC00NjMwLTlmNGUtODU2MGM3NDk1NWFlLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDEzMjAxNFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWQwMThlYzBiY2Y3MjUyYzA1ZGU1NThmOGM4OWMyMTBjODdiNjQxNTUxOGU4OWU5YmU0ZTI2NjFhZDdmN2NlYjgmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.BGm36A4YxLh0N8VYCssYD-LcnqpTF6_5X1TzC84tCKc)](https://lobehub.com/blog/knowledge-base)

### File Upload /Knowledge Base

LobeHub supports file upload and knowledge base functionality. You can upload various types of files including documents, images, audio, and video, as well as create knowledge bases, making it convenient for users to manage and search for files. Additionally, you can utilize files and knowledge base features during conversations, enabling a richer dialogue experience.

chat.pdf.mp4<video src="https://private-user-images.githubusercontent.com/28616219/363406445-faa8cf67-e743-4590-8bf6-ebf6ccc34175.mp4?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNDU5MTQsIm5iZiI6MTc3NjM0NTYxNCwicGF0aCI6Ii8yODYxNjIxOS8zNjM0MDY0NDUtZmFhOGNmNjctZTc0My00NTkwLThiZjYtZWJmNmNjYzM0MTc1Lm1wND9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDEzMjAxNFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWJhMGY0NjliMGRkNWI3Mjc1Yzc1YmQ5YjlmMGJkNjIwYzMxZDgxM2JmMjc1NDBmMDQ0MDI5N2JmNTAyY2UyZmQmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT12aWRlbyUyRm1wNCJ9.MzlKLXqK055U8-Z6o1VEElYd2g33R1eFhttc5fr1nss" controls="controls"></video>

> \[!TIP\]
> 
> Learn more on [📘 LobeHub Knowledge Base Launch — From Now On, Every Step Counts](https://lobehub.com/blog/knowledge-base)

[![](https://private-user-images.githubusercontent.com/34400653/411259144-e553e407-42de-4919-977d-7dbfcf44a821.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNDU5MTQsIm5iZiI6MTc3NjM0NTYxNCwicGF0aCI6Ii8zNDQwMDY1My80MTEyNTkxNDQtZTU1M2U0MDctNDJkZS00OTE5LTk3N2QtN2RiZmNmNDRhODIxLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDEzMjAxNFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWI2ZmQwMDc4NmFhYjM3NjNiZGZiODYzZWQ0YWY2ZjJlMDAxNDRkZDFhYTk2M2VlMWExZDFiY2MyZGM5MDA1ZjImWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.NV6ppVGHON3b4lGQMd30_ke0ZJ--mRCAyoG2onmXcRk)](https://lobehub.com/docs/usage/features/multi-ai-providers)

### Multi-Model Service Provider Support

In the continuous development of LobeHub, we deeply understand the importance of diversity in model service providers for meeting the needs of the community when providing AI conversation services. Therefore, we have expanded our support to multiple model service providers, rather than being limited to a single one, in order to offer users a more diverse and rich selection of conversations.

In this way, LobeHub can more flexibly adapt to the needs of different users, while also providing developers with a wider range of choices.

#### Supported Model Service Providers

We have implemented support for the following model service providers:

See more providers (+-10)

> 📊 Total providers: [**0**](https://lobechat.com/discover/providers)

At the same time, we are also planning to support more model service providers. If you would like LobeHub to support your favorite service provider, feel free to join our [💬 community discussion](https://github.com/lobehub/lobehub/discussions/1284).

[![](https://private-user-images.githubusercontent.com/34400653/411257887-1239da50-d832-4632-a7ef-bd754c0f3850.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNDU5MTQsIm5iZiI6MTc3NjM0NTYxNCwicGF0aCI6Ii8zNDQwMDY1My80MTEyNTc4ODctMTIzOWRhNTAtZDgzMi00NjMyLWE3ZWYtYmQ3NTRjMGYzODUwLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDEzMjAxNFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTljNTBjNTVkMmE5MTdjNWUxY2ZiN2JiMzNkNWUyOTU4MDg5OTYyNmM1YTk0NDAzNDBkNzk4MTc2ZmQ0OWE5NTEmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.jD3b0GJ_Zg1cUrvFrjpejQ2XBjRtOllA-aYNmEQzbag)](https://lobehub.com/docs/usage/features/local-llm)

### Local Large Language Model (LLM) Support

To meet the specific needs of users, LobeHub also supports the use of local models based on [Ollama](https://ollama.ai/), allowing users to flexibly use their own or third-party models.

> \[!TIP\]
> 
> Learn more about [📘 Using Ollama in LobeHub](https://lobehub.com/docs/usage/providers/ollama) by checking it out.

[![](https://private-user-images.githubusercontent.com/17870709/413550908-18574a1f-46c2-4cbc-af2c-35a86e128a07.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNDU5MTQsIm5iZiI6MTc3NjM0NTYxNCwicGF0aCI6Ii8xNzg3MDcwOS80MTM1NTA5MDgtMTg1NzRhMWYtNDZjMi00Y2JjLWFmMmMtMzVhODZlMTI4YTA3LnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDEzMjAxNFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTk5MGJjNzVhM2RjM2ZhZjMzYzlkYzJlM2U1N2YyMTFmZjA1ODkzZDM1ZTA0YWFlMTc1MGJmNDIyMWU3MDcyM2UmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.5i70jDx_fFS6OT7kHnzmeb5ZYqVu1a3SYhtaWzcIQPc)](https://lobehub.com/docs/usage/features/vision)

### Model Visual Recognition

LobeHub now supports OpenAI's latest [`gpt-4-vision`](https://platform.openai.com/docs/guides/vision) model with visual recognition capabilities, a multimodal intelligence that can perceive visuals. Users can easily upload or drag and drop images into the dialogue box, and the agent will be able to recognize the content of the images and engage in intelligent conversation based on this, creating smarter and more diversified chat scenarios.

This feature opens up new interactive methods, allowing communication to transcend text and include a wealth of visual elements. Whether it's sharing images in daily use or interpreting images within specific industries, the agent provides an outstanding conversational experience.

[![](https://private-user-images.githubusercontent.com/34400653/411259401-50189597-2cc3-4002-b4c8-756a52ad5c0a.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNDU5MTQsIm5iZiI6MTc3NjM0NTYxNCwicGF0aCI6Ii8zNDQwMDY1My80MTEyNTk0MDEtNTAxODk1OTctMmNjMy00MDAyLWI0YzgtNzU2YTUyYWQ1YzBhLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDEzMjAxNFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWIwYzg4ZjQ0ODFlYjMxZDY3MzYzOWYyMjBhNDEzY2E4NDFhYzczMmEwOGVlZDFlMzk5ZTFiN2QyYzgwZWEyOTAmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.Zbaq7vAv9HvASsIeQt2JZaBqNi_363No1OIoZ4hkht4)](https://lobehub.com/docs/usage/features/tts)

### TTS & STT Voice Conversation

LobeHub supports Text-to-Speech (TTS) and Speech-to-Text (STT) technologies, enabling our application to convert text messages into clear voice outputs, allowing users to interact with our conversational agent as if they were talking to a real person. Users can choose from a variety of voices to pair with the agent.

Moreover, TTS offers an excellent solution for those who prefer auditory learning or desire to receive information while busy. In LobeHub, we have meticulously selected a range of high-quality voice options (OpenAI Audio, Microsoft Edge Speech) to meet the needs of users from different regions and cultural backgrounds. Users can choose the voice that suits their personal preferences or specific scenarios, resulting in a personalized communication experience.

[![](https://private-user-images.githubusercontent.com/34400653/411259372-708274a7-2458-494b-a6ec-b73dfa1fa7c2.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNDU5MTQsIm5iZiI6MTc3NjM0NTYxNCwicGF0aCI6Ii8zNDQwMDY1My80MTEyNTkzNzItNzA4Mjc0YTctMjQ1OC00OTRiLWE2ZWMtYjczZGZhMWZhN2MyLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDEzMjAxNFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTZmOTQ0YTFkNmI2NGI3YmIxMTIwMzYxYmM0NTRkZTVjZTcxYjE0ZDY1ZTFhMDkwNDIyMjNlNTUzMTgxMTk1MzAmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.ayKEr2bbqScZRXB1N6MEBMOIAwYiUKYdJB98b4WWb_E)](https://lobehub.com/docs/usage/features/text-to-image)

### Text to Image Generation

With support for the latest text-to-image generation technology, LobeHub now allows users to invoke image creation tools directly within conversations with the agent. By leveraging the capabilities of AI tools such as [`DALL-E 3`](https://openai.com/dall-e-3), [`MidJourney`](https://www.midjourney.com/), and [`Pollinations`](https://pollinations.ai/), the agents are now equipped to transform your ideas into images.

This enables a more private and immersive creative process, allowing for the seamless integration of visual storytelling into your personal dialogue with the agent.

[![](https://private-user-images.githubusercontent.com/34400653/411257826-66a891ac-01b6-4e3f-b978-2eb07b489b1b.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNDU5MTQsIm5iZiI6MTc3NjM0NTYxNCwicGF0aCI6Ii8zNDQwMDY1My80MTEyNTc4MjYtNjZhODkxYWMtMDFiNi00ZTNmLWI5NzgtMmViMDdiNDg5YjFiLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDEzMjAxNFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTY3N2ZlZTEyMzRiZDVkOTIwNDNkNWY1NThiYmZmZTc1ZjcyZWUxMTU3Yzg0ZDM0ODgxNjkxNTJiYjAyYjkyMWEmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.PzJc-MZT67PqKm15oZ6GMKQTPaEBOSqzsfCuMOssZpE)](https://lobehub.com/docs/usage/features/plugin-system)

### Plugin System (Function Calling)

The plugin ecosystem of LobeHub is an important extension of its core functionality, greatly enhancing the practicality and flexibility of the LobeHub assistant.

Plugin-Demo.mp4<video src="https://github.com/lobehub/lobehub/assets/28616219/f29475a3-f346-4196-a435-41a6373ab9e2" controls="controls"></video>

By utilizing plugins, LobeHub assistants can obtain and process real-time information, such as searching for web information and providing users with instant and relevant news.

In addition, these plugins are not limited to news aggregation, but can also extend to other practical functions, such as quickly searching documents, generating images, obtaining data from various platforms like Bilibili, Steam, and interacting with various third-party services.

> \[!TIP\]
> 
> Learn more about [📘 Plugin Usage](https://lobehub.com/docs/usage/plugins/basic) by checking it out.

| Recent Submits | Description |
| --- | --- |
| [Shopping tools](https://lobechat.com/discover/plugin/ShoppingTools)   <sup>By <strong>shoppingtools</strong> on <strong>2026-01-12</strong></sup> | Search for products on eBay & AliExpress, find eBay events & coupons. Get prompt examples.   `shopping` `e-bay` `ali-express` `coupons` |
| [SEO Assistant](https://lobechat.com/discover/plugin/seo_assistant)   <sup>By <strong>webfx</strong> on <strong>2026-01-12</strong></sup> | The SEO Assistant can generate search engine keyword information in order to aid the creation of content.   `seo` `keyword` |
| [Video Captions](https://lobechat.com/discover/plugin/VideoCaptions)   <sup>By <strong>maila</strong> on <strong>2025-12-13</strong></sup> | Convert Youtube links into transcribed text, enable asking questions, create chapters, and summarize its content.   `video-to-text` `youtube` |
| [WeatherGPT](https://lobechat.com/discover/plugin/WeatherGPT)   <sup>By <strong>steven-tey</strong> on <strong>2025-12-13</strong></sup> | Get current weather information for a specific location.   `weather` |

> 📊 Total plugins: [**40**](https://lobechat.com/discover/plugins)

[![](https://private-user-images.githubusercontent.com/17870709/413551032-b3ab6e35-4fbc-468d-af10-e3e0c687350f.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNDU5MTQsIm5iZiI6MTc3NjM0NTYxNCwicGF0aCI6Ii8xNzg3MDcwOS80MTM1NTEwMzItYjNhYjZlMzUtNGZiYy00NjhkLWFmMTAtZTNlMGM2ODczNTBmLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDEzMjAxNFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTgyZDViZGUxMGRkMDRiMjVhZTU5ZjAyODVkYzEwMDAzOGQ2ZmI5MmM5M2RiMzk1ZDI4MjQ4ZjdkZjNmNTI3NzkmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.M_ek2jH8c3Kl2xtF-W2oM0Imdz5Fsq5WUurJ9NNK3Y0)](https://lobehub.com/docs/usage/features/agent-market)

### Agent Market (GPTs)

In LobeHub Agent Marketplace, creators can discover a vibrant and innovative community that brings together a multitude of well-designed agents, which not only play an important role in work scenarios but also offer great convenience in learning processes. Our marketplace is not just a showcase platform but also a collaborative space. Here, everyone can contribute their wisdom and share the agents they have developed.

> \[!TIP\]
> 
> By [🤖/🏪 Submit Agents](https://github.com/lobehub/lobe-chat-agents), you can easily submit your agent creations to our platform. Importantly, LobeHub has established a sophisticated automated internationalization (i18n) workflow, capable of seamlessly translating your agent into multiple language versions. This means that no matter what language your users speak, they can experience your agent without barriers.

> \[!IMPORTANT\]
> 
> We welcome all users to join this growing ecosystem and participate in the iteration and optimization of agents. Together, we can create more interesting, practical, and innovative agents, further enriching the diversity and practicality of the agent offerings.

| Recent Submits | Description |
| --- | --- |
| [Turtle Soup Host](https://lobechat.com/discover/assistant/lateral-thinking-puzzle)   <sup>By <strong><a href="https://github.com/CSY2022">CSY2022</a></strong> on <strong>2025-06-19</strong></sup> | A turtle soup host needs to provide the scenario, the complete story (truth of the event), and the key point (the condition for guessing correctly).   `turtle-soup` `reasoning` `interaction` `puzzle` `role-playing` |
| [Academic Writing Assistant](https://lobechat.com/discover/assistant/academic-writing-assistant)   <sup>By <strong><a href="https://github.com/swarfte">swarfte</a></strong> on <strong>2025-06-17</strong></sup> | Expert in academic research paper writing and formal documentation   `academic-writing` `research` `formal-style` |
| [Gourmet Reviewer🍟](https://lobechat.com/discover/assistant/food-reviewer)   <sup>By <strong><a href="https://github.com/renhai-lab">renhai-lab</a></strong> on <strong>2025-06-17</strong></sup> | Food critique expert   `gourmet` `review` `writing` |
| [Minecraft Senior Developer](https://lobechat.com/discover/assistant/java-development)   <sup>By <strong><a href="https://github.com/iamyuuk">iamyuuk</a></strong> on <strong>2025-06-17</strong></sup> | Expert in advanced Java development and Minecraft mod and server plugin development   `development` `programming` `minecraft` `java` |

> 📊 Total agents: [**505**](https://lobechat.com/discover/assistants)

[![](https://private-user-images.githubusercontent.com/34400653/411259251-f1697c8b-d1fb-4dac-ba05-153c6295d91d.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNDU5MTQsIm5iZiI6MTc3NjM0NTYxNCwicGF0aCI6Ii8zNDQwMDY1My80MTEyNTkyNTEtZjE2OTdjOGItZDFmYi00ZGFjLWJhMDUtMTUzYzYyOTVkOTFkLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDEzMjAxNFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTY1YjVhZWI4Y2NkYTU3MzY1ZjgzY2VkYTU1ZTg3NjJjMzU3YTg3NDJjZDlhYjVhNzJlZDUyZGEyMGY4OTViYmYmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.pc9xktw2_rVCDXdJJqwVsknwQaBmQE8m405RZLZGOIw)](https://lobehub.com/docs/usage/features/database)

### Support Local / Remote Database

LobeHub supports the use of both server-side and local databases. Depending on your needs, you can choose the appropriate deployment solution:

- **Local database**: suitable for users who want more control over their data and privacy protection. LobeHub uses CRDT (Conflict-Free Replicated Data Type) technology to achieve multi-device synchronization. This is an experimental feature aimed at providing a seamless data synchronization experience.
- **Server-side database**: suitable for users who want a more convenient user experience. LobeHub supports PostgreSQL as a server-side database. For detailed documentation on how to configure the server-side database, please visit [Configure Server-side Database](https://lobehub.com/docs/self-hosting/advanced/server-database).

Regardless of which database you choose, LobeHub can provide you with an excellent user experience.

[![](https://private-user-images.githubusercontent.com/34400653/411257957-80bb232e-19d1-4f97-98d6-e291f3585e6d.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNDU5MTQsIm5iZiI6MTc3NjM0NTYxNCwicGF0aCI6Ii8zNDQwMDY1My80MTEyNTc5NTctODBiYjIzMmUtMTlkMS00Zjk3LTk4ZDYtZTI5MWYzNTg1ZTZkLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDEzMjAxNFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTI2N2MxMmEyZmE0ZTE5NjMyNTZkZjZlZDJjY2MwMzkzYzZhZGJjNzRmZWI4YjMyNDk3MjJmZjY2OWRiYTBhOWQmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.f0SBPmZKFB5JSfEQe1dctYFKFutUqCAwtZizbaYN-hA)](https://lobehub.com/docs/usage/features/auth)

### Support Multi-User Management

LobeHub supports multi-user management and provides flexible user authentication solutions:

- **Better Auth**: LobeHub integrates `Better Auth`, a modern and flexible authentication library that supports multiple authentication methods, including OAuth, email login, credential login, magic links, and more. With `Better Auth`, you can easily implement user registration, login, session management, social login, multi-factor authentication (MFA), and other functions to ensure the security and privacy of user data.

[![](https://private-user-images.githubusercontent.com/34400653/411259329-9647f70f-b71b-43b6-9564-7cdd12d1c24d.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNDU5MTQsIm5iZiI6MTc3NjM0NTYxNCwicGF0aCI6Ii8zNDQwMDY1My80MTEyNTkzMjktOTY0N2Y3MGYtYjcxYi00M2I2LTk1NjQtN2NkZDEyZDFjMjRkLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDEzMjAxNFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWJiODUwYzFmNjE4YTJmYjMyMzc4NmMxZjM2MWRkNDI3NGIzM2RhZTI4ZDlhMDNkNzBmN2RlYzViM2E0ZDMxNmYmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.Yrj8Ih8rP9aMwbVX1iABKkPvwPbnoQ08DI4asx6_yd0)](https://lobehub.com/docs/usage/features/pwa)

### Progressive Web App (PWA)

We deeply understand the importance of providing a seamless experience for users in today's multi-device environment. Therefore, we have adopted Progressive Web Application ([PWA](https://support.google.com/chrome/answer/9658361)) technology, a modern web technology that elevates web applications to an experience close to that of native apps.

Through PWA, LobeHub can offer a highly optimized user experience on both desktop and mobile devices while maintaining high-performance characteristics. Visually and in terms of feel, we have also meticulously designed the interface to ensure it is indistinguishable from native apps, providing smooth animations, responsive layouts, and adapting to different device screen resolutions.

> \[!NOTE\]
> 
> If you are unfamiliar with the installation process of PWA, you can add LobeHub as your desktop application (also applicable to mobile devices) by following these steps:
> 
> - Launch the Chrome or Edge browser on your computer.
> - Visit the LobeHub webpage.
> - In the upper right corner of the address bar, click on the Install icon.
> - Follow the instructions on the screen to complete the PWA Installation.

[![](https://private-user-images.githubusercontent.com/34400653/411257845-32cf43c4-96bd-4a4c-bfb6-59acde6fe380.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNDU5MTQsIm5iZiI6MTc3NjM0NTYxNCwicGF0aCI6Ii8zNDQwMDY1My80MTEyNTc4NDUtMzJjZjQzYzQtOTZiZC00YTRjLWJmYjYtNTlhY2RlNmZlMzgwLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDEzMjAxNFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWVhMWU3NWEzOTQ5ZmEzMGZjYzc1OThmZjA5MzYyMGRmYWM0OWZlNDA0ZTg1NjhjNWNkZjExM2RlYmFiMmVmZjAmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.T4CwMEr4lPgsDUDlTh4oU1w10TqGGWC5vKEXE4YZkgo)](https://lobehub.com/docs/usage/features/mobile)

### Mobile Device Adaptation

We have carried out a series of optimization designs for mobile devices to enhance the user's mobile experience. Currently, we are iterating on the mobile user experience to achieve smoother and more intuitive interactions. If you have any suggestions or ideas, we welcome you to provide feedback through GitHub Issues or Pull Requests.

[![](https://private-user-images.githubusercontent.com/34400653/411259389-b47c39f1-806f-492b-8fcb-b0fa973937c1.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNDU5MTQsIm5iZiI6MTc3NjM0NTYxNCwicGF0aCI6Ii8zNDQwMDY1My80MTEyNTkzODktYjQ3YzM5ZjEtODA2Zi00OTJiLThmY2ItYjBmYTk3MzkzN2MxLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDEzMjAxNFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWU4NTg0YzNjYjQ0OTZiMmMzZjE2ZDRmYmIwMmVkZmNkMWEzZGY0ODM0ZDQ5N2QyY2ZlYmViZWQ4YmM4MjU3Y2ImWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.38TNfIqKlgqd1iJlNfjlMwmB438sz2JKWgcwaTZ0a9Q)](https://lobehub.com/docs/usage/features/theme)

### Custom Themes

As a design-engineering-oriented application, LobeHub places great emphasis on users' personalized experiences, hence introducing flexible and diverse theme modes, including a light mode for daytime and a dark mode for nighttime. Beyond switching theme modes, a range of color customization options allow users to adjust the application's theme colors according to their preferences. Whether it's a desire for a sober dark blue, a lively peach pink, or a professional gray-white, users can find their style of color choices in LobeHub.

> \[!TIP\]
> 
> The default configuration can intelligently recognize the user's system color mode and automatically switch themes to ensure a consistent visual experience with the operating system. For users who like to manually control details, LobeHub also offers intuitive setting options and a choice between chat bubble mode and document mode for conversation scenarios.

### \* What's more

Beside these features, LobeHub also have much better basic technique underground:

- 💨 **Quick Deployment**: Using the Vercel platform or docker image, you can deploy with just one click and complete the process within 1 minute without any complex configuration.
- 🌐 **Custom Domain**: If users have their own domain, they can bind it to the platform for quick access to the dialogue agent from anywhere.
- 🔒 **Privacy Protection**: All data is stored locally in the user's browser, ensuring user privacy.
- 💎 **Exquisite UI Design**: With a carefully designed interface, it offers an elegant appearance and smooth interaction. It supports light and dark themes and is mobile-friendly. PWA support provides a more native-like experience.
- 🗣️ **Smooth Conversation Experience**: Fluid responses ensure a smooth conversation experience. It fully supports Markdown rendering, including code highlighting, LaTex formulas, Mermaid flowcharts, and more.

> ✨ more features will be added when LobeHub evolve.

## 🛳 Self Hosting

LobeHub provides Self-Hosted Version with Vercel, Alibaba Cloud, and [Docker Image](https://hub.docker.com/r/lobehub/lobehub). This allows you to deploy your own chatbot within a few minutes without any prior knowledge.

> [!tip] Tip
> Learn more about [📘 Build your own LobeHub](https://lobehub.com/docs/self-hosting/start) by checking it out.

### A Deploying with Vercel, Zeabur, Sealos or Alibaba Cloud

"If you want to deploy this service yourself on Vercel, Zeabur or Alibaba Cloud, you can follow these steps:

- Prepare your [OpenAI API Key](https://platform.openai.com/account/api-keys).
- Click the button below to start deployment: Log in directly with your GitHub account, and remember to fill in the `OPENAI_API_KEY` (required) on the environment variable section.
- After deployment, you can start using it.
- Bind a custom domain (optional): The DNS of the domain assigned by Vercel is polluted in some areas; binding a custom domain can connect directly.

| Deploy with Vercel | Deploy with Zeabur | Deploy with Sealos | Deploy with RepoCloud | Deploy with Alibaba Cloud |
| --- | --- | --- | --- | --- |
|  |  |  | [![](https://camo.githubusercontent.com/bb59e7a3c986f97daed8cee9518a0e5edf7567e1b7823158ea3f946ef15768db/68747470733a2f2f64313674307063343834367835322e636c6f756466726f6e742e6e65742f6465706c6f796c6f62652e737667)](https://repocloud.io/details/?app_id=248) |  |

#### After Fork

After fork, only retain the upstream sync action and disable other actions in your repository on GitHub.

#### Keep Updated

If you have deployed your own project following the one-click deployment steps in the README, you might encounter constant prompts indicating "updates available." This is because Vercel defaults to creating a new project instead of forking this one, resulting in an inability to detect updates accurately.

> [!tip] Tip
> We suggest you redeploy using the following steps, [📘 Auto Sync With Latest](https://lobehub.com/docs/self-hosting/advanced/upstream-sync)

  

### B Deploying with Docker

We provide a Docker image for deploying the LobeHub service on your own private device. Use the following command to start the LobeHub service:

1. create a folder to for storage files
```
$ mkdir lobehub-db && cd lobehub-db
```
1. init the LobeHub infrastructure
```
bash <(curl -fsSL https://lobe.li/setup.sh)
```
1. Start the LobeHub service
```
docker compose up -d
```

> [!note] Note
> For detailed instructions on deploying with Docker, please refer to the [📘 Docker Deployment Guide](https://lobehub.com/docs/self-hosting/server-database/docker-compose)

  

### Environment Variable

This project provides some additional configuration items set with environment variables:

| Environment Variable | Required | Description | Example |
| --- | --- | --- | --- |
| `OPENAI_API_KEY` | Yes | This is the API key you apply on the OpenAI account page | `sk-xxxxxx...xxxxxx` |
| `OPENAI_PROXY_URL` | No | If you manually configure the OpenAI interface proxy, you can use this configuration item to override the default OpenAI API request base URL | `https://api.chatanywhere.cn` or `https://aihubmix.com/v1`   The default value is   `https://api.openai.com/v1` |
| `OPENAI_MODEL_LIST` | No | Used to control the model list. Use `+` to add a model, `-` to hide a model, and `model_name=display_name` to customize the display name of a model, separated by commas. | `qwen-7b-chat,+glm-6b,-gpt-3.5-turbo` |

> [!note] Note
> The complete list of environment variables can be found in the [📘 Environment Variables](https://lobehub.com/docs/self-hosting/environment-variables)

## 📦 Ecosystem

| NPM | Repository | Description | Version |
| --- | --- | --- | --- |
| [@lobehub/ui](https://www.npmjs.com/package/@lobehub/ui) | [lobehub/lobe-ui](https://github.com/lobehub/lobe-ui) | Open-source UI component library dedicated to building AIGC web applications. |  |
| [@lobehub/icons](https://www.npmjs.com/package/@lobehub/icons) | [lobehub/lobe-icons](https://github.com/lobehub/lobe-icons) | Popular AI / LLM Model Brand SVG Logo and Icon Collection. |  |
| [@lobehub/tts](https://www.npmjs.com/package/@lobehub/tts) | [lobehub/lobe-tts](https://github.com/lobehub/lobe-tts) | High-quality & reliable TTS/STT React Hooks library |  |
| [@lobehub/lint](https://www.npmjs.com/package/@lobehub/lint) | [lobehub/lobe-lint](https://github.com/lobehub/lobe-lint) | Configurations for ESlint, Stylelint, Commitlint, Prettier, Remark, and Semantic Release for LobeHub. |  |

## 🧩 Plugins

Plugins provide a means to extend the [Function Calling](https://lobehub.com/blog/openai-function-call) capabilities of LobeHub. They can be used to introduce new function calls and even new ways to render message results. If you are interested in plugin development, please refer to our [📘 Plugin Development Guide](https://lobehub.com/docs/usage/plugins/development) in the Wiki.

- [lobe-chat-plugins](https://github.com/lobehub/lobe-chat-plugins): This is the plugin index for LobeHub. It accesses index.json from this repository to display a list of available plugins for LobeHub to the user.
- [chat-plugin-template](https://github.com/lobehub/chat-plugin-template): This is the plugin template for LobeHub plugin development.
- [@lobehub/chat-plugin-sdk](https://github.com/lobehub/chat-plugin-sdk): The LobeHub Plugin SDK assists you in creating exceptional chat plugins for LobeHub.
- [@lobehub/chat-plugins-gateway](https://github.com/lobehub/chat-plugins-gateway): The LobeHub Plugins Gateway is a backend service that provides a gateway for LobeHub plugins. We deploy this service using Vercel. The primary API POST /api/v1/runner is deployed as an Edge Function.

> [!note] Note
> The plugin system is currently undergoing major development. You can learn more in the following issues:
> 
> - [**Plugin Phase 1**](https://github.com/lobehub/lobehub/issues/73): Implement separation of the plugin from the main body, split the plugin into an independent repository for maintenance, and realize dynamic loading of the plugin.
> - [**Plugin Phase 2**](https://github.com/lobehub/lobehub/issues/97): The security and stability of the plugin's use, more accurately presenting abnormal states, the maintainability of the plugin architecture, and developer-friendly.
> - [**Plugin Phase 3**](https://github.com/lobehub/lobehub/issues/149): Higher-level and more comprehensive customization capabilities, support for plugin authentication, and examples.

## ⌨️ Local Development

You can use GitHub Codespaces for online development:

Or clone it for local development:

```
$ git clone https://github.com/lobehub/lobehub.git
$ cd lobehub
$ pnpm install
$ pnpm dev          # Full-stack (Next.js + Vite SPA)
$ bun run dev:spa   # SPA frontend only (port 9876)
```

> **Debug Proxy**: After running `dev:spa`, the terminal prints a proxy URL like `https://app.lobehub.com/_dangerous_local_dev_proxy?debug-host=http%3A%2F%2Flocalhost%3A9876`. Open it to develop locally against the production backend with HMR.

If you would like to learn more details, please feel free to look at our [📘 Development Guide](https://lobehub.com/docs/development/start).

## 🤝 Contributing

Contributions of all types are more than welcome; if you are interested in contributing code, feel free to check out our GitHub [Issues](https://github.com/lobehub/lobehub/issues) and [Projects](https://github.com/lobehub/lobehub/projects) to get stuck in to show us what you're made of.

> [!tip] Tip
> We are creating a technology-driven forum, fostering knowledge interaction and the exchange of ideas that may culminate in mutual inspiration and collaborative innovation.
> 
> Help us make LobeHub better. Welcome to provide product design feedback, user experience discussions directly to us.
> 
> **Principal Maintainers:** [@arvinxx](https://github.com/arvinxx) [@canisminor1990](https://github.com/canisminor1990)

[

<table><tbody><tr><th colspan="2"><br><a href="https://camo.githubusercontent.com/03d457c0b09b6acbe1395a4e7b632ee6b0d6de683c67225319d3418053851e66/68747470733a2f2f636f6e747269622e726f636b732f696d6167653f7265706f3d6c6f62656875622f6c6f6265687562"><img src="https://camo.githubusercontent.com/03d457c0b09b6acbe1395a4e7b632ee6b0d6de683c67225319d3418053851e66/68747470733a2f2f636f6e747269622e726f636b732f696d6167653f7265706f3d6c6f62656875622f6c6f6265687562"></a><br><br></th></tr><tr><td><themed-picture><picture><img src="https://camo.githubusercontent.com/0f10bdb1729fb8065ddccc170632abc69a9e9aee6d1db3720f88aad676dac8c1/68747470733a2f2f6e6578742e6f7373696e73696768742e696f2f776964676574732f6f6666696369616c2f636f6d706f73652d6f72672d6163746976652d636f6e7472696275746f72732f7468756d626e61696c2e706e673f61637469766974793d61637469766526706572696f643d706173745f32385f64617973266f776e65725f69643d313331343730383332267265706f5f6964733d36343334343532333526696d6167655f73697a653d32783326636f6c6f725f736368656d653d6c69676874"></picture></themed-picture></td><td rowspan="2"><themed-picture><picture><img src="https://camo.githubusercontent.com/86d9c070c2720376338b056778b4c17bed03dcad16bb4bc0e8fedb8f36f1c7e3/68747470733a2f2f6e6578742e6f7373696e73696768742e696f2f776964676574732f6f6666696369616c2f636f6d706f73652d6f72672d7061727469636970616e74732d67726f7774682f7468756d626e61696c2e706e673f61637469766974793d61637469766526706572696f643d706173745f32385f64617973266f776e65725f69643d313331343730383332267265706f5f6964733d36343334343532333526696d6167655f73697a653d34783726636f6c6f725f736368656d653d6c69676874"></picture></themed-picture></td></tr><tr><td><themed-picture><picture><img src="https://camo.githubusercontent.com/0d05309de624152ea680f3f1af9628a0cd1e77dd59246dfbca80c883387b3ceb/68747470733a2f2f6e6578742e6f7373696e73696768742e696f2f776964676574732f6f6666696369616c2f636f6d706f73652d6f72672d6163746976652d636f6e7472696275746f72732f7468756d626e61696c2e706e673f61637469766974793d6e657726706572696f643d706173745f32385f64617973266f776e65725f69643d313331343730383332267265706f5f6964733d36343334343532333526696d6167655f73697a653d32783326636f6c6f725f736368656d653d6c69676874"></picture></themed-picture></td></tr></tbody></table>

](https://github.com/lobehub/lobehub/graphs/contributors)

## ❤️ Sponsor

Every bit counts and your one-time donation sparkles in our galaxy of support! You're a shooting star, making a swift and bright impact on our journey. Thank you for believing in us – your generosity guides us toward our mission, one brilliant flash at a time.

## 🔗 More Products

- **[🅰️ Lobe SD Theme](https://github.com/lobehub/sd-webui-lobe-theme):** Modern theme for Stable Diffusion WebUI, exquisite interface design, highly customizable UI, and efficiency-boosting features.
- **[⛵️ Lobe Midjourney WebUI](https://github.com/lobehub/lobe-midjourney-webui):** WebUI for Midjourney, leverages AI to quickly generate a wide array of rich and diverse images from text prompts, sparking creativity and enhancing conversations.
- **[🌏 Lobe i18n](https://github.com/lobehub/lobe-commit/tree/master/packages/lobe-i18n):** Lobe i18n is an automation tool for the i18n (internationalization) translation process, powered by ChatGPT. It supports features such as automatic splitting of large files, incremental updates, and customization options for the OpenAI model, API proxy, and temperature.
- **[💌 Lobe Commit](https://github.com/lobehub/lobe-commit/tree/master/packages/lobe-commit):** Lobe Commit is a CLI tool that leverages Langchain/ChatGPT to generate Gitmoji-based commit messages.

---

#### 📝 License

[![](https://camo.githubusercontent.com/e4452dd189e4ed4d2c7d74dd6206487d7e9a0caf071c9e5f71f40f90392ade65/68747470733a2f2f6170702e666f7373612e636f6d2f6170692f70726f6a656374732f6769742532426769746875622e636f6d2532466c6f62656875622532466c6f62656875622e7376673f747970653d6c61726765)](https://app.fossa.com/projects/git%2Bgithub.com%2Flobehub%2Flobehub)

Copyright © 2026 [LobeHub](https://github.com/lobehub).  
This project is [LobeHub Community License](https://github.com/lobehub/lobehub/blob/canary/LICENSE) licensed.