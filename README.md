# Creator Finder skills marketplace

Public entrypoints for 16 Creator Finder workflows, plus setup and a read-only connection diagnostic. The proprietary research methods and outreach templates are retrieved from CF using your authenticated account. Your agent does the work.

## Codex desktop / CLI and local Work

Install the public skills from a terminal with Codex available:

```sh
codex plugin marketplace add CreatorFinder/skills
codex plugin add creator-finder@creatorfinder
```

For a local export, replace CreatorFinder/skills with the absolute extracted marketplace root. Open a new session after installing, then select Get Started from your client's skills menu or ask your agent to use it. Configure CF data MCP separately through your CF workspace Connections page using secure API-key settings. Local Work support depends on its runtime mode; credentials from a terminal are not automatically available to a separately launched GUI or cloud Work.

## ChatGPT web / cloud Work: preparation only

Workspace administrators can import this skills-only GitHub marketplace where their workspace supports plugin import. **CF's cloud data connection is not available yet:** current CF OAuth supports Claude's callback only. Importing skills does not connect data, grant account access or enable authenticated playbook retrieval. Do not advertise a working cloud integration until supported authentication and end-to-end access are implemented and verified. A public Plugins Directory listing would require separate OpenAI review.

## Claude Code: install locally

In Claude Code, run:

```text
/plugin marketplace add /absolute/path/to/extracted-marketplace
/plugin install creator-finder@creatorfinder
```

Choose user scope for availability across projects. Reload plugins or start a new session, then run /creator-finder:get-started.

## Claude Code: repository installation

In Claude Code, install from the official Creator Finder skills repository:

```text
/plugin marketplace add CreatorFinder/skills
/plugin install creator-finder@creatorfinder
```

This skills-only package contains no bundled MCP server, API host, credentials or private playbook content. Use your existing CF API/MCP connection from your workspace's Connections page. Installing skills does not enable account access. Native Claude Code browser sign-in is not required to install these skills or use an existing API-key connection.

## How it works

The selected skill calls get_creator_playbook for its instructions. Outreach uses list_outreach_templates and get_outreach_template. The backend checks account access and template visibility; unavailable access stops retrieval. These reads do not run hosted AI, charge data attempts or send messages. Your own agent then applies the instructions with your authorized tools.

API access and a current pilot grant are required. Optional browsing, verification and sending services are separate. Never put credentials or retrieved proprietary instructions into this public repository. Update through your client's plugin manager and start a fresh session afterward.
