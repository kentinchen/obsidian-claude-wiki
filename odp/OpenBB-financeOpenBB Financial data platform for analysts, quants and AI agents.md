---
title: "OpenBB-finance/OpenBB: Financial data platform for analysts, quants and AI agents."
source: "https://github.com/OpenBB-finance/OpenBB"
author:
published:
created: 2026-04-16
description: "Financial data platform for analysts, quants and AI agents. - OpenBB-finance/OpenBB"
tags:
  - "clippings"
---
[![Open Data Platform by OpenBB logo](https://github.com/OpenBB-finance/OpenBB/raw/develop/images/odp-light.svg?raw=true#gh-light-mode-only)](https://github.com/OpenBB-finance/OpenBB/blob/develop/images/odp-light.svg?raw=true#gh-light-mode-only)

  
  

Open Data Platform by OpenBB (ODP) is the open-source toolset that helps data engineers integrate proprietary, licensed, and public data sources into downstream applications like AI copilots and research dashboards.

ODP operates as the "connect once, consume everywhere" infrastructure layer that consolidates and exposes data to multiple surfaces at once: Python environments for quants, OpenBB Workspace and Excel for analysts, MCP servers for AI agents, and REST APIs for other applications.

[![Logo](https://camo.githubusercontent.com/a3fd1d9d5a13e0dcb0d83b89dcbfbfab38371622bd86c0e9629e6145ada8cb13/68747470733a2f2f6f70656e62622d636d732e64697265637475732e6170702f6173736574732f37306239373165662d376137652d343836652d623561652d3163633630326632313632632e706e67)](https://pro.openbb.co/)

Get started with: `pip install openbb`

```
from openbb import obb
output = obb.equity.price.historical("AAPL")
df = output.to_dataframe()
```

Data integrations available can be found here: [https://docs.openbb.co/python/reference](https://docs.openbb.co/python/reference)

---

## OpenBB Workspace

While the Open Data Platform provides the open-source data integration foundation, **OpenBB Workspace** offers the enterprise UI for analysts to visualize datasets and leverage AI agents. The platform's "connect once, consume everywhere" architecture enables seamless integration between the two.

You can find OpenBB Workspace at [https://pro.openbb.co](https://pro.openbb.co/).Data integration:

- You can learn more about adding data to the OpenBB workspace from the [docs](https://docs.openbb.co/workspace) or [this open source repository](https://github.com/OpenBB-finance/backends-for-openbb).

AI Agents integration:

- You can learn more about adding AI agents to the OpenBB workspace from [this open source repository](https://github.com/OpenBB-finance/agents-for-openbb).

### Integrating Open Data Platform to the OpenBB Workspace

Connect this library to the OpenBB Workspace with a few simple commands, in a Python (3.9.21 - 3.12) environment.

#### Run an ODP backend

- Install the packages.
```
pip install "openbb[all]"
```
- Start the API server over localhost.
```
openbb-api
```

This will launch a FastAPI server, via Uvicorn, at `127.0.0.1:6900`.

You can check that it works by going to [http://127.0.0.1:6900](http://127.0.0.1:6900/).

#### Integrate the ODP Backend to OpenBB Workspace

Sign-in to the [OpenBB Workspace](https://pro.openbb.co/), and follow the following steps:

[![CleanShot 2025-05-17 at 09 51 56@2x](https://private-user-images.githubusercontent.com/25267873/444785019-75cffb4a-5e95-470a-b9d0-6ffd4067e069.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNTQ5MTEsIm5iZiI6MTc3NjM1NDYxMSwicGF0aCI6Ii8yNTI2Nzg3My80NDQ3ODUwMTktNzVjZmZiNGEtNWU5NS00NzBhLWI5ZDAtNmZmZDQwNjdlMDY5LnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDE1NTAxMVomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTYwNGI5ODY5YmY5YmRhMjc1MzYxOTViZDhlYTBjNWRkOWE5YjZlMzU2YjYzYTQwNDJiNWU4NzlkMTZlYzU1NmUmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.QCT6L_4mwif-BxktZ1l_MoMTLtO_sTpj5P27n0n6jpg)](https://private-user-images.githubusercontent.com/25267873/444785019-75cffb4a-5e95-470a-b9d0-6ffd4067e069.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNTQ5MTEsIm5iZiI6MTc3NjM1NDYxMSwicGF0aCI6Ii8yNTI2Nzg3My80NDQ3ODUwMTktNzVjZmZiNGEtNWU5NS00NzBhLWI5ZDAtNmZmZDQwNjdlMDY5LnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDE1NTAxMVomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTYwNGI5ODY5YmY5YmRhMjc1MzYxOTViZDhlYTBjNWRkOWE5YjZlMzU2YjYzYTQwNDJiNWU4NzlkMTZlYzU1NmUmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.QCT6L_4mwif-BxktZ1l_MoMTLtO_sTpj5P27n0n6jpg)

1. Go to the "Apps" tab
2. Click on "Connect backend"
3. Fill in the form with: Name: Open Data Platform URL: [http://127.0.0.1:6900](http://127.0.0.1:6900/)
4. Click on "Test". You should get a "Test successful" with the number of apps found.
5. Click on "Add".

That's it.

---

## Table of Contents

1. [Installation](#1-installation)
2. [Contributing](#2-contributing)
3. [License](#3-license)
4. [Disclaimer](#4-disclaimer)
5. [Contacts](#5-contacts)
6. [Star History](#6-star-history)
7. [Contributors](#7-contributors)

## 1\. Installation

The ODP Python Package can be installed from [PyPI package](https://pypi.org/project/openbb/) by running `pip install openbb`

or by cloning the repository directly with `git clone https://github.com/OpenBB-finance/OpenBB.git`.

Please find more about the installation process, in the [OpenBB Documentation](https://docs.openbb.co/python/installation).

### ODP CLI installation

The ODP CLI is a command-line interface that allows you to access the ODP directly from your command line.

It can be installed by running `pip install openbb-cli`

or by cloning the repository directly with `git clone https://github.com/OpenBB-finance/OpenBB.git`.

Please find more about the installation process in the [OpenBB Documentation](https://docs.openbb.co/cli/installation).

## 2\. Contributing

There are three main ways of contributing to this project. (Hopefully you have starred the project by now ⭐️)

### Become a Contributor

- More information on our [Developer Documentation](https://docs.openbb.co/python/developer).

### Create a GitHub ticket

Before creating a ticket make sure the one you are creating doesn't exist already [among the existing issues](https://github.com/OpenBB-finance/OpenBB/issues)

- [Report bug](https://github.com/OpenBB-finance/OpenBB/issues/new?assignees=&labels=bug&template=bug_report.md&title=%5BBug%5D)
- [Suggest improvement](https://github.com/OpenBB-finance/OpenBB/issues/new?assignees=&labels=enhancement&template=enhancement.md&title=%5BIMPROVE%5D)
- [Request a feature](https://github.com/OpenBB-finance/OpenBB/issues/new?assignees=&labels=new+feature&template=feature_request.md&title=%5BFR%5D)

### Provide feedback

We are most active on [our Discord](https://openbb.co/discord), but feel free to reach out to us in any of [our social media](https://openbb.co/links) for feedback.

## 3\. License

Distributed under the AGPLv3 License. See [LICENSE](https://github.com/OpenBB-finance/OpenBB/blob/main/LICENSE) for more information.

## 4\. Disclaimer

Trading in financial instruments involves high risks including the risk of losing some, or all, of your investment amount, and may not be suitable for all investors.

Before deciding to trade in a financial instrument you should be fully informed of the risks and costs associated with trading the financial markets, carefully consider your investment objectives, level of experience, and risk appetite, and seek professional advice where needed.

The data contained in the Open Data Platform is not necessarily accurate.

OpenBB and any provider of the data contained in this website will not accept liability for any loss or damage as a result of your trading, or your reliance on the information displayed.

All names, logos, and brands of third parties that may be referenced in our sites, products or documentation are trademarks of their respective owners. Unless otherwise specified, OpenBB and its products and services are not endorsed by, sponsored by, or affiliated with these third parties.

Our use of these names, logos, and brands is for identification purposes only, and does not imply any such endorsement, sponsorship, or affiliation.

## 5\. Contacts

If you have any questions about the platform or anything OpenBB, feel free to email us at `support@openbb.co`

If you want to say hi, or are interested in partnering with us, feel free to reach us at `hello@openbb.co`

Any of our social media platforms: [openbb.co/links](https://openbb.co/links)

## 6\. Star History

This is a proxy of our growth and that we are just getting started.

But for more metrics important to us check [openbb.co/open](https://openbb.co/open).

[![Star History Chart](https://camo.githubusercontent.com/17bcc77a81b74e439926d82e406fa1602742219e72ff0e3c34f89f339345d359/68747470733a2f2f6170692e737461722d686973746f72792e636f6d2f7376673f7265706f733d6f70656e62622d66696e616e63652f4f70656e424226747970653d44617465267468656d653d6461726b)](https://api.star-history.com/svg?repos=openbb-finance/OpenBB&type=Date&theme=dark)

## 7\. Contributors

OpenBB wouldn't be OpenBB without you. If we are going to disrupt financial industry, every contribution counts. Thank you for being part of this journey.

[![](https://camo.githubusercontent.com/5a28c87a8563a6db7157ecd2524d570dda419452ba66711de174914125bf8eb4/68747470733a2f2f636f6e7472696275746f72732d696d672e7765622e6170702f696d6167653f7265706f3d4f70656e42422d66696e616e63652f4f70656e4242)](https://github.com/OpenBB-finance/OpenBB/graphs/contributors)