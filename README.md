# Creator Finder skills marketplace

Public entrypoints for 16 Creator Finder workflows, plus setup and a read-only connection diagnostic. The proprietary research methods and outreach templates are retrieved from CF using your authenticated account. Your agent does the work.

## Install locally

In Claude Code, run:

```text
/plugin marketplace add /absolute/path/to/extracted-marketplace
/plugin install creator-finder@creatorfinder
```

Choose user scope for availability across projects. Reload plugins or start a new session, then run /creator-finder:get-started.

## Repository installation

In Claude Code, install from the official Creator Finder skills repository:

```text
/plugin marketplace add jaybeckham/creatorfinder-plugins
/plugin install creator-finder@creatorfinder
```

This skills-only package contains no bundled MCP server, API host, credentials or private playbook content. Use your existing CF API/MCP connection from your workspace's Connections page. Installing skills does not enable account access. Native Claude Code browser sign-in is not required to install these skills or use an existing API-key connection.

## How it works

The selected skill calls get_creator_playbook for its instructions. Outreach uses list_outreach_templates and get_outreach_template. The backend checks account access and template visibility; unavailable access stops retrieval. These reads do not run hosted AI, charge data attempts or send messages. Your own agent then applies the instructions with your authorized tools.

API access and a current pilot grant are required. Optional browsing, verification and sending services are separate. Never put credentials or retrieved proprietary instructions into this public repository. Update through Claude Code's plugin manager and reload afterward.
