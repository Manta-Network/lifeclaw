# DeepSeek Harness

This configuration bundle adds the hosted LifeClaw MCP server to a DeepSeek Harness profile through its built-in `@deepseek-ai/dsh-mcp-client`. It contains no LifeClaw server code or credentials.

1. Create a personal API token in [LifeClaw Connections](https://lifeclaw.agentese.ai/chat?settings=tokens).
2. Set `LIFECLAW_API_TOKEN` in the environment that starts DeepSeek Harness. Do not save it in this repository or a profile file.
3. Install the public bundle into the profile you use, then restart that profile:

   ```bash
   export LIFECLAW_API_TOKEN='lc_your_token_here'
   dsh plugin --profile web add github:Manta-Network/lifeclaw
   dsh --profile web --dump-config
   dsh web
   ```

The config dump should include a `dsh-lifeclaw-mcp` layer with an `mcp-lifeclaw` row. In a running session, LifeClaw tools are named `mcp__lifeclaw__<tool>`. Ask the agent to check your account status to confirm the connection without placing a call.

![LifeClaw configuration bundle installed in DeepSeek Harness](../../assets/deepseek-harness-plugin.jpg)

The screenshot shows the bundle loaded in an isolated Web profile. It does not show an authenticated tool call.

To remove the bundle:

```bash
dsh plugin --profile web remove dsh-lifeclaw-mcp
```

The MCP client evaluates the token environment variable at startup. Restart Harness after setting or rotating it. Calls can consume LifeClaw points; check the recipient and action before approving a phone call.

This is an unofficial community integration maintained by LifeClaw, not a DeepSeek AI product. See the [DeepSeek Harness bundle guide](https://github.com/deepseek-ai/deepseek-harness/blob/master/docs/user/develop/basic/publish.md) and [MCP client configuration](https://github.com/deepseek-ai/deepseek-harness/blob/master/packages/mcp/mcp-client/README.md).
