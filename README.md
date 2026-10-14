# LifeClaw MCP

LifeClaw lets an AI agent make phone calls on your behalf and bring the answer back. Its hosted MCP server provides three phone capabilities:

- `call_me` calls your verified receiving number when an urgent decision needs your answer, including when you have not responded in chat.
- `call_person` relays a message you confirmed to a specified person.
- `call_business` calls a business for an inquiry or booking and returns the result.

## Connect

| Item | Value |
| --- | --- |
| MCP transport | Streamable HTTP |
| Endpoint | `https://api-v2.lifeclaw.agentese.ai/mcp` |
| Authentication | LifeClaw OAuth or `Authorization: Bearer lc_...` |
| Setup and tool documentation | [lifeclaw.agentese.ai/mcp](https://lifeclaw.agentese.ai/mcp) |

Claude Code and Codex can open LifeClaw's browser authorization flow without a manually created API token:

```bash
# Claude Code: run /mcp after adding the server, then authorize in your browser
claude mcp add --transport http lifeclaw https://api-v2.lifeclaw.agentese.ai/mcp

# Codex: the login command opens the browser authorization flow
codex mcp add lifeclaw --url https://api-v2.lifeclaw.agentese.ai/mcp
codex mcp login lifeclaw
```

Manage these connections in [LifeClaw Settings → Connections → Connected apps](https://lifeclaw.agentese.ai/chat?settings=tokens). OAuth access tokens refresh automatically; the connection's renewal window is 30 days.

For clients using a manual Bearer token, create one in [LifeClaw Settings → Connections → API tokens](https://lifeclaw.agentese.ai/chat?settings=tokens). Configure your MCP client to send it in the `Authorization` header. Keep the token in your client's secret or environment settings; do not commit it to a repository. Client-specific configuration syntax may differ.

Calls may consume credits and require phone setup. Verify your receiving number before using `call_me`. Confirm the recipient, number, and exact message before using `call_person`. See the [MCP documentation](https://lifeclaw.agentese.ai/mcp) for limits and usage examples.

Support: [LifeClaw Telegram](https://t.me/agenteseAI). The public configuration files in this repository are licensed under [MIT](LICENSE).
