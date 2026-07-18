# FinOps Workbench — User Guide

A walkthrough of everything FinOps Workbench does. Screens shown use sample data.

- [Getting started](#getting-started)
- [The Environments view](#the-environments-view)
- [Requesting just-in-time SQL access](#requesting-just-in-time-sql-access)
- [The SQL workspace](#the-sql-workspace)
- [Downloading assets](#downloading-assets)
- [The MCP server](#the-mcp-server)
- [Settings & appearance](#settings--appearance)

---

## Getting started

1. Install and launch the app (see the [downloads](https://github.com/veriland/FOWorkbench-releases/releases/latest)).
2. On the **Environments** page, click **Sign in**. A Microsoft sign-in window
   opens — sign in with your Entra ID account.
3. Once signed in, your name and account appear in the bottom-left corner and the
   environment list loads automatically.

Your session is remembered securely between launches, so you normally only sign
in once.

---

## The Environments view

The home page lists every environment you can administer, with live status,
capacity, versions and lifecycle state.

![Environments view](images/environments.png)

**Layout**

- **Left rail** — switch between the four areas (Environments, SQL Workspace,
  Assets, MCP Server). Your signed-in account sits at the bottom.
- **Ribbon** — grouped actions (Authentication, Lifecycle, Data ops, View). Buttons
  enable or disable based on the selected environment.
- **Grid** — one row per environment. The **Kind** column shows whether an
  environment is a unified developer environment (**UDE**), an **LCS**-managed
  environment, or a plain **Dataverse** environment. Coloured **State** pills give
  status at a glance.
- **Details tab** (right edge) and **Activity log** (bottom edge) — both tuck away
  by default; click the tab to expand. Details shows a full breakdown of the
  selected environment; the Activity log records everything the app does.

**Common actions**

| Action | What it does |
|---|---|
| **New** | Provision a new environment. |
| **Copy** | Overwrite a target environment with a copy of the selected one. |
| **Delete** | Permanently delete an environment (type-to-confirm). |
| **Refresh** | Reload the list and fetch F&O details. |
| **History** | Show the lifecycle-operation history for the environment. |
| **Request SQL access** | Get temporary SQL credentials (see below). |
| **SQL Workspace ▾** | Open the F&O database or the Dataverse tables in the query workspace. |
| **DB Sync** | Trigger a database synchronisation and follow it in the background. |
| **Download assets** | Open the asset-download picker (see below). |
| **Save JSON** | Save the raw environment definition to a file. |

Double-click any row to see its full JSON (a curated **Details** tab and the
**Raw JSON**).

---

## Requesting just-in-time SQL access

Select an environment and click **Request SQL access**. Choose the access level
(read or read/write) and a reason; the app opens the SQL firewall for your current
IP and requests time-limited credentials. For LCS-managed environments it signs
you in to Lifecycle Services once and requests access there.

The result is the **SQL JIT credentials** viewer:

![SQL JIT credentials](images/jit-credentials.png)

- **Credentials tab** — the server, database, user name, password (masked, with a
  **Show** toggle), role and expiry (with the time remaining), plus a ready-to-use
  **connection string**.
- **Copy connection string** puts the .NET/SSMS-ready connection string on the
  clipboard; **Copy JSON** copies the raw response; **Raw JSON** shows the full
  response on its own tab.
- **Re-request** obtains a fresh grant — for example to upgrade a read grant to
  read/write.

The granted credentials are cached for the session (the environment's **SQL
access** column shows a key), so the **SQL Workspace ▾ → F&O database** option
opens straight away without asking again — and re-opening **Request SQL access**
just shows the held credentials while they're still valid for your IP.

---

## The SQL workspace

An SSMS-style workspace for browsing and querying environment databases.

![SQL Workspace](images/sql-workspace.png)

- **Object tree** (left) — expand an environment to browse schemas, tables and
  views; type in the filter box to find objects quickly.
- **Query tabs** (right) — each tab has a SQL editor (press **F5** to run) and a
  results grid. Double-click a table to open a `SELECT TOP 1000` tab.
- Multiple environments — and both the F&O and Dataverse endpoints of the same
  environment — can be open side by side as separate top-level nodes.

Open it from the Environments page via **SQL Workspace ▾**: the **F&O database**
item uses a held SQL grant; the **Dataverse tables** item connects to the org's
read-only endpoint with your signed-in identity (no separate credentials needed).

---

## Downloading assets

Select an environment and click **Download assets** to open the picker. It lists
everything available for that environment — downloadable VHD versions, developer
tools, and (for LCS-managed environments) the project's asset library and database
backups. Tick what you want and click **Download…** to save to a folder.

The **Assets** page is your download library — it shows what you've already
downloaded, with quick actions to open the file or its folder, or remove it.

![Assets library](images/assets.png)

---

## The MCP server

FinOps Workbench can expose your signed-in session to AI tooling (Claude Desktop
or Claude Code) through a built-in **Model Context Protocol** server. An assistant
can then list and inspect environments, read F&O details, and run SQL on your
behalf.

![MCP Server](images/mcp-server.png)

1. Set the **Host** / **Port** (defaults are fine for local use).
2. Click **Start**.
3. Use **Add to Claude Code** / **Add to Claude Desktop** to register the server,
   or **Copy config** to paste the connection into your client manually.

Write operations (create/copy/delete/DB sync) are **off by default** — turn on
**Allow write ops** only if you want the assistant to make changes. The endpoint is
localhost-only; don't expose it beyond your machine.

---

## Settings & appearance

Open **Settings** from the ribbon.

![Settings](images/settings.png)

- **Theme** — follow Windows, or pin Light/Dark. The whole app (below) re-themes
  instantly.
- **Load LCS environments** — also crawl Lifecycle Services for environments that
  aren't in the Power Platform admin list.
- **LCS region** — pick the regional LCS endpoint used for asset downloads.

The app follows your Windows light/dark preference automatically:

![Dark mode](images/environments-dark.png)
