# Installing in each client

The server is remote: `https://app.arbituro.com/mcp`, streamable HTTP, OAuth. Nothing runs on your
machine and there is no key to paste. The first call opens a browser to sign in.

To reach one workspace only, use `https://app.arbituro.com/mcp/<workspace>` wherever an address
appears below.

## Claude Code

The plugin, with the server and the skills:

```bash
claude plugin marketplace add writan-labs/arbituro-mcp
```

```bash
claude plugin install arbituro@writan-labs
```

The server alone:

```bash
claude mcp add --transport http arbituro https://app.arbituro.com/mcp
```

Run `/mcp` in a session to sign in.

## Codex

```bash
codex mcp add arbituro --url https://app.arbituro.com/mcp
```

```bash
codex mcp login arbituro
```

Or in `~/.codex/config.toml`:

```toml
[mcp_servers.arbituro]
url = "https://app.arbituro.com/mcp"
```

The plugin: add this repository as a marketplace, then install **Arbituro** from the Plugins
directory.

```bash
codex plugin marketplace add writan-labs/arbituro-mcp
```

## Gemini CLI

The extension, with the server, the skills and a context file:

```bash
gemini extensions install https://github.com/writan-labs/arbituro-mcp
```

The server alone:

```bash
gemini mcp add --transport http arbituro https://app.arbituro.com/mcp
```

Run `/mcp auth` in a session to sign in.

## Cursor

In `~/.cursor/mcp.json`, or `.cursor/mcp.json` in a project:

```json
{
  "mcpServers": {
    "arbituro": { "url": "https://app.arbituro.com/mcp" }
  }
}
```

## VS Code and GitHub Copilot

In `.vscode/mcp.json`, or through **MCP: Add Server** and **HTTP**:

```json
{
  "servers": {
    "arbituro": { "type": "http", "url": "https://app.arbituro.com/mcp" }
  }
}
```

## Windsurf

In `~/.codeium/windsurf/mcp_config.json`:

```json
{
  "mcpServers": {
    "arbituro": { "serverUrl": "https://app.arbituro.com/mcp" }
  }
}
```

## OpenCode

In `opencode.json`:

```json
{
  "mcp": {
    "arbituro": { "type": "remote", "url": "https://app.arbituro.com/mcp" }
  }
}
```

## Any other client

Give it the address and choose streamable HTTP. The client reads
`https://app.arbituro.com/.well-known/oauth-protected-resource/mcp` to find where to sign in, and
registers itself. A client that supports neither Client ID Metadata Documents nor Dynamic Client
Registration cannot connect.

## The skills

In any harness that reads Agent Skills:

```bash
npx skills add writan-labs/arbituro-mcp
```

One skill, for one agent:

```bash
npx skills add writan-labs/arbituro-mcp --skill arbituro-work-job -a claude-code
```

## Your repository's AGENTS.md

[snippets/AGENTS.md](../snippets/AGENTS.md) is a paragraph to paste into your own repository's
`AGENTS.md`, so any agent working there puts the job's key in its branch and commits.

## If it does not connect

- **The browser never opens.** Start sign-in by hand: `/mcp` in Claude Code, `codex mcp login
  arbituro`, `/mcp auth` in Gemini CLI.
- **Signed in, and every project is refused.** You are signed in as somebody who is not on that
  project. A project you cannot open and one that does not exist get the same answer.
- **A key is refused with two addresses.** You are on a project with that key in two workspaces.
  Connect the workspace you mean by its own address.
