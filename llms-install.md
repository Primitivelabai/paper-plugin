# Installing primitive paper (for agents like Cline)

primitive paper is a **hosted remote MCP server**. There is nothing to clone, build or install, and no API key to paste.

- URL: `https://paper.primitiveai.com.au/mcp`
- Transport: streamable HTTP
- Auth: OAuth 2.1 with dynamic client registration (the client registers itself, then opens a browser sign-in)

## Steps

1. Add this server to the MCP settings file (for Cline, `cline_mcp_settings.json`):

```json
{
  "mcpServers": {
    "primitive-paper": {
      "type": "streamableHttp",
      "url": "https://paper.primitiveai.com.au/mcp",
      "disabled": false
    }
  }
}
```

2. When the server first connects, a browser sign-in page opens. The user signs in to paper and chooses which items this connection can see and whether it can read, suggest edits, or read form answers (`paper:read`, `paper:write`, `paper:responses`).
3. Confirm it works by calling the `discover_capabilities` tool, or asking "what's in my paper?".

The user needs a paper account, which they can open at https://paper.primitiveai.com.au.

## How to behave once connected

- Read before you write, and re-read if the page changed.
- Edits arrive as suggestions the user approves; nothing saves without their OK.
- Every change returns a receipt that can be undone.
