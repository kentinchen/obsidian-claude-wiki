---
title: "psmux/psmux: Tmux on Windows Powershell - tmux for PowerShell, Windows Terminal, cmd.exe. Includes psmux, pmux, and tmux commands. This is native Powershell Tmux designed for Windows in Rust 🦀"
source: "https://github.com/psmux/psmux"
author:
published:
created: 2026-05-04
description: "Tmux on Windows Powershell - tmux for PowerShell, Windows Terminal, cmd.exe. Includes psmux, pmux, and tmux commands. This is native Powershell Tmux designed for Windows in Rust 🦀 - psmux/psmux"
tags:
  - "clippings"
---
```
╔═══════════════════════════════════════════════════════════╗
║   ██████╗ ███████╗███╗   ███╗██╗   ██╗██╗  ██╗            ║
║   ██╔══██╗██╔════╝████╗ ████║██║   ██║╚██╗██╔╝            ║
║   ██████╔╝███████╗██╔████╔██║██║   ██║ ╚███╔╝             ║
║   ██╔═══╝ ╚════██║██║╚██╔╝██║██║   ██║ ██╔██╗             ║
║   ██║     ███████║██║ ╚═╝ ██║╚██████╔╝██╔╝ ██╗            ║
║   ╚═╝     ╚══════╝╚═╝     ╚═╝ ╚═════╝ ╚═╝  ╚═╝            ║
║     Born in PowerShell. Made in Rust. 🦀                 ║
║          Terminal Multiplexer for Windows                 ║
╚═══════════════════════════════════════════════════════════╝
```

**The native Windows tmux. Born in PowerShell, made in Rust.**  
Full mouse support · tmux themes · tmux config · 83 commands · blazing fast

