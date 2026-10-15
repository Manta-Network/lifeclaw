# Claude Directory handoff — LifeClaw MCP connector

Submit from the **Manta Claude organization** at <https://claude.ai/directory/manage>. Choose **Submit new → MCP connector** (a remote server URL); this submission does not require a repository upload. A Team or Enterprise organization Owner can submit. The connector is a public directory listing, not an organization-only connector.

## Copy into the listing

| Field | Value |
| --- | --- |
| Server URL | `https://api-v2.lifeclaw.agentese.ai/mcp` |
| Name | LifeClaw |
| One-liner | Let Claude call you, a contact, or a business and bring the answer back. |
| Description | LifeClaw gives Claude phone tools for time-sensitive decisions, approved message relay, and business inquiries or bookings. Connect your LifeClaw account with OAuth. Calls use LifeClaw points and may require a verified receiving number or outbound Caller ID. LifeClaw does not monitor events or schedule calls on Claude's behalf; the calling workflow must decide when to use the tools. |
| Suggested categories | Productivity; Communication (choose only categories offered in the portal) |
| Documentation | `https://lifeclaw.agentese.ai/mcp` |
| Privacy policy | `https://lifeclaw.agentese.ai/privacy` |
| Support contact | `lifeclaw@manta.network` |
| Icon file | [`assets/logo.png`](../assets/logo.png) |
| Suggested slug | `lifeclaw` if available; check before publishing because it becomes permanent |
| Company website | `https://lifeclaw.agentese.ai/` |
| Company legal name | Confirm the submitting organization's verified legal name; the intended entity supplied by LifeClaw is **P0XEIDON LABS PTE. LTD.** |
| Authentication | OAuth 2.0 with Dynamic Client Registration (DCR) |
| Data handling | First-party LifeClaw API, with third-party providers for telephony, AI, search, hosting, and payments as described in the privacy policy. The connector handles account details, contacts, call details and results; it does not require health data or sponsored content. Verify answers against the live service. |

Use cases: call the account owner's verified number for an urgent decision; relay an approved message to a specified person; find and call a business for an inquiry or booking. Users need a LifeClaw account and points for paid actions. `call_me` requires a selected, voice-verified receiving number; personal calls require verified outbound Caller ID. Tools include both reads and actions that place real phone calls.

## Submission sequence

1. Add the URL as a custom connector in Claude and complete OAuth with a **dedicated reviewer account**. Test the tools that the portal discovers. The owner should not attest to testing any tool that has not actually been exercised.
2. In the portal, choose **MCP connector**, paste the server URL, and let it sync tools. Review any annotation or tool-scan warnings before submitting.
3. Fill the listing values above. Upload [`assets/logo.png`](../assets/logo.png). Use the Manta organization and its correct legal identity.
4. In **Test & launch**, enter reviewer credentials and setup instructions privately. The account should contain representative contacts and have enough points and verified phone setup to exercise calls. Do not put credentials in this repository or in a chat message.
5. Complete the portal's data-handling and policy questions using actual operating practices, then submit. Save the resulting review-status URL or screenshot for the team.

The server has no embedded MCP App UI, so carousel screenshots are not applicable. If the portal asks for screenshots despite that, check the scanned resources before adding any.

## Check before policy attestations

- The public [Privacy Policy](https://lifeclaw.agentese.ai/privacy) and [Terms](https://lifeclaw.agentese.ai/terms) currently describe the service as offered under the **Agentese Labs brand**. Confirm that wording is accurate for **P0XEIDON LABS PTE. LTD.** before representing the company's identity to a directory reviewer.
- A real Claude OAuth sign-in, consent, token exchange, and at least one authenticated tool call still need to be confirmed with the reviewer account. Public metadata and DCR checks alone do not establish the full flow.
- LifeClaw's current web sign-in uses Google or email/phone one-time codes. Arrange a reviewer sign-in that works independently for the reviewer before submitting; do not claim an unattended review account exists yet.
- Reviewer credentials, actual callable test numbers, and any required billing allowance must be prepared and shared only in the portal's private reviewer fields.

Official instructions: [Publish to the directory](https://claude.com/docs/directory/publish), [Submit a connector](https://claude.com/docs/connectors/building/submission), [Connector review criteria](https://claude.com/docs/connectors/building/review-criteria).
