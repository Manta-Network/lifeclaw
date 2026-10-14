# LifeClaw for Cursor

Connect Cursor to LifeClaw's hosted MCP server. Your agent can:

- `call_me` to reach you by phone when an urgent decision needs your answer, including when you have not responded in chat;
- `call_person` to relay a confirmed message to a private contact by phone;
- `call_business` to ask a business a question or make a booking by phone, then bring the answer back.

Install the plugin, then set `LIFECLAW_API_TOKEN` to **your own** `lc_` token from [LifeClaw API key settings](https://lifeclaw.agentese.ai/chat?settings=tokens). The plugin sends it as a Bearer token to the [LifeClaw MCP endpoint](https://api-v2.lifeclaw.agentese.ai/mcp). Do not put tokens in this repository.

Calls may incur charges and require the relevant phone setup and account balance. Confirm the recipient, number, and exact message before relaying to a person. For `call_me`, set and verify a receiving number in LifeClaw first. See [MCP documentation](https://lifeclaw.agentese.ai/mcp) for setup, limits, and examples.

Support: [LifeClaw Telegram](https://t.me/agenteseAI).