[Install](#installation) · [Usage](#usage) · [Claude Code](https://github.com/psmux/psmux/blob/master/docs/claude-code.md) · [Features](https://github.com/psmux/psmux/blob/master/docs/features.md) · [Compatibility](https://github.com/psmux/psmux/blob/master/docs/compatibility.md) · [Performance](https://github.com/psmux/psmux/blob/master/docs/performance.md) · [Plugins](https://github.com/psmux/psmux/blob/master/docs/plugins.md) · [Keys](https://github.com/psmux/psmux/blob/master/docs/keybindings.md) · [Scripting](https://github.com/psmux/psmux/blob/master/docs/scripting.md) · [Config](https://github.com/psmux/psmux/blob/master/docs/configuration.md) · [Mouse/SSH](https://github.com/psmux/psmux/blob/master/docs/mouse-ssh.md) · [FAQ](https://github.com/psmux/psmux/blob/master/docs/faq.md) · [Related Projects](#related-projects)

---

## psmux

**The real tmux for Windows.** Not a port, not a wrapper, not a workaround.

psmux is a **native Windows terminal multiplexer** built from the ground up in Rust. It uses Windows ConPTY directly, speaks the tmux command language, reads your `.tmux.conf`, and supports tmux themes. All without WSL, Cygwin, or MSYS2.

> 💡 **Tip:** psmux ships with `tmux` and `pmux` aliases. Just type `tmux` and it works!

👀 On Windows 👇

[![psmux in action](https://github.com/psmux/psmux/raw/master/demo.gif)](https://github.com/psmux/psmux/blob/master/demo.gif)

## Installation

### Using WinGet

```
winget install psmux
```

### Using Cargo

```
cargo install psmux
```

This installs `psmux`, `pmux`, and `tmux` binaries to your Cargo bin directory.

### Using Scoop

```
scoop bucket add psmux https://github.com/psmux/scoop-psmux
scoop install psmux
```

### Using Chocolatey

```
choco install psmux
```

### From GitHub Releases

Download the latest `.zip` from [GitHub Releases](https://github.com/psmux/psmux/releases) and add to your PATH.

### From Source

```
git clone https://github.com/psmux/psmux.git
cd psmux
cargo build --release
```

Built binaries:

```
target\release\psmux.exe
target\release\pmux.exe
target\release\tmux.exe
```

### Docker (build environment)

A ready-made Windows container with Rust + MSVC + SSH for building psmux:

```
cd docker
docker build -t psmux-dev .
docker run -d --name psmux-dev -p 127.0.0.1:2222:22 -e ADMIN_PASSWORD=YourPass123! psmux-dev
ssh ContainerAdministrator@localhost -p 2222
```

See [docker/README.md](https://github.com/psmux/psmux/blob/master/docker/README.md) for full details.

### Requirements

- Windows 10 or Windows 11
- **PowerShell 7+** (recommended) or cmd.exe
	- Download PowerShell: `winget install --id Microsoft.PowerShell`
		- Or visit: [https://aka.ms/powershell](https://aka.ms/powershell)

## Why psmux?

If you've used tmux on Linux/macOS and wished you had something like it on Windows, **this is it**. Split panes, multiple windows, session persistence, full mouse support, tmux themes, 83 commands, 140+ format variables, 53 vim copy-mode keys. Your existing `.tmux.conf` works. Full details: **[docs/features.md](https://github.com/psmux/psmux/blob/master/docs/features.md)** · **[docs/compatibility.md](https://github.com/psmux/psmux/blob/master/docs/compatibility.md)**

## Usage

Use `psmux`, `pmux`, or `tmux` — they're identical:

```
psmux                        # Start a new session
psmux new-session -s work    # Named session
psmux ls                     # List sessions
psmux attach -t work         # Attach to a session
psmux --help                 # Show help
```

## Claude Code Agent Teams

psmux has first-class support for Claude Code agent teams. When Claude Code runs inside a psmux session, teammate agents automatically spawn in separate tmux panes instead of running in-process.

```
psmux new-session -s work    # Start a psmux session
claude                       # Run Claude Code — agent teams just work
```

No extra configuration needed. Full guide: **[docs/claude-code.md](https://github.com/psmux/psmux/blob/master/docs/claude-code.md)**

## Documentation

| Topic | Description |
| --- | --- |
| **[Features](https://github.com/psmux/psmux/blob/master/docs/features.md)** | Full feature list — mouse, copy mode, layouts, format engine |
| **[Compatibility](https://github.com/psmux/psmux/blob/master/docs/compatibility.md)** | tmux command/config compatibility matrix |
| **[Performance](https://github.com/psmux/psmux/blob/master/docs/performance.md)** | Benchmarks and optimization details |
| **[Key Bindings](https://github.com/psmux/psmux/blob/master/docs/keybindings.md)** | Default keys and customization |
| **[Scripting](https://github.com/psmux/psmux/blob/master/docs/scripting.md)** | 83 commands, hooks, targets, pipe-pane |
| **[Configuration](https://github.com/psmux/psmux/blob/master/docs/configuration.md)** | Config files, options, environment variables |
| **[Plugins & Themes](https://github.com/psmux/psmux/blob/master/docs/plugins.md)** | Plugin ecosystem — Catppuccin, Dracula, Nord, and more |
| **[Mouse Over SSH](https://github.com/psmux/psmux/blob/master/docs/mouse-ssh.md)** | SSH mouse support and Windows version requirements |
| **[Claude Code](https://github.com/psmux/psmux/blob/master/docs/claude-code.md)** | Agent teams integration guide |
| **[FAQ](https://github.com/psmux/psmux/blob/master/docs/faq.md)** | Common questions and answers |

## Related Projects

| [![pstop demo](https://raw.githubusercontent.com/psmux/pstop/master/pstop-demo.gif)   **pstop**](https://github.com/psmux/pstop)   <sub>htop for Windows — real-time system monitor with per-core CPU bars, tree view, 7 color schemes</sub>   `cargo install pstop` | [![psnet screenshot](https://raw.githubusercontent.com/psmux/psnet/master/image.png)   **psnet**](https://github.com/psmux/psnet)   <sub>Real-time TUI network monitor — live speed graphs, connections, traffic log, packet sniffer</sub>   `cargo install psnet` |
| --- | --- |
| [![Tmux Plugin Panel screenshot](https://raw.githubusercontent.com/psmux/Tmux-Plugin-Panel/master/screenshot.png)   **Tmux Plugin Panel**](https://github.com/psmux/Tmux-Plugin-Panel)   <sub>TUI plugin &amp; theme manager for tmux and psmux — browse, install, update from your terminal</sub>   `cargo install tmuxpanel` | [![OMP Manager screenshot](https://raw.githubusercontent.com/psmux/omp-manager/master/screenshot.png)   **OMP Manager**](https://github.com/psmux/omp-manager)   <sub>Oh My Posh setup wizard — browse 100+ themes, install fonts, configure shells automatically</sub>   `cargo install omp-manager` |

## License

MIT

## Contributing

Contributions welcome — bug reports, PRs, docs, and test scripts via [GitHub Issues](https://github.com/psmux/psmux/issues).

If psmux helps your Windows workflow, consider giving it a ⭐ on GitHub!

## Star History

[![Star History Chart](https://camo.githubusercontent.com/a61074bea987bed1916055996e0136d2845308a429494ce6b02eabf4f63314e8/68747470733a2f2f6170692e737461722d686973746f72792e636f6d2f696d6167653f7265706f733d70736d75782f70736d757826747970653d64617465266c6567656e643d746f702d6c656674)](https://www.star-history.com/?repos=psmux%2Fpsmux&type=date&legend=top-left)

---

Made with ❤️ for PowerShell using Rust 🦀