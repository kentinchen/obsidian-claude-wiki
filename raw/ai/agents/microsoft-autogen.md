---
title: "microsoft/autogen: A programming framework for agentic AI"
source: "https://github.com/microsoft/autogen"
author:
published:
created: 2026-04-17
description: "A programming framework for agentic AI. Contribute to microsoft/autogen development by creating an account on GitHub."
tags:
  - "clippings"
---
[![AutoGen Logo](https://camo.githubusercontent.com/2905ec919ee215233fc90a7fa9303c96f4526e9e25d9f0cd1d0cd590f4a6a5e1/68747470733a2f2f6d6963726f736f66742e6769746875622e696f2f6175746f67656e2f302e322f696d672f61672e737667)](https://camo.githubusercontent.com/2905ec919ee215233fc90a7fa9303c96f4526e9e25d9f0cd1d0cd590f4a6a5e1/68747470733a2f2f6d6963726f736f66742e6769746875622e696f2f6175746f67656e2f302e322f696d672f61672e737667)

## AutoGen

**AutoGen** is a framework for creating multi-agent AI applications that can act autonomously or work alongside humans.

> [!caution] Caution
> **⚠️ Maintenance Mode**
> 
> AutoGen is now in maintenance mode. It will not receive new features or enhancements and is community managed going forward.
> 
> New users should start with [Microsoft Agent Framework](https://github.com/microsoft/agent-framework). Existing users are encouraged to migrate using the [AutoGen → Microsoft Agent Framework migration guide](https://learn.microsoft.com/en-us/agent-framework/migration-guide/from-autogen/).
> 
> Microsoft Agent Framework (MAF) is the enterprise‑ready successor to AutoGen. Microsoft Agent FrameworkAF in now available as a production-ready release: stable APIs, and a commitment to long-term support. Whether you're building a single assistant or orchestrating a fleet of specialized agents, Microsoft Agent Framework 1.0 gives you enterprise-grade multi-agent orchestration, multi-provider model support, and cross-runtime interoperability via A2A and MCP.

## Installation

AutoGen requires **Python 3.10 or later**.

```
# Install AgentChat and OpenAI client from Extensions
pip install -U "autogen-agentchat" "autogen-ext[openai]"
```

The current stable version can be found in the [releases](https://github.com/microsoft/autogen/releases). If you are upgrading from AutoGen v0.2, please refer to the [Migration Guide](https://microsoft.github.io/autogen/stable/user-guide/agentchat-user-guide/migration-guide.html) for detailed instructions on how to update your code and configurations.

```
# Install AutoGen Studio for no-code GUI
pip install -U "autogenstudio"
```

## Quickstart

The following samples call OpenAI API, so you first need to create an account and export your key as `export OPENAI_API_KEY="sk-..."`.

### Hello World

Create an assistant agent using OpenAI's GPT-4o model. See [other supported models](https://microsoft.github.io/autogen/stable/user-guide/agentchat-user-guide/tutorial/models.html).

```
import asyncio
from autogen_agentchat.agents import AssistantAgent
from autogen_ext.models.openai import OpenAIChatCompletionClient

async def main() -> None:
    model_client = OpenAIChatCompletionClient(model="gpt-4.1")
    agent = AssistantAgent("assistant", model_client=model_client)
    print(await agent.run(task="Say 'Hello World!'"))
    await model_client.close()

asyncio.run(main())
```

### MCP Server

Create a web browsing assistant agent that uses the Playwright MCP server.

```
# First run \`npm install -g @playwright/mcp@latest\` to install the MCP server.
import asyncio
from autogen_agentchat.agents import AssistantAgent
from autogen_agentchat.ui import Console
from autogen_ext.models.openai import OpenAIChatCompletionClient
from autogen_ext.tools.mcp import McpWorkbench, StdioServerParams

async def main() -> None:
    model_client = OpenAIChatCompletionClient(model="gpt-4.1")
    server_params = StdioServerParams(
        command="npx",
        args=[
            "@playwright/mcp@latest",
            "--headless",
        ],
    )
    async with McpWorkbench(server_params) as mcp:
        agent = AssistantAgent(
            "web_browsing_assistant",
            model_client=model_client,
            workbench=mcp, # For multiple MCP servers, put them in a list.
            model_client_stream=True,
            max_tool_iterations=10,
        )
        await Console(agent.run_stream(task="Find out how many contributors for the microsoft/autogen repository"))

asyncio.run(main())
```

> **Warning**: Only connect to trusted MCP servers as they may execute commands in your local environment or expose sensitive information.

### Multi-Agent Orchestration

You can use `AgentTool` to create a basic multi-agent orchestration setup.

```
import asyncio

from autogen_agentchat.agents import AssistantAgent
from autogen_agentchat.tools import AgentTool
from autogen_agentchat.ui import Console
from autogen_ext.models.openai import OpenAIChatCompletionClient

async def main() -> None:
    model_client = OpenAIChatCompletionClient(model="gpt-4.1")

    math_agent = AssistantAgent(
        "math_expert",
        model_client=model_client,
        system_message="You are a math expert.",
        description="A math expert assistant.",
        model_client_stream=True,
    )
    math_agent_tool = AgentTool(math_agent, return_value_as_last_message=True)

    chemistry_agent = AssistantAgent(
        "chemistry_expert",
        model_client=model_client,
        system_message="You are a chemistry expert.",
        description="A chemistry expert assistant.",
        model_client_stream=True,
    )
    chemistry_agent_tool = AgentTool(chemistry_agent, return_value_as_last_message=True)

    agent = AssistantAgent(
        "assistant",
        system_message="You are a general assistant. Use expert tools when needed.",
        model_client=model_client,
        model_client_stream=True,
        tools=[math_agent_tool, chemistry_agent_tool],
        max_tool_iterations=10,
    )
    await Console(agent.run_stream(task="What is the integral of x^2?"))
    await Console(agent.run_stream(task="What is the molecular weight of water?"))

asyncio.run(main())
```

For more advanced multi-agent orchestrations and workflows, read [AgentChat documentation](https://microsoft.github.io/autogen/stable/user-guide/agentchat-user-guide/index.html).

### AutoGen Studio

Use AutoGen Studio to prototype and run multi-agent workflows without writing code.

> **Caution**: AutoGen Studio is meant to help you rapidly prototype multi-agent workflows and demonstrate an example of end user interfaces built with AutoGen. It is **not meant to be a production-ready app**. Developers are encouraged to use the AutoGen framework to build their own applications, implementing authentication, security and other features required for deployed applications. See the [security note](https://microsoft.github.io/autogen/dev/user-guide/autogenstudio-user-guide/index.html#a-note-on-security) for more details.

```
# Run AutoGen Studio on http://localhost:8080
autogenstudio ui --port 8080 --appdir ./my-app
```

## Why AutoGen?

[![AutoGen Landing](https://github.com/microsoft/autogen/raw/main/autogen-landing.jpg)](https://github.com/microsoft/autogen/blob/main/autogen-landing.jpg)

Pioneered in Microsoft Research, AutoGen opened the door to experimental multi-agent orchestration patterns that inspired the community. While AutoGen is now in maintenance mode, existing users can continue to use the framework with the architecture described below. **For new projects, we recommend [Microsoft Agent Framework](https://github.com/microsoft/agent-framework)**, which builds on the lessons learned from AutoGen with enterprise-grade support.

The autogen *framework* uses a layered and extensible design. Layers have clearly divided responsibilities and build on top of layers below. This design enables you to use the framework at different levels of abstraction, from high-level APIs to low-level components.

- [Core API](https://github.com/microsoft/autogen/blob/main/python/packages/autogen-core) implements message passing, event-driven agents, and local and distributed runtime for flexibility and power. It also support cross-language support for.NET and Python.
- [AgentChat API](https://github.com/microsoft/autogen/blob/main/python/packages/autogen-agentchat) implements a simpler but opinionated API for rapid prototyping. This API is built on top of the Core API and is closest to what users of v0.2 are familiar with and supports common multi-agent patterns such as two-agent chat or group chats.
- [Extensions API](https://github.com/microsoft/autogen/blob/main/python/packages/autogen-ext) enables first- and third-party extensions continuously expanding framework capabilities. It support specific implementation of LLM clients (e.g., OpenAI, AzureOpenAI), and capabilities such as code execution.

The ecosystem also supports two essential *developer tools*:

[![AutoGen Studio Screenshot](https://media.githubusercontent.com/media/microsoft/autogen/refs/heads/main/python/packages/autogen-studio/docs/ags_screen.png)](https://media.githubusercontent.com/media/microsoft/autogen/refs/heads/main/python/packages/autogen-studio/docs/ags_screen.png)

- [AutoGen Studio](https://github.com/microsoft/autogen/blob/main/python/packages/autogen-studio) provides a no-code GUI for building multi-agent applications.
- [AutoGen Bench](https://github.com/microsoft/autogen/blob/main/python/packages/agbench) provides a benchmarking suite for evaluating agent performance.

You can use the AutoGen framework and developer tools to create applications for your domain. For example, [Magentic-One](https://github.com/microsoft/autogen/blob/main/python/packages/magentic-one-cli) is a state-of-the-art multi-agent team built using AgentChat API and Extensions API that can handle a variety of tasks that require web browsing, code execution, and file handling.

For community support, visit our [Discord server](https://aka.ms/autogen-discord) or [GitHub Discussions](https://github.com/microsoft/autogen/discussions). Note that AutoGen is now community-managed and responses may be limited.

## Where to go next?

> **Starting a new project?** Head to [Microsoft Agent Framework](https://github.com/microsoft/agent-framework) for the latest multi-agent capabilities with long-term support.
> 
> **Existing AutoGen user?** Use the [migration guide](https://learn.microsoft.com/en-us/agent-framework/migration-guide/from-autogen/) to transition, or refer to the resources below for current AutoGen documentation.

|  | [![Python](https://camo.githubusercontent.com/0cf4604c8696f10cd1b611f28bef4ea5addf3d65ab72ca0cf169a6ece3615342/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f4175746f47656e2d507974686f6e2d626c75653f6c6f676f3d707974686f6e266c6f676f436f6c6f723d7768697465)](https://github.com/microsoft/autogen/blob/main/python) | [![.NET](https://camo.githubusercontent.com/847b8c17262197b4e1dab12ac90e0c317bd17958b24b188d7b071470621e693b/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f4175746f47656e2d2e4e45542d677265656e3f6c6f676f3d2e6e6574266c6f676f436f6c6f723d7768697465)](https://github.com/microsoft/autogen/blob/main/dotnet) | [![Studio](https://camo.githubusercontent.com/81cfe72f740bc3b4fbcd99692f26c11614856b614f945d16c9250eca0d34eb59/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f4175746f47656e2d53747564696f2d707572706c653f6c6f676f3d76697375616c2d73747564696f266c6f676f436f6c6f723d7768697465)](https://github.com/microsoft/autogen/blob/main/python/packages/autogen-studio) |
| --- | --- | --- | --- |
| Installation | [![Installation](https://camo.githubusercontent.com/6a6c49bdf317f9022084411c44178834007c26799afa24602c80d7433c82e7fa/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f496e7374616c6c2d626c7565)](https://microsoft.github.io/autogen/stable/user-guide/agentchat-user-guide/installation.html) | [![Install](https://camo.githubusercontent.com/9a3d2f6eeceb77fb2c2082b7119487f244098098b3fcdc5aaaf713fe6d13343c/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f496e7374616c6c2d677265656e)](https://microsoft.github.io/autogen/dotnet/dev/core/installation.html) |  |
| Quickstart | [![Quickstart](https://camo.githubusercontent.com/15bae0407fc86e454571028c4510ffff0d13f41339bf3cf38437df60a42a3f15/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f517569636b73746172742d626c7565)](https://microsoft.github.io/autogen/stable/user-guide/agentchat-user-guide/quickstart.html#) |  | [![Usage](https://camo.githubusercontent.com/29cab71ccc02f9543450696cf77f4e49c630babb05e3616056b58f0a65860340/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f517569636b73746172742d707572706c65)](https://microsoft.github.io/autogen/stable/user-guide/autogenstudio-user-guide/usage.html#) |
| Tutorial | [![Tutorial](https://camo.githubusercontent.com/63885daf70511b532283e9507675119b6457b9a83fc7a11fe8e17051c711fb44/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f5475746f7269616c2d626c7565)](https://microsoft.github.io/autogen/stable/user-guide/agentchat-user-guide/tutorial/index.html) |  | [![Usage](https://camo.githubusercontent.com/741f37d1b7cf5f96c8632942ed86aa02aab3f5ad9934de1d32d9070751997d89/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f5475746f7269616c2d707572706c65)](https://microsoft.github.io/autogen/stable/user-guide/autogenstudio-user-guide/usage.html#) |
| API Reference | [![API](https://camo.githubusercontent.com/2a36814f02453ee8ff9908b5926abcc3b0b57ba4ad1b751a33d3132f3f3d22b6/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f446f63732d626c7565)](https://microsoft.github.io/autogen/stable/reference/index.html#) |  |  |
| Packages | [![PyPi autogen-core](https://camo.githubusercontent.com/72e3121fd9e07164e455f54b358a7001649f8f371e363902e1aa2d294843ed1f/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f507950692d6175746f67656e2d2d636f72652d626c75653f6c6f676f3d70797069)](https://pypi.org/project/autogen-core/)   [![PyPi autogen-agentchat](https://camo.githubusercontent.com/ec5beb5966507716ad72aef6b14d48060cede0fe523b303f282b08fb252b6437/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f507950692d6175746f67656e2d2d6167656e74636861742d626c75653f6c6f676f3d70797069)](https://pypi.org/project/autogen-agentchat/)   [![PyPi autogen-ext](https://camo.githubusercontent.com/fc1300c12c15ad394e09fc9425c0571b3c10f66aefe69b3aef2e346c9ff77635/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f507950692d6175746f67656e2d2d6578742d626c75653f6c6f676f3d70797069)](https://pypi.org/project/autogen-ext/) | [![NuGet Contracts](https://camo.githubusercontent.com/fa6c7c78a95fe2fdf7db52b53cc6c1131e6086860b09055505879cab4ae06687/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f4e754765742d436f6e7472616374732d677265656e3f6c6f676f3d6e75676574)](https://www.nuget.org/packages/Microsoft.AutoGen.Contracts/)   [![NuGet Core](https://camo.githubusercontent.com/8074cb36843e07dfea67739962736fae18f1bc6ae98333ec8c60b06deb6dc53b/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f4e754765742d436f72652d677265656e3f6c6f676f3d6e75676574)](https://www.nuget.org/packages/Microsoft.AutoGen.Core/)   [![NuGet Core.Grpc](https://camo.githubusercontent.com/93f7a013d5b67f84a58d83809e7180b4f97fafa9a3156dd15ec14584550a4ad4/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f4e754765742d436f72652e477270632d677265656e3f6c6f676f3d6e75676574)](https://www.nuget.org/packages/Microsoft.AutoGen.Core.Grpc/)   [![NuGet RuntimeGateway.Grpc](https://camo.githubusercontent.com/4d30db663149cf7e298ef2935a6bac45ee9ee625fa99fde3b610d3e3a533e5ea/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f4e754765742d52756e74696d65476174657761792e477270632d677265656e3f6c6f676f3d6e75676574)](https://www.nuget.org/packages/Microsoft.AutoGen.RuntimeGateway.Grpc/) | [![PyPi autogenstudio](https://camo.githubusercontent.com/17d7a788419ab5c484b34dce4d12a77bf873df09a0033fc3d7db4ebfca55c934/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f507950692d6175746f67656e73747564696f2d707572706c653f6c6f676f3d70797069)](https://pypi.org/project/autogenstudio/) |

Interested in contributing? See [CONTRIBUTING.md](https://github.com/microsoft/autogen/blob/main/CONTRIBUTING.md) for guidelines. As AutoGen is in maintenance mode, contributions are limited to bug fixes, security patches, and documentation improvements. For feature development, consider contributing to [Microsoft Agent Framework](https://github.com/microsoft/agent-framework).

Have questions? Check out our [Frequently Asked Questions (FAQ)](https://github.com/microsoft/autogen/blob/main/FAQ.md) for answers to common queries. Community support is available through [GitHub Discussions](https://github.com/microsoft/autogen/discussions) and the [Discord server](https://aka.ms/autogen-discord), though response times may vary as AutoGen is now community-managed. For actively supported tooling, see [Microsoft Agent Framework](https://github.com/microsoft/agent-framework).

## Legal Notices

Microsoft and any contributors grant you a license to the Microsoft documentation and other content in this repository under the [Creative Commons Attribution 4.0 International Public License](https://creativecommons.org/licenses/by/4.0/legalcode), see the [LICENSE](https://github.com/microsoft/autogen/blob/main/LICENSE) file, and grant you a license to any code in the repository under the [MIT License](https://opensource.org/licenses/MIT), see the [LICENSE-CODE](https://github.com/microsoft/autogen/blob/main/LICENSE-CODE) file.

Microsoft, Windows, Microsoft Azure, and/or other Microsoft products and services referenced in the documentation may be either trademarks or registered trademarks of Microsoft in the United States and/or other countries. The licenses for this project do not grant you rights to use any Microsoft names, logos, or trademarks. Microsoft's general trademark guidelines can be found at [http://go.microsoft.com/fwlink/?LinkID=254653](http://go.microsoft.com/fwlink/?LinkID=254653).

Privacy information can be found at [https://go.microsoft.com/fwlink/?LinkId=521839](https://go.microsoft.com/fwlink/?LinkId=521839)

Microsoft and any contributors reserve all other rights, whether under their respective copyrights, patents, or trademarks, whether by implication, estoppel, or otherwise.

[↑ Back to Top ↑](#readme-top)