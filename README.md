<p align="center"><img src="assets/logo.png" width="96" height="96" alt="Aeon"></p>

# Aeon MCP

Connect your coding agent to [Aeon](https://www.aeon.fun/connect), the open-source autonomous agent that runs skills on a schedule with GitHub Actions in your own repo. This repo is a small plugin and extension that points Claude Code, Codex, Gemini CLI, Cursor, VS Code, GitHub Copilot CLI and Grok at Aeon's hosted MCP server. There is nothing to run locally and no API key.

**Server URL:** `https://www.aeon.fun/connect/mcp` (remote, Streamable HTTP, OAuth 2.1 with PKCE)

With it you can list and run skills, follow runs and read their output, search the agent's memory, edit its strategy and voice, install skill packs and change settings, all from chat. Writes commit to your own repo, and secrets are never readable over MCP.

## Sign in

The first time your client connects, it opens a browser window. Sign in with GitHub and pick which Aeon agent (repo) the client may use. That is all the setup there is. Don't have an agent yet? Start at [www.aeon.fun/connect](https://www.aeon.fun/connect).

## Install

### Claude Code

```bash
claude mcp add --transport http aeon https://www.aeon.fun/connect/mcp
```

Then run `/mcp` in Claude Code and sign in. Or install this repo as a plugin:

```bash
claude plugin marketplace add aeonfun/aeon-mcp
claude plugin install aeon@aeon
```

### Codex

```bash
codex mcp add aeon --url https://www.aeon.fun/connect/mcp
```

If the sign-in window does not open, run `codex mcp login aeon`.

### Gemini CLI

Install this repo as an extension:

```bash
gemini extensions install https://github.com/aeonfun/aeon-mcp
```

Then run `/mcp auth aeon` in Gemini CLI to sign in. To add only the server instead: `gemini mcp add --transport http aeon https://www.aeon.fun/connect/mcp`.

### Cursor

[Add to Cursor](https://cursor.com/install-mcp?name=aeon&config=eyJ1cmwiOiJodHRwczovL3d3dy5hZW9uLmZ1bi9jb25uZWN0L21jcCJ9), or add this to `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "aeon": { "url": "https://www.aeon.fun/connect/mcp" }
  }
}
```

### VS Code

```bash
code --add-mcp '{"name":"aeon","type":"http","url":"https://www.aeon.fun/connect/mcp"}'
```

Or add this to `.vscode/mcp.json`:

```json
{
  "servers": {
    "aeon": { "type": "http", "url": "https://www.aeon.fun/connect/mcp" }
  }
}
```

### GitHub Copilot CLI

```bash
copilot plugin install aeonfun/aeon-mcp
```

### Grok

In Grok, open **Connectors > New > Custom** and paste `https://www.aeon.fun/connect/mcp`.

### Any other MCP client

```json
{
  "mcpServers": {
    "aeon": { "url": "https://www.aeon.fun/connect/mcp" }
  }
}
```

## Tools

27 tools, including `list_skills`, `run_skill`, `list_runs`, `get_run`, `read_output`, `update_skill`, `read_memory`, `search_memory`, `read_strategy`, `update_strategy`, `read_soul`, `update_soul`, `list_packs`, `install_pack`, `setup_status`, `list_instances`, `switch_instance`, `read_instance_settings`, `update_instance_settings` and `open_runs` (a runs dashboard in clients that support MCP Apps). Write tools are annotated so your client can ask before using them.

## What is in this repo

| File | For |
| --- | --- |
| `plugin.json` + `mcp.json` | [Agent Plugins](https://agent-plugins.org) standard (GitHub Copilot CLI, VS Code, Cursor) |
| `.claude-plugin/` + `.mcp.json` | Claude Code plugin and marketplace |
| `.cursor-plugin/plugin.json` | Cursor plugin |
| `.grok-plugin/plugin.json` | Grok Build plugin |
| `gemini-extension.json` + `GEMINI.md` | Gemini CLI extension |

Every file only points at `https://www.aeon.fun/connect/mcp`. No code runs on your machine, and the plugin reads no local files or environment variables.

## Links

- Docs: [www.aeon.fun/docs#mcp-hosted](https://www.aeon.fun/docs#mcp-hosted)
- Official MCP Registry: `fun.aeon/aeon`
- Aeon framework (MIT): [github.com/aeonfun/aeon](https://github.com/aeonfun/aeon)
- Privacy: [www.aeon.fun/privacy](https://www.aeon.fun/privacy)
- Terms: [www.aeon.fun/terms](https://www.aeon.fun/terms)
- Support: [aaron@aeon.fun](mailto:aaron@aeon.fun)

Made by Aaron Elijah Mars. MIT license.
