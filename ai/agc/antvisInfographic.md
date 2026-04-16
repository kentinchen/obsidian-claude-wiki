---
title: "antvis/Infographic: 🦋 An Infographic Generation and Rendering Framework, bring words to life with AI!"
source: "https://github.com/antvis/infographic"
author:
published:
created: 2026-04-16
description: "🦋 An Infographic Generation and Rendering Framework, bring words to life with AI! - antvis/Infographic"
tags:
  - "clippings"
---
[简体中文](https://github.com/antvis/Infographic/blob/main/README.zh-CN.md) | English

## Infographic, bring words to life!

🦋 An Infographic Generation and Rendering Framework, bring words to life!

[![antvis%2FInfographic | Trendshift](https://camo.githubusercontent.com/9c0aab70ff98e8d8bb1482146c723b70bb3bca0ab58a98cd62dbfb3e4a71cfea/68747470733a2f2f7472656e6473686966742e696f2f6170692f62616467652f7265706f7369746f726965732f3135383338)](https://trendshift.io/repositories/15838)

[![](https://camo.githubusercontent.com/63b394e7eaaafab151fe0a0400bb34852563698fd8b838c148e39a9d3f2fa97a/68747470733a2f2f6d646e2e616c697061796f626a656374732e636f6d2f6875616d65695f7161387178752f616674732f696d672f412a45646b58536f6a4f78717341414141415148414141416741656d4a3741512f6f726967696e616c)](https://camo.githubusercontent.com/63b394e7eaaafab151fe0a0400bb34852563698fd8b838c148e39a9d3f2fa97a/68747470733a2f2f6d646e2e616c697061796f626a656374732e636f6d2f6875616d65695f7161387178752f616674732f696d672f412a45646b58536f6a4f78717341414141415148414141416741656d4a3741512f6f726967696e616c)

**AntV Infographic** is AntV's next-generation **declarative infographic visualization engine**. With a carefully designed infographic syntax, it can quickly and flexibly render high-quality infographics, making information presentation more efficient and data storytelling simpler.

[![AntV Infographic Preview](https://camo.githubusercontent.com/5b932da8069dc0d528386a488e949e0ed7b8860ec42495bfc285d91069bd7f32/68747470733a2f2f6d646e2e616c697061796f626a656374732e636f6d2f6875616d65695f7161387178752f616674732f696d672f412a5a646549535a574875794941414141416245414141416741656d4a3741512f666d742e77656270)](https://camo.githubusercontent.com/5b932da8069dc0d528386a488e949e0ed7b8860ec42495bfc285d91069bd7f32/68747470733a2f2f6d646e2e616c697061796f626a656374732e636f6d2f6875616d65695f7161387178752f616674732f696d672f412a5a646549535a574875794941414141416245414141416741656d4a3741512f666d742e77656270)

## ✨ Features

- 🤖 **AI-friendly**: Configuration and syntax are tuned for AI generation, provide concise prompts, and support AI streaming output and rendering
- 📦 **Ready to use**: ~200 built-in infographic templates, data-item components, and layouts to build professional infographics in minutes
- 🎨 **Theme system**: Hand-drawn, gradients, patterns, multiple preset themes, plus deep customization
- 🧑🏻💻 **Built-in editor**: Includes an editor for infographics so AI-generated results can be edited further
- 📐 **High-quality SVG output**: Renders with SVG by default to ensure visual fidelity and easy editing

## 🚀 Installation

```
npm install @antv/infographic
```

## 📝 Quick Start

```
import { Infographic } from '@antv/infographic';

const infographic = new Infographic({
  container: '#container',
  width: '100%',
  height: '100%',
  editable: true,
});

infographic.render(\`
infographic list-row-simple-horizontal-arrow
data
  lists
    - label Step 1
      desc Start
    - label Step 2
      desc In Progress
    - label Step 3
      desc Complete
\`);
```

The rendered result looks like this:

[![AntV Infographic DEMO](https://camo.githubusercontent.com/db9cb537d4eec51b97376a3b9e3fcad2c8f63702a41eb3bc00aaa6a7b26f9d81/68747470733a2f2f6d646e2e616c697061796f626a656374732e636f6d2f6875616d65695f7161387178752f616674732f696d672f412a75766a385162323646314d41414141415241414141416741656d4a3741512f666d742e77656270)](https://camo.githubusercontent.com/db9cb537d4eec51b97376a3b9e3fcad2c8f63702a41eb3bc00aaa6a7b26f9d81/68747470733a2f2f6d646e2e616c697061796f626a656374732e636f6d2f6875616d65695f7161387178752f616674732f696d672f412a75766a385162323646314d41414141415241414141416741656d4a3741512f666d742e77656270)

## Streaming Rendering

With a highly fault-tolerant infographic syntax you can stream AI output in real time and progressively render the infographic.

```
let buffer = '';
for (const chunk of chunks) {
  buffer += chunk;
  infographic.render(buffer);
}
```

[![AntV Infographic Streaming Rendering](https://camo.githubusercontent.com/fd21c1be10ebcd822c8d79b61954b798d4d7a36a66129fba04fb5cae411b9429/68747470733a2f2f6d646e2e616c697061796f626a656374732e636f6d2f6875616d65695f7161387178752f616674732f696d672f412a655f5046535a725239415141414141415364414141416741656d4a3741512f6f726967696e616c)](https://camo.githubusercontent.com/fd21c1be10ebcd822c8d79b61954b798d4d7a36a66129fba04fb5cae411b9429/68747470733a2f2f6d646e2e616c697061796f626a656374732e636f6d2f6875616d65695f7161387178752f616674732f696d672f412a655f5046535a725239415141414141415364414141416741656d4a3741512f6f726967696e616c)

## 🔧 Skills Integration

AntV Infographic provides skills to integrate with AI agents:

- **infographic-creator**: Create an HTML file that renders an infographic
- **infographic-syntax-creator**: Generate infographic syntax from descriptions
- **infographic-structure-creator**: Generate custom structure designs
- **infographic-item-creator**: Generate custom item designs
- **infographic-template-updater**: (For developers) update the template library

### Claude Code

> Claude marketplace is now available. You can install from marketplace, or keep using manual install.

```
/plugin marketplace add https://github.com/antvis/Infographic.git
/plugin install antv-infographic-skills@antv-infographic
```

Manual install:

```
set -e

VERSION=0.2.4 # Replace with the latest tag, e.g. 0.2.14
BASE_URL=https://github.com/antvis/Infographic/releases/download
mkdir -p .claude/skills

curl -L --fail -o skills.zip "$BASE_URL/$VERSION/skills.zip"
unzip -q -o skills.zip -d .claude/skills
rm -f skills.zip
```

### Codex

> Enter codex

```
# Replace <SKILL> with the skill name, e.g. infographic-creator
# https://github.com/antvis/Infographic/tree/main/skills/<SKILL>
$skill-installer install https://github.com/antvis/Infographic/tree/main/skills/infographic-creator
```

## 🌐 Ecosystem

Community projects and products powered by AntV Infographic:

- 💼 **Products**
	- [Alma](https://alma.now/) — Desktop AI provider orchestration app with Infographic
		- [Chrome Extension](https://github.com/xicilion/markdown-viewer-extension) — Markdown viewer with Infographic support, export to Word
		- [InfographicAI](https://infographic-ai.tuntun.site/) — Generate PPT slides powered by Infographic
		- [LangChat Slides](https://github.com/TyCoding/langchat-slides) — Next-Gen AI Slide Generator using @antv/infographic
		- [Nowledge Mem](https://mem.nowledge.co/) — AI Memory Bank with Presentation Creator supporting Infographic
		- [WeChat Markdown Editor](https://md.doocs.org/) — Markdown to WeChat article editor with Infographic
		- [Welight](https://waer.ltd/) — WeChat article creation platform with Infographic support
		- [Zojo](https://zojo.ai/infographic) — Generate professional infographics with simple syntax
- 📦 **Libraries**
	- [astro-koharu](https://github.com/cosZone/astro-koharu) — Anime blog theme (Astro) with Infographic support
		- [docsify-infographic](https://github.com/bulexu/docsify-infographic) — Plugin to render Infographic diagrams in Docsify
		- [feffery-infographic](https://github.com/HogaStack/feffery-infographic) — Create infographics in Python with Plotly Dash
		- [infographic-cli](https://github.com/lyw405/infographic-cli) — CLI tool to generate SVG infographics
		- [infographic-for-react](https://github.com/lyw405/infographic-for-react) — React component wrapper for @antv/infographic
		- [markdown-it-infographic](https://github.com/hcg1023/markdown-it-infographic) — markdown-it plugin for @antv/infographic
		- [markstream-vue](https://github.com/Simon-He95/markstream-vue) — Streaming Markdown rendering for Vue 3 with Infographic
		- [obsidian-infographic](https://github.com/hcg1023/obsidian-infographic) — Obsidian plugin for @antv/infographic
		- [slidev-addon-infographic](https://github.com/fxss5201/slidev-addon-infographic) — @antv/infographic component for Slidev
		- [VSCode Extension](https://github.com/liwx2000/infographic-vscode-extension) — Preview Infographic in VSCode Markdown files

> 💡 Have a project using AntV Infographic? Share it in [Issue #99](https://github.com/antvis/Infographic/issues/99)!

## 💬 Community & Communication

- Submit your questions or suggestions on GitHub
- Join [GitHub Discussions](https://github.com/antvis/infographic/discussions) to communicate with the community
- Contributions are welcome! Let's improve AntV Infographic together!

If you have any suggestions, feel free to communicate with us on GitHub! Star ⭐ us to show your support.

## 📄 License

This project is open source under the **MIT** license. See [LICENSE](https://github.com/antvis/Infographic/blob/main/LICENSE) for details.