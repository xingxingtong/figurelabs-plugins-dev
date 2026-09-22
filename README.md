# FigureLabs Dev Plugin

FigureLabs plugin with MCP integration and scientific visualization skills for creating and editing scientific illustrations, data plots, and flowcharts in Codex.

This repository distributes the **dev environment** plugin. It connects to `https://txx.natappvip.cc/plot-mcp` and requires a FigureLabs account with access to that environment. The remote service runs separately from this repository; downloading the files does not start or deploy a server.

## Install in Codex

Use a Codex version that supports plugin marketplaces:

```sh
codex plugin marketplace add xingxingtong/figurelabs-plugins-dev --ref main
```

Open the client's Plugins page, find the **Figurelabs Dev Marketplace** source, and install **FigureLabs Dev**. Complete the authentication flow when prompted, then start a new conversation and select the plugin. The marketplace identifier is `figurelabs-dev-marketplace`.

If the source does not appear, restart the client and inspect registered sources with:

```sh
codex plugin marketplace list
```

If your client does not recognize `codex plugin marketplace`, update to a version with plugin marketplace support. Support for third-party marketplaces varies by client and workspace policy. Publishing this repository does not list the plugin in OpenAI's public Plugins Directory.

### Dev from a local clone

```sh
git clone https://github.com/xingxingtong/figurelabs-plugins-dev.git
cd figurelabs-plugins-dev
codex plugin marketplace add .
```

Then install and authenticate the plugin in the client as above. Use either the GitHub source or the local source for a dev session, so you can identify which copy is installed.

## Try it

Start with an empty project to check connection and authorization:

> Connect to FigureLabs Dev, open an empty illustration project, and introduce the available capabilities. Do not generate an image yet.

Then try a workflow:

- Create a scientific illustration explaining a research mechanism.
- Create a data plot from an attached CSV, XLS, or XLSX file.
- Turn an experimental procedure into an editable flowchart.
- Change the labels, colors, or layout of an existing figure.

Generation and editing use the dev service's account permissions, quotas, and applicable credit rules. Browser interactions require a compatible browser capability in the host; the skills describe a fallback when it is unavailable.

## Included workflows

| Skill | Purpose |
| --- | --- |
| `figurelabs-dev-onboarding` | Connect, introduce capabilities, and create or reopen a workspace |
| `figurelabs-dev-generation` | Generate scientific illustrations, real-data plots, and flowcharts |
| `figurelabs-dev-browser-handoff` | Open or refresh the editable project and handle browser limitations |
| `figurelabs-dev-canvas-edit` | Revise an existing figure or use available canvas controls |
| `figurelabs-dev-file-import` | Import reference images and plotting data |

## Repository layout

```text
.agents/plugins/marketplace.json
plugins/figurelabs-dev/
  .codex-plugin/plugin.json
  .mcp.json
  skills/
README.md
README.zh-CN.md
.gitignore
```

The marketplace points to `./plugins/figurelabs-dev`, relative to the repository root. Keep all skill reference files and the dot-prefixed configuration files when copying or uploading the repository.

## Update

```sh
codex plugin marketplace upgrade figurelabs-dev-marketplace
```

Refresh or update the installed plugin in the client as needed, then start a new conversation. Installed plugins use a cached copy; changing the repository does not change every existing session immediately.

## Maintainer upload

Push the **contents of this directory** to the root of `figurelabs-ai/figurelabs-plugins-dev` on `main`. The repository root must contain `.agents/` and `plugins/`, without an extra enclosing folder. Do not upload a ZIP as the only repository file: Codex needs the extracted files in Git.

Only the client plugin configuration and skills are included. Each user authenticates separately; do not commit access tokens, API keys, local client settings, or backend configuration. Keep the `figurelabs-dev` name and dev endpoint together. Distribute a separately named production plugin when you are ready for production use.

See the [official OpenAI plugin packaging documentation](https://developers.openai.com/plugins/build/plugins) for marketplace setup details.
