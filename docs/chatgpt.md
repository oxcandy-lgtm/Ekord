# Connect ChatGPT

Use Ekord as a remote MCP server in an OpenAI/ChatGPT surface that supports
remote MCP with OAuth.

1. Add a custom/remote MCP server.
2. Enter only the Ekord MCP endpoint below.
3. Follow the OAuth prompt, sign in to the Ekord account that owns the paired
   machine, and choose **Allow**.
4. Ask the client to inspect or change something disposable on the machine.

```text
https://ekord.app/mcp
```

Do not paste an Ekord API key, OAuth client secret, authorization URL, or token
into ChatGPT. The MCP endpoint exposes the discovery metadata needed by capable
clients.

If the client later reports the connection as unauthorized, re-authorize the
Ekord server from that client's MCP settings.
