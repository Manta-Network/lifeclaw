# LifeClaw MCP

LifeClaw lets an AI agent make phone calls on your behalf and bring the answer back. Its hosted MCP server provides three phone capabilities:

- `call_me` calls your verified receiving number when you ask for a phone update or an urgent alert needs your attention.
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
# Claude Code: install for your user (all projects), then run /mcp and authorize in your browser
claude mcp add --scope user --transport http lifeclaw https://api-v2.lifeclaw.agentese.ai/mcp

# Codex: the login command opens the browser authorization flow
codex mcp add lifeclaw --url https://api-v2.lifeclaw.agentese.ai/mcp
codex mcp login lifeclaw
```

Manage these connections in [LifeClaw Settings → Connections → Connected apps](https://lifeclaw.agentese.ai/chat?settings=tokens). OAuth access tokens refresh automatically; the connection's renewal window is 30 days.

For clients using a manual Bearer token, create one in [LifeClaw Settings → Connections → API tokens](https://lifeclaw.agentese.ai/chat?settings=tokens). Configure your MCP client to send it in the `Authorization` header. Keep the token in your client's secret or environment settings; do not commit it to a repository. Client-specific configuration syntax may differ.

For DeepSeek Harness, this repository also includes a [configuration bundle](integrations/deepseek-harness/README.md) that connects its built-in MCP client to LifeClaw. Install it from GitHub with `dsh plugin --profile web add github:Manta-Network/lifeclaw` after setting `LIFECLAW_API_TOKEN` in your environment.

## Things to try

- **Urgent alert:** “If the production outage is still active and I haven't acknowledged the alert after 10 minutes, call me.”
- **Requested update:** “When the long-running job finishes, call me with a short summary.”
- **Business inquiry:** “Call the restaurant and ask whether they have a quiet table for four tonight. Tell me what they say.”
- **Booking:** “Find a nearby dentist, check availability by phone for Friday afternoon, and book a slot after I confirm the details.”
- **Change a booking:** “Call the restaurant to move my confirmed reservation to 7:30 pm and tell me whether they agree.”
- **Contact:** “Call my saved contact Alex and relay this message after I confirm the recipient and wording.”

The 10-minute example needs a running client workflow that waits, checks whether the alert is still active and unacknowledged, then asks LifeClaw to call. LifeClaw handles the phone call; the client handles the timer and alert checks.

Calls may consume credits and require phone setup. Verify your receiving number before using `call_me`. Confirm the recipient, number, and exact message before using `call_person`. See the [MCP documentation](https://lifeclaw.agentese.ai/mcp) for limits and usage examples.

Support: [LifeClaw Telegram](https://t.me/agenteseAI). The public configuration files in this repository are licensed under [MIT](LICENSE).
