# OpenAI Plugins handoff — LifeClaw

Open <https://platform.openai.com/plugins> in the **Manta OpenAI organization**. The portable Agent Plugins package is in [`integrations/openai/`](../integrations/openai/). Upload the ready ZIP [`lifeclaw-openai-plugin.zip`](./lifeclaw-openai-plugin.zip), which contains only `plugin.json`, `mcp.json`, and `assets/logo.png`. The directory serves ChatGPT and Codex after approval and publication.

## Package and listing values

| Field | Value |
| --- | --- |
| Plugin name / display name | `lifeclaw` / LifeClaw |
| MCP server | `https://api-v2.lifeclaw.agentese.ai/mcp` |
| Transport / auth | Streamable HTTP; OAuth with DCR; scope `lifeclaw:mcp` |
| Short description | Phone calls for your agent |
| Category | Productivity |
| Website / docs | `https://lifeclaw.agentese.ai/` / `https://lifeclaw.agentese.ai/mcp` |
| Support / privacy / terms | `https://t.me/agenteseAI` / `https://lifeclaw.agentese.ai/privacy` / `https://lifeclaw.agentese.ai/terms` |
| Logo and composer icon | [`assets/logo.png`](../integrations/openai/assets/logo.png), included in the ZIP |
| Publisher identity | Select the verified Manta business identity. Confirm the exact registered name before submitting; LifeClaw supplied **P0XEIDON LABS PTE. LTD.** |

The full description and three starter prompts are already in [`plugin.json`](../integrations/openai/plugin.json). The manifest contains no credential or test-account data. The OAuth configuration is in [`mcp.json`](../integrations/openai/mcp.json); do **not** upload the repository-root `mcp.json`, which is a manual-token example.

## Submission sequence

1. Finish **business developer identity verification** in [organization settings](https://platform.openai.com/settings/organization/general). An organization Owner can submit; another member needs Apps Management Write. Use a project with global data residency if submitting a remote MCP server.
2. In [Plugins](https://platform.openai.com/plugins), upload the ZIP, select the verified identity, and resolve metadata findings. Verify the MCP domain using the exact challenge token and URL shown by the portal; it may require a deployed `/.well-known/openai-apps-challenge` response.
3. Connect the included MCP server via OAuth, run **Scan Tools**, and resolve required scan findings. Review all tool annotations and supply honest per-tool justifications for `readOnlyHint`, `openWorldHint`, and `destructiveHint` where the portal asks.
4. In **Review details**, enter a dedicated reviewer account and login instructions through the private form. It must work without MFA, SMS/email codes, magic links, or private-network access. Provide enough points and verified phone setup to run the proposed scenarios. Do not place its credentials in the ZIP, repository, or a message to coworkers.
5. Use [review cases](./OPENAI-REVIEW-CASES.md) as a draft for **five positive and three negative cases**. Run and adjust every case against the actual reviewer account before entering it. Record a reviewer-accessible demo video and enter its URL in the portal; add release notes (suggested: “Initial LifeClaw MCP release with account status, business search, verified phone calls, message relay, contacts, and call results.”).
6. Complete policy attestations, submit for review, save the draft/review URL, and **publish after approval**. Approval alone does not create a public listing.

## Check before final submission

- The public [Privacy Policy](https://lifeclaw.agentese.ai/privacy) and [Terms](https://lifeclaw.agentese.ai/terms) currently refer to the **Agentese Labs brand**; confirm this matches the verified **P0XEIDON LABS PTE. LTD.** identity.
- A production login → consent → token exchange → authenticated call from ChatGPT/Codex has not been documented as tested. Complete it with the dedicated reviewer account.
- LifeClaw currently offers Google or email/phone one-time-code sign-in, while OpenAI's review instructions exclude MFA, SMS/email codes, and magic links. A reviewer-ready login path or usable dedicated social-login account must be confirmed first; the ZIP alone does not remove this blocker.
- The current MCP tool declarations include `title` and all three boolean hints. OpenAI additionally requires a **justification for every hint on every tool**; complete those in the portal and fix any scan errors on the server. Do not attest that the scan passed before it does.
- The supplied review cases are **drafts**. Actual phone numbers, named businesses, contacts, call charges, results and demo recording depend on the reviewer account and must be confirmed by the submitting teammate.

## Tool annotation notes for the scan

These are explanations of the server's current advertised values, not substitutes for the portal's per-tool fields. Check the live scan because deploying a change may alter them.

| Tools | Current hints | Why |
| --- | --- | --- |
| `search_places`, `get_place` | read-only false; destructive false; open-world true | Search/detail requests use a paid third-party public business data service and spend points. They do not place calls or modify external records. |
| `call_business`, `modify_booking`, `call_person`, `call_contact`, `call_me` | read-only false; destructive true; open-world true | These initiate real phone calls to external parties and can communicate or change a booking; a placed call cannot be undone. |
| `wait_for_call`, `list_bookings`, `account_status`, `receiving_phone_status`, `list_contacts` | read-only true; destructive false; open-world false | These retrieve the connected account's task, booking, balance, phone, or contact data. |
| `caller_id_status` | read-only false; destructive false; open-world false | The status check may reconcile LifeClaw's stored Caller ID state with Twilio; it does not initiate a call. |
| `save_contact`, `update_contact`, `delete_contact` | read-only false; destructive true; open-world false | These change or remove contact records in the connected LifeClaw account; deletion and overwrite are not always reversible. |

Official instructions: [Upload and submit](https://developers.openai.com/plugins/deploy/submission), [Remote MCP review](https://developers.openai.com/plugins/deploy/app-review), [Submission errors](https://developers.openai.com/plugins/deploy/submission-errors).
