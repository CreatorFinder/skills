# Creator Finder toolkit

Includes 16 public skill entrypoints, Get Started and Check Creator Finder. Proprietary playbooks and outreach templates stay in CF and require an authenticated, eligible account to retrieve. Your agent performs the work.

This skills-only package includes no MCP server configuration. Use your existing CF API/MCP connection, configured separately through your workspace Connections page.

Open a new conversation, select Creator Finder’s Get Started skill from your client’s skills menu, and send **Start**. Installation alone does not launch a conversation; this package has no hooks or persistent onboarding state. In Claude Code you can also run /creator-finder:get-started. The installed skills request the current instructions through get_creator_playbook; they do not contain the proprietary methods. Outreach instructions are retrieved through list_outreach_templates and get_outreach_template. Inspect exposed tool schemas and stop if retrieval is unavailable. Do not substitute legacy hosted generation.

The same connection can also expose the offer-owner database tools (start_offer_owner_setup, list_offer_owner_categories, preview_offer_owner_pull, pull_offer_owners, get_offer_owner_deliveries, get_account) when offer-owner permission was approved and the account has database access. Get Started guides setup, a free preview, an explicit pull and free history without needing a private playbook. That ledger charges delivered people and uses snake_case idempotency_key; provider data uses camelCase idempotencyKey and counts attempts. To add offer-owner permission to an existing connection, remove it under Connected applications, reconnect and approve.

Claude Code browser sign-in is optional future work; existing API-key MCP connections can be used. Never paste credentials in chat, repository files or skill files. Account API access and a current pilot grant are required. Installation does not grant or verify access.

Select Check Creator Finder for a read-only usage check; Claude Code also supports /creator-finder:check-creator-finder. Playbook/template retrieval does not run AI or acquire provider data. Data acquisition and optional external tools have separate usage; agree a bounded task before using them. Sending requires explicit authorization.

skill-hashes.json records the included public entrypoint bytes. Do not redistribute authenticated playbook responses.
