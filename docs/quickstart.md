# Quickstart

1. Sign in to Ekord with Google.
2. Install and start the Agent on the machine you want to use (macOS arm64):

   ```sh
   curl -fsSL https://ekord.app/install | sh
   ekord
   ```

3. The Agent opens the pairing page automatically. You can also enter its
   6-character code from Connections. The code is valid for 15 minutes; verify
   the device name and code, then approve it.
4. Add `https://ekord.app/mcp` as a remote MCP server in ChatGPT/OpenAI and
   complete OAuth with the same Ekord account.
5. Ask the AI to inspect a file, make a disposable change, and verify it.

After pairing, the Agent reuses its device credential on restart. Normal
restarts do not require another pairing approval.

More detail: [Connect ChatGPT](./chatgpt.md) · [Agent](./agent.md) ·
[Tools](./tools.md).
