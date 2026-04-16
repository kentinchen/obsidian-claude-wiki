---
title: "microsoft/retina: eBPF distributed networking observability tool for Kubernetes"
source: "https://github.com/microsoft/retina"
author:
published:
created: 2026-04-17
description: "eBPF distributed networking observability tool for Kubernetes - microsoft/retina"
tags:
  - "clippings"
---
## Overview

Retina is a cloud-agnostic, open-source **Kubernetes network observability platform** that provides a **centralized hub for monitoring application health, network health, and security**. It provides actionable insights to cluster network administrators, cluster security administrators, and DevOps engineers navigating DevOps, SecOps, and compliance use cases.

Retina **collects customizable telemetry**, which can be exported to **multiple storage options** (such as Prometheus, Azure Monitor, and other vendors) and **visualized in a variety of ways** (like Grafana, Azure Log Analytics, and other vendors).

## Features

- **[eBPF](https://ebpf.io/what-is-ebpf#what-is-ebpf) -based** Network Observability platform for Kubernetes workloads.
- **On-Demand** and **Configurable**.
- Actionable, industry-standard **Prometheus metrics**.
- Streamlined **Packet Captures** for deep dives.
- **Cloud-agnostic**, supporting multiple OS (like Linux, Windows, Azure Linux).

## Why Retina?

Retina lets you **investigate network issues on-demand** and **continuously monitor your clusters**. For scenarios where Retina shines, see the intro docs [here](https://retina.sh/docs/Introduction/intro)

## Documentation

See [retina.sh](http://retina.sh/) for documentation and examples.

## Known Limitations

⚠️ **Performance on High-Core-Count Systems**: Community users have reported performance considerations when using Advanced metrics (with `packetparser` plugin) on nodes with 32+ CPU cores under high network load. Consider starting with Basic metrics mode on large node types. See [Known Limitations](https://retina.sh/docs/Introduction/intro#known-limitations) for details.

⚠️ **Windows Server 2019**: Retina no longer supports Windows Server 2019 nodes. Use Windows Server 2022 for Windows workloads.

## Capabilities

Retina has two major features:

- [Metrics](https://retina.sh/docs/Metrics/metrics-intro)
- [Captures](https://retina.sh/docs/Captures/overview)

### Metrics Quick Install Guide

Retina can be installed using the Helm chart from GHCR:

```
# Set the version to a specific version here or get latest version from GitHub API.
VERSION=$( curl -sL https://api.github.com/repos/microsoft/retina/releases/latest | jq -r .name)
helm upgrade --install retina oci://ghcr.io/microsoft/retina/charts/retina \
    --version $VERSION \
    --set image.tag=$VERSION \
    --set operator.tag=$VERSION \
    --set logLevel=info \
    --set enabledPlugin_linux="\[dropreason\,packetforward\,linuxutil\,dns\]"
```

Set the `version` and image `tag` arguments to the desired version, if different.

After Helm install, follow the steps for setting up [Prometheus](https://retina.sh/docs/Installation/prometheus) and [Grafana](https://retina.sh/docs/Installation/grafana) to configure metrics collection and visualization.

### Captures Quick Start Guide

#### Captures via CLI

The preferred way to install the Retina CLI using [Krew](https://krew.sigs.k8s.io/).

```
kubectl krew install retina
```

Other installation options are documented in [CLI Installation](https://retina.sh/docs/Installation/CLI).

Verify installation:

```
$ kubectl retina
Retina is an eBPF distributed networking observability tool for Kubernetes.

Usage:
  kubectl-retina [command]

Available Commands:
  capture     Capture network traffic
  completion  Generate the autocompletion script for the specified shell
  config      Configure retina CLI
  help        Help about any command
  shell       [EXPERIMENTAL] Interactively debug a node or pod
  trace       Retrieve status or results from Retina
  version     Show version

Flags:
  -h, --help   help for kubectl-retina

Use "kubectl-retina [command] --help" for more information about a command.
```

To quickly start creating a capture:

```
kubectl retina capture create --pod-selectors <app=my-app>
```

For further CLI documentation, see [Capture with Retina CLI](https://retina.sh/docs/Captures/cli).

#### Captures via CRD

Install Retina using Helm:

```
VERSION=$( curl -sL https://api.github.com/repos/microsoft/retina/releases/latest | jq -r .name)
helm upgrade --install retina oci://ghcr.io/microsoft/retina/charts/retina \
    --version $VERSION \
    --set image.tag=$VERSION \
    --set operator.tag=$VERSION \
    --set image.pullPolicy=Always \
    --set logLevel=info \
    --set os.windows=true \
    --set operator.enabled=true \
    --set operator.enableRetinaEndpoint=true \
    --skip-crds \
    --set enabledPlugin_linux="\[dropreason\,packetforward\,linuxutil\,dns\,packetparser\]"
```

Then follow steps in [Capture CRD](https://retina.sh/docs/Captures/overview/#option-2-capture-crd-custom-resource-definition) for documentation of the CRD and examples for setting up Captures.

## Contributing

This project welcomes contributions and suggestions. Most contributions require you to agree to a Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us the rights to use your contribution. For details, visit [https://cla.opensource.microsoft.com](https://cla.opensource.microsoft.com/).

When you submit a pull request, a CLA bot will automatically determine whether you need to provide a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

[Read more about how to begin contributing here.](https://retina.sh/docs/Contributing/overview)

### Verify signed images

Retina images published to GHCR are cryptographically signed. You can verify their provenance with [`sigstore/cosign`](https://github.com/sigstore/cosign):

```
REPO=microsoft/retina # or your repo
IMAGE=retina-operator # or other image to verify
# This can be replaced with another tag to verify, or with the image SHA256
LATEST_TAG=$(curl -s https://api.github.com/repos/microsoft/retina/releases | jq -r '.[0].name')
cosign verify ghcr.io/$REPO/$IMAGE:$LATEST_TAG --certificate-oidc-issuer https://token.actions.githubusercontent.com --certificate-identity-regexp="https://github.com/$REPO" -o text
```

### Office Hours and Community Meetings

We host a periodic open community meeting. [Find the details here.](https://retina.sh/docs/Contributing/overview#office-hours-and-community-meetings)

## Trademarks

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft trademarks or logos is subject to and must follow [Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general). Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship. Any use of third-party trademarks or logos are subject to those third-party's policies.

## License

See the [LICENSE](https://github.com/microsoft/retina/blob/main/LICENSE).

## Code of Conduct

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.