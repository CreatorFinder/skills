# Connection and access

## First conversation by client

- **Cowork:** upload the downloaded ZIP through Customize → Plugins, connect Creator Finder and approve access in the browser. Open a new conversation, select Creator Finder's Get Started skill and send **Start**.
- **Claude Code:** install `creator-finder@creatorfinder` from the CreatorFinder/skills marketplace. Once installation is complete, exit the old session and run `claude "Use Creator Finder's Get Started skill to walk me through setup and my first useful result."` in a terminal. This explicitly starts an interactive conversation with the installed skill; it does not install or authenticate the connector.
- **Codex / supported local Work:** install the skills, configure the separate CF data connection and open a new conversation. Where @-selection is supported, type **@**, select **Creator Finder**, choose **Get Started**, and send **Start**. If this client exposes a skills menu instead, select Get Started there or ask the agent to use it. Availability depends on the installed client's runtime and plugin support.
- **ChatGPT web / cloud Work:** importing skills is preparation only; authenticated CF work remains blocked as described below.

Nothing runs simply because the package was installed. If a skill is absent from the selection menu, confirm installation and new-session readiness before diagnosing account access. Describe the missing step, not an invented successful connection.

## Account access

The repository marketplace package for Codex, local Work and Claude Code contains skills only. Add the Creator Finder data MCP using the API-key connection instructions in your CF workspace Connections page, or use an existing working connection. The authenticated data endpoint is `/mcp/data` on your configured API host. Never copy credentials into chats, skills or repositories. Use the client's secure configuration.

Cowork's ZIP also includes the configured data connector and supports its browser sign-in flow. Sign in, review the application and explicitly approve access. Native Claude Code browser sign-in is separate optional work, not a prerequisite for installing skills or using an existing API-key connection.

For Codex, use a securely configured API-key environment-variable reference for the HTTP MCP connection. The key must be available to the actual runtime; a terminal variable does not automatically reach a separately launched GUI or cloud runtime. Local Work support depends on its runtime mode.

ChatGPT web / cloud Work skills import is preparation only. CF's cloud data connection is currently unavailable because its OAuth service permits Claude's callback only. Importing skills through a workspace administrator does not enable authenticated retrieval. Do not tell cloud users to attempt unsupported sign-in or assume local API-key settings apply there.

Account API access, an enabled data service and a current pilot grant are required. Skill installation grants none of these. `get_creator_playbook` returns authenticated research instructions; `list_outreach_templates` and `get_outreach_template` apply account and template visibility checks. If these tools are missing, the backend may not yet include playbook retrieval. Report setup incomplete; do not substitute the legacy hosted workflow.

Check Creator Finder uses one `list_data_usage({})` call without a provider request or data attempt. Success verifies connection and allowance, not every workflow or external tool. Missing or invalid usage means unknown access.

REST clients can use `GET /v1/data/playbooks`, `GET /v1/data/playbooks/{slug}`, `GET /v1/data/outreach-templates` and `GET /v1/data/outreach-templates/{slug}` with securely configured API-key authorization. Do not cache responses in public storage. Manage API keys in your workspace; manage browser-approved connections through Connected applications.
