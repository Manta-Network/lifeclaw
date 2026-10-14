# OpenAI directory submission package

This folder is a portable Agent Plugins package for the shared ChatGPT and Codex directory. Its `mcp.json` uses LifeClaw OAuth with Dynamic Client Registration. It contains no access token, client secret, or server source code.

Build a ZIP with `plugin.json`, `mcp.json`, and `assets/logo.png` at the ZIP root:

```bash
cd integrations/openai
zip -r lifeclaw-openai-plugin.zip plugin.json mcp.json assets/logo.png
```

Upload the ZIP at [OpenAI Plugins](https://platform.openai.com/plugins), choose the verified developer identity, verify the MCP domain, and connect the server. Public submission also needs a dedicated review account, five positive and three negative test cases, and an accessible demo recording. Wait until the LifeClaw OAuth endpoint has been deployed and tested before connecting the server.

The repository-root `mcp.json` is a manual Bearer-token example for other MCP clients. Use this folder's `mcp.json` for the OpenAI directory; the public submission portal does not accept a fixed Bearer token in `headers`.
