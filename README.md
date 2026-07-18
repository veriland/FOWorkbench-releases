<div align="center">

# FinOps Workbench

**One desktop app for managing Microsoft Power Platform and Dynamics 365 Finance & Operations environments.**

List and provision environments · request just-in-time SQL access · query environment databases · download Lifecycle Services assets · follow lifecycle operations · expose an MCP server for AI tooling.

### [⬇ Download the latest release](https://github.com/veriland/FOWorkbench-releases/releases/latest) · [📖 User Guide](docs/USER_GUIDE.md)

![Environments view](docs/images/environments.png)

</div>

---

## Download

Get the latest installer from the **[Releases](https://github.com/veriland/FOWorkbench-releases/releases/latest)** page.

| Installer | For |
|---|---|
| `FinOpsWorkbench-<version>-x64-setup.exe` | 64-bit Windows (most PCs) |
| `FinOpsWorkbench-<version>-arm64-setup.exe` | Windows on ARM |
| `FinOpsWorkbench-<version>-ia32-setup.exe` | 32-bit Windows |
| `FinOpsWorkbench-<version>-setup.exe` | Combined (auto-selects your architecture) |

If you're unsure, download the **x64** installer.

## What it does

- **Environments** — every environment in one grid with live status, capacity,
  versions and lifecycle state. Provision and copy environments.
- **Just-in-time SQL access** — temporary SQL credentials with a ready-to-use
  connection string.
- **SQL workspace** — browse and query environment databases SSMS-style.
- **Assets** — download VHDs, deployable/data packages, database backups and
  developer tools, and track what you've downloaded.
- **Lifecycle operations** — trigger database sync and follow progress, with a
  full operation history.
- **MCP server** — expose your session to Claude Desktop / Claude Code for AI
  tooling (read-only by default).

👉 See the **[illustrated User Guide](docs/USER_GUIDE.md)** for a full walkthrough.

## Installing

1. Download the installer for your architecture.
2. Run it and follow the prompts (installs per-user; no administrator rights
   required).

> The installers are not code-signed, so Windows SmartScreen may show a warning
> on first launch. Choose **More info → Run anyway** to proceed.

## Requirements

- Windows 10/11 (x64, ARM64, or 32-bit)
- A Microsoft Entra ID account with access to the Power Platform / D365 F&O
  environments you want to manage

## About

Built and maintained by **Veriland Consulting** for the Dynamics 365 community —
free to use and share. This repository hosts the public downloads and user guide
only.
