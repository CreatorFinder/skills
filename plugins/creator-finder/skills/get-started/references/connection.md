# Connection and access

Claude Code's marketplace package contains skills only. Add the Creator Finder data MCP using the API-key connection instructions in your CF workspace Connections page, or use an existing working connection. The authenticated data endpoint is `/mcp/data` on your configured API host. Never copy credentials into chats, skills or repositories. Use the client's secure configuration.

Cowork's ZIP also includes the configured data connector and supports its browser sign-in flow. Sign in, review the application and explicitly approve access. Native Claude Code browser sign-in is separate optional work, not a prerequisite for installing skills or using an existing API-key connection.

Account API access, an enabled data service and a current pilot grant are required. Skill installation grants none of these. `get_creator_playbook` returns authenticated research instructions; `list_outreach_templates` and `get_outreach_template` apply account and template visibility checks. If these tools are missing, the backend may not yet include playbook retrieval. Report setup incomplete; do not substitute the legacy hosted workflow.

Check Creator Finder uses one `list_data_usage({})` call without a provider request or data attempt. Success verifies connection and allowance, not every workflow or external tool. Missing or invalid usage means unknown access.

REST clients can use `GET /v1/data/playbooks`, `GET /v1/data/playbooks/{slug}`, `GET /v1/data/outreach-templates` and `GET /v1/data/outreach-templates/{slug}` with securely configured API-key authorization. Do not cache responses in public storage. Manage API keys in your workspace; manage browser-approved connections through Connected applications.
