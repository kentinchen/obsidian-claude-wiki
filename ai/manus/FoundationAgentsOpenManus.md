---
title: "FoundationAgents/OpenManus: No fortress, purely open ground.  OpenManus is Coming."
source: "https://github.com/FoundationAgents/OpenManus"
author:
published:
created: 2026-04-16
description: "No fortress, purely open ground.  OpenManus is Coming. - FoundationAgents/OpenManus"
tags:
  - "clippings"
---
[![](https://github.com/FoundationAgents/OpenManus/raw/main/assets/logo.jpg)](https://github.com/FoundationAgents/OpenManus/blob/main/assets/logo.jpg)

English | [中文](https://github.com/FoundationAgents/OpenManus/blob/main/README_zh.md) | [한국어](https://github.com/FoundationAgents/OpenManus/blob/main/README_ko.md) | [日本語](https://github.com/FoundationAgents/OpenManus/blob/main/README_ja.md)

## 👋 OpenManus

Manus is incredible, but OpenManus can achieve any idea without an *Invite Code* 🛫!

Our team members [@Xinbin Liang](https://github.com/mannaandpoem) and [@Jinyu Xiang](https://github.com/XiangJinyu) (core authors), along with [@Zhaoyang Yu](https://github.com/MoshiQAQ), [@Jiayi Zhang](https://github.com/didiforgithub), and [@Sirui Hong](https://github.com/stellaHSR), we are from [@MetaGPT](https://github.com/geekan/MetaGPT). The prototype is launched within 3 hours and we are keeping building!

It's a simple implementation, so we welcome any suggestions, contributions, and feedback!

Enjoy your own agent with OpenManus!

We're also excited to introduce [OpenManus-RL](https://github.com/OpenManus/OpenManus-RL), an open-source project dedicated to reinforcement learning (RL)- based (such as GRPO) tuning methods for LLM agents, developed collaboratively by researchers from UIUC and OpenManus.

## Project Demo

seo\_website.mp4<video src="https://github.com/user-attachments/assets/6dcfd0d2-9142-45d9-b74e-d10aa75073c6" controls="controls"></video>

## Installation

We provide two installation methods. Method 2 (using uv) is recommended for faster installation and better dependency management.

### Method 1: Using conda

1. Create a new conda environment:
```
conda create -n open_manus python=3.12
conda activate open_manus
```
1. Clone the repository:
```
git clone https://github.com/FoundationAgents/OpenManus.git
cd OpenManus
```
1. Install dependencies:
```
pip install -r requirements.txt
```
1. Install uv (A fast Python package installer and resolver):
```
curl -LsSf https://astral.sh/uv/install.sh | sh
```
1. Clone the repository:
```
git clone https://github.com/FoundationAgents/OpenManus.git
cd OpenManus
```
1. Create a new virtual environment and activate it:
```
uv venv --python 3.12
source .venv/bin/activate  # On Unix/macOS
# Or on Windows:
# .venv\Scripts\activate
```
1. Install dependencies:
```
uv pip install -r requirements.txt
```

### Browser Automation Tool (Optional)

```
playwright install
```

## Configuration

OpenManus requires configuration for the LLM APIs it uses. Follow these steps to set up your configuration:

1. Create a `config.toml` file in the `config` directory (you can copy from the example):
```
cp config/config.example.toml config/config.toml
```
1. Edit `config/config.toml` to add your API keys and customize settings:
```
# Global LLM configuration
[llm]
model = "gpt-4o"
base_url = "https://api.openai.com/v1"
api_key = "sk-..."  # Replace with your actual API key
max_tokens = 4096
temperature = 0.0

# Optional configuration for specific LLM models
[llm.vision]
model = "gpt-4o"
base_url = "https://api.openai.com/v1"
api_key = "sk-..."  # Replace with your actual API key
```

## Quick Start

One line for run OpenManus:

```
python main.py
```

Then input your idea via terminal!

For MCP tool version, you can run:

```
python run_mcp.py
```

For unstable multi-agent version, you also can run:

```
python run_flow.py
```

### Custom Adding Multiple Agents

Currently, besides the general OpenManus Agent, we have also integrated the DataAnalysis Agent, which is suitable for data analysis and data visualization tasks. You can add this agent to `run_flow` in `config.toml`.

```
# Optional configuration for run-flow
[runflow]
use_data_analysis_agent = true     # Disabled by default, change to true to activate
```

In addition, you need to install the relevant dependencies to ensure the agent runs properly: [Detailed Installation Guide](https://github.com/FoundationAgents/OpenManus/blob/main/app/tool/chart_visualization/README.md##Installation)

## How to contribute

We welcome any friendly suggestions and helpful contributions! Just create issues or submit pull requests.

Or contact @mannaandpoem via 📧email: [mannaandpoem@gmail.com](mailto:mannaandpoem@gmail.com)

**Note**: Before submitting a pull request, please use the pre-commit tool to check your changes. Run `pre-commit run --all-files` to execute the checks.

## Community Group

Join our networking group on Feishu and share your experience with other developers!

## Star History

[![Star History Chart](https://camo.githubusercontent.com/3d83e7184c2026a157c3266b74edf9b0a31d61dd87cbff39e3b85d9e0bfbb81b/68747470733a2f2f6170692e737461722d686973746f72792e636f6d2f7376673f7265706f733d466f756e646174696f6e4167656e74732f4f70656e4d616e757326747970653d44617465)](https://star-history.com/#FoundationAgents/OpenManus&Date)

## Sponsors

Thanks to [PPIO](https://ppinfra.com/user/register?invited_by=OCPKCN&utm_source=github_openmanus&utm_medium=github_readme&utm_campaign=link) for computing source support.

> PPIO: The most affordable and easily-integrated MaaS and GPU cloud solution.

## Acknowledgement

Thanks to [anthropic-computer-use](https://github.com/anthropics/anthropic-quickstarts/tree/main/computer-use-demo), [browser-use](https://github.com/browser-use/browser-use) and [crawl4ai](https://github.com/unclecode/crawl4ai) for providing basic support for this project!

Additionally, we are grateful to [AAAJ](https://github.com/metauto-ai/agent-as-a-judge), [MetaGPT](https://github.com/geekan/MetaGPT), [OpenHands](https://github.com/All-Hands-AI/OpenHands) and [SWE-agent](https://github.com/SWE-agent/SWE-agent).

We also thank stepfun(阶跃星辰) for supporting our Hugging Face demo space.

OpenManus is built by contributors from MetaGPT. Huge thanks to this agent community!

## Cite

```
@misc{openmanus2025,
   = {Xinbin Liang and Jinyu Xiang and Zhaoyang Yu and Jiayi Zhang and Sirui Hong and Sheng Fan and Xiao Tang and Bang Liu and Yuyu Luo and Chenglin Wu},
  title = {OpenManus: An open-source framework for building general AI agents},
  year = {2025},
  publisher = {Zenodo},
  doi = {10.5281/zenodo.15186407},
  url = {https://doi.org/10.5281/zenodo.15186407},
}
```