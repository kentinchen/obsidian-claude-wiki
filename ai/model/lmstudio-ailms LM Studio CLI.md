---
title: "lmstudio-ai/lms: LM Studio CLI"
source: "https://github.com/lmstudio-ai/lms"
author:
published:
created: 2026-04-16
description: "LM Studio CLI. Contribute to lmstudio-ai/lms development by creating an account on GitHub."
tags:
  - "clippings"
---
![lmstudio cli logo](https://camo.githubusercontent.com/0bcb760c2ea442218d8c7734cddd9abef065347dfd9cde67a4167d3f96005adc/68747470733a2f2f66696c65732e6c6d73747564696f2e61692f6c6d732d6c696768742e706e67)  
  

`lms` - Command Line Tool for [LM Studio](https://lmstudio.ai/)

Built with `lmstudio.js`

## Installation

`lms` ships with [LM Studio](https://lmstudio.ai/) 0.2.22 and newer.

If you have trouble running the command, try running `npx lmstudio install-cli` to add it to path.

To check if the bootstrapping was successful, run the following in a **👉 new terminal window 👈**:

```
lms
```

## Usage

You can use `lms --help` to see a list of all available subcommands.

For details about each subcommand, run `lms <subcommand> --help`.

Here are some frequently used commands:

- `lms status` - To check the status of LM Studio.
- `lms server start` - To start the local API server.
- `lms server stop` - To stop the local API server.
- `lms ls` - To list all downloaded models.
	- `lms ls --json` - To list all downloaded models in machine-readable JSON format.
- `lms ps` - To list all loaded models available for inferencing.
	- `lms ps --json` - To list all loaded models available for inferencing in machine-readable JSON format.
- `lms load` - To load a model
	- `lms load <model path> -y` - To load a model with maximum GPU acceleration without confirmation
- `lms unload <model identifier>` - To unload a model
	- `lms unload --all` - To unload all models
- `lms create` - To create a new project with LM Studio SDK
- `lms log stream` - To stream logs from LM Studio

## Contributing

The CLI is part of the [lmstudio.js monorepo](https://github.com/lmstudio-ai/lmstudio.js) and cannot be built standalone.

## Building and Testing the CLI

```
# Clone and build the entire monorepo
git clone https://github.com/lmstudio-ai/lmstudio-js.git --recursive
cd lmstudio-js
npm install
npm run build

# Test your CLI changes
node publish/cli/dist/index.js <subcommand>
```

**Example:**

```
node publish/cli/dist/index.js --help
node publish/cli/dist/index.js status
```

See [CONTRIBUTING.md](https://github.com/lmstudio-ai/lms/blob/main/CONTRIBUTING.md) for more information.