<p align="center">
  <img src="assets/wizbi-logo.svg" alt="WizBI" width="96" height="96">
</p>

<h1 align="center">WizBI MCP server</h1>

<p align="center">
  Your organization's connected business data and its context, read with each person's permissions.<br>
  <a href="https://wizbi.ai">wizbi.ai</a>
</p>

---

WizBI connects your AI assistant to the data your organization has connected to WizBI, such as its ERP, databases and spreadsheets, and to its definitions: instructions, glossary and table notes.

WizBI is a hosted remote MCP server. This repository holds only its public documentation and manifests; there is no server code here.

| | |
|---|---|
| Server address | `https://mcp.wizbi.ai` |
| Transport | Streamable HTTP |
| Sign-in | OAuth 2.1, with your own WizBI account |
| Access | By invitation from your organization's admin |
| Data access | Read-only |
| MCP Registry | [`ai.wizbi/wizbi`](https://registry.modelcontextprotocol.io/v0.1/servers?search=ai.wizbi) |
| Languages | English, Hebrew, Portuguese |

## What you can do

- Get your organization's context for a question: instructions, data guide, glossary, table notes and your access.
- See what data exists: list tables, read columns, find a column by name, search the catalog, and see how fresh each dataset is.
- Run one read-only SQL statement (BigQuery Standard SQL) over the connected datasets.
- See your organizations and the AI agents connected to your account.

**Your permissions apply.** You sign in with your own WizBI account, and WizBI returns only what you may see in your organization. Tables and columns outside your permissions are refused or removed.

**Read-only.** This connection reads data. It changes nothing in your organization's systems and sends no messages.

## Before you connect

Access to WizBI is by invitation. You need:

1. A WizBI account, through an invitation from your organization's admin.
2. An organization on WizBI with at least one data source connected.

Without an invitation, sign-in shows that you have no access yet, and no data is available. To bring WizBI to your organization, [contact us](https://wizbi.ai/contact).

## Connect

Every client connects to the same address, `https://mcp.wizbi.ai`, and then asks you to sign in to WizBI in your browser. No key or token is copied anywhere.

### Claude

[Add WizBI to Claude](https://claude.ai/customize/connectors?modal=add-custom-connector&connectorName=WizBI&connectorUrl=https%3A%2F%2Fmcp.wizbi.ai) (opens the "Add custom connector" dialog with WizBI filled in), or by hand:

1. In Claude, open **Customize → Connectors**.
2. Click **+** or **Add custom connector**.
3. Enter `WizBI` as the name, paste `https://mcp.wizbi.ai` as the address, and click **Add**.
4. Click **Connect** and sign in to WizBI.

On a Claude Team or Enterprise plan, whoever runs the company's Claude account adds WizBI once, and everyone else just clicks **Connect**. Once added on claude.ai or in the Claude desktop app, it works in the Claude mobile app too.

### ChatGPT (custom connector)

1. On ChatGPT on the web, open **Plugins → + → Add custom MCP server**.
2. Enter `WizBI` as the name and paste `https://mcp.wizbi.ai`.
3. Choose **OAuth**, confirm the warning and select **Create as a plugin**.
4. Install the plugin and sign in to WizBI.

On Business, Enterprise and Edu plans, an admin, or someone the admin allows, does this.

### Claude Code

```bash
claude mcp add --transport http --scope user wizbi https://mcp.wizbi.ai
```

Then run `/mcp` inside Claude Code and choose `wizbi` to sign in.

### Gemini CLI

Install this repository as an extension:

```bash
gemini extensions install https://github.com/wizbi-ai/wizbi-mcp
```

Or add the server directly:

```bash
gemini mcp add --transport http --scope user wizbi https://mcp.wizbi.ai
```

Then run `/mcp auth wizbi` inside Gemini CLI. It opens your browser to sign in to WizBI.

### Visual Studio Code

```bash
code --add-mcp '{"name":"wizbi","type":"http","url":"https://mcp.wizbi.ai"}'
```

Or add it to `.vscode/mcp.json` in a workspace:

```json
{
  "servers": {
    "wizbi": {
      "type": "http",
      "url": "https://mcp.wizbi.ai"
    }
  }
}
```

VS Code asks you to sign in to WizBI the first time it starts the server.

### Cursor

Add it to `~/.cursor/mcp.json` (every project) or `.cursor/mcp.json` (one project):

```json
{
  "mcpServers": {
    "wizbi": {
      "url": "https://mcp.wizbi.ai"
    }
  }
}
```

Cursor asks you to sign in to WizBI when it connects.

### Other MCP clients

Clients that run on your computer and support OAuth can usually connect to the same address. A web-based client that is not listed here may not be able to sign in yet; [let us know](https://wizbi.ai/contact) which one you use.

## Your data

WizBI receives what your AI client sends in a tool call, such as a question or a SQL statement. It has no tool that reads your AI client's memory, chat history or files. WizBI does not use identifiable information of a customer, its inputs or its outputs to train foundation models. See the [privacy policy](https://legal.wizbi.ai/privacy/en).

Answers are written by your AI assistant and may contain errors. Check important figures against the source.

## Links

- Website: https://wizbi.ai
- Privacy policy: https://legal.wizbi.ai/privacy/en
- Terms of service: https://legal.wizbi.ai/terms/en
- Security: https://wizbi.ai/security
- Support: contact@wizbi.ai · [contact page](https://wizbi.ai/contact) · [support hours and response targets](https://legal.wizbi.ai/support) (Hebrew)
- Security reports: security@wizbi.ai

## This repository

| File | What it is |
|---|---|
| `server.json` | A copy of the server's entry in the official MCP Registry |
| `gemini-extension.json` | The Gemini CLI extension manifest |
| `assets/` | The WizBI logo |

## License

The documentation and manifests in this repository are under the [MIT License](LICENSE). The license covers only these files. It grants no rights to the WizBI service, which is provided under its [terms of service](https://legal.wizbi.ai/terms/en), and none to the WizBI name and logo, which remain the trademarks of WIZBI.AI LTD.

WizBI is provided by WIZBI.AI LTD.
