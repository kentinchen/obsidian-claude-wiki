---
title: "Overview"
source: "https://www.jetify.com/docs/devbox/installing-devbox#installing-wsl2"
author:
published:
created: 2026-06-28
description:
tags:
  - "clippings"
---
### Prerequisites

- Nix Package Manager

If Nix is not detected when running a command, Devbox will automatically install it for you. Don’t worry: You can use Devbox without needing to learn the Nix Language. If you would like to install Nix yourself, we recommend the [Determinate Nix Installer](https://determinate.systems/nix-installer/).

### Installation Script

Run the following install script to install the latest version of Devbox:

```shellscript
curl -fsSL https://get.jetify.com/devbox | bash
```

### OS-Specific Notes

Run the install script as a **non-root user**.

Devbox will install Nix in single-user mode for Linux if not already present.

Devbox will install Nix in multi-user mode for macOS if not already present.

You can use Devbox on Windows using [**Windows Subsystem for Linux 2**](https://learn.microsoft.com/en-us/windows/wsl/install).

Installing WSL2

To install WSL2 with the default Ubuntu distribution, open Powershell or Windows Command Prompt as an administrator, and run:

```shellscript
wsl --install
```

If WSL2 is already installed, you can install Ubuntu by running

```shellscript
wsl --install -d Ubuntu
```

If you are running an older version of Windows, you may need to follow the [manual installation steps](https://learn.microsoft.com/en-us/windows/wsl/install-manual) to enable virtualization and WSL2 on your system. See the [official docs](https://learn.microsoft.com/en-us/windows/wsl/install) for more details.

Run the install script in your WSL2 terminal as a **non-root user**.

Devbox will install Nix in single-user mode for WSL2 if not already present.

Devbox is available through the [**Nix Package Manager**](https://search.nixos.org/packages?channel=unstable&show=devbox&from=0&size=50&sort=relevance&type=packages&query=devbox).

To install on NixOS:

```shellscript
nix-env -iA nixos.devbox
```

To install on a non NixOS:

```shellscript
nix-env -iA nixpkgs.devbox
```

or

```shellscript
nix profile install nixpkgs#devbox
```

New releases of Devbox need to be updated in Nixpkgs before they are available for installation. If you want to use the latest version of Devbox, you can install it using the [Nix Flake](https://www.jetify.com/docs/devbox/installing-devbox?install-method=flake).

You can also install Devbox on a NixOS/Nixpkgs system using our Nix Flake. Using the Nix Flake can help you access pre-releases and final releases of Devbox as soon as they are published.

To get the latest version:

```shellscript
nix profile install github:jetify-com/devbox/latest
```

To install a specific version, you can run the following command (only supports versions 0.13.2 and above):

```shellscript
nix profile install github:jetify-com/devbox/0.13.2
```

---

Devbox will notify you when a new version is available. To update to the latest released version of Devbox, you can run `devbox version update`.

If you installed Devbox with Nix, you can update Devbox via Nix using `nix-env -u devbox`, or `nix profile upgrade`.

You can find release notes and details on the [Releases page](https://github.com/jetify-com/devbox/releases) of the Devbox Github repo.

You can rollback or pin the version of Devbox on your system using the `DEVBOX_USE_VERSION` environment variable. For example, to use version 0.8.0:

```text
export DEVBOX_USE_VERSION=0.8.0
```

Setting this variable will use the specified version of Devbox even if a newer version has been installed on your machine.

If you installed Devbox with Nixpkgs, you will need to pin Devbox in your profile or Nix configuration. You can find the Nixpkg commits for previous versions of Devbox on [Nixhub](https://www.nixhub.io/packages/devbox).

- **[Getting Started](https://www.jetify.com/docs/devbox/quickstart):** Learn how to create a dev environment with Devbox
- **[Devbox Global](https://www.jetify.com/docs/devbox/devbox-global):** Learn how to use the devbox as a global package manager

[Edit this page](https://github.com/jetify-com/docs/tree/main/docs/devbox/installing-devbox.mdx)