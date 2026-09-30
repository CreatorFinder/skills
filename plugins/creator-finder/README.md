# Creator Finder toolkit

Includes 16 public skill entrypoints, Get Started and Check Creator Finder. Proprietary playbooks and outreach templates stay in CF and require an authenticated, eligible account to retrieve. Your agent performs the work.

This skills-only package includes no MCP server configuration. Use your existing CF API/MCP connection, configured separately through your workspace Connections page.

Select Get Started from your client’s skills menu or ask your agent to use it. In Claude Code you can also run /creator-finder:get-started. The installed skills request the current instructions through get_creator_playbook; they do not contain the proprietary methods. Outreach instructions are retrieved through list_outreach_templates and get_outreach_template. Inspect exposed tool schemas and stop if retrieval is unavailable. Do not substitute legacy hosted generation.

Claude Code browser sign-in is optional future work; existing API-key MCP connections can be used. Never paste credentials in chat, repository files or skill files. Account API access and a current pilot grant are required. Installation does not grant or verify access.

Select Check Creator Finder for a read-only usage check; Claude Code also supports /creator-finder:check-creator-finder. Playbook/template retrieval does not run AI or acquire provider data. Data acquisition and optional external tools have separate usage; agree a bounded task before using them. Sending requires explicit authorization.

skill-hashes.json records the included public entrypoint bytes. Do not redistribute authenticated playbook responses.
