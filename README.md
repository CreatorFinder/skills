# Creator Finder skills marketplace

Public entrypoints for 16 Creator Finder workflows, plus setup and a read-only connection diagnostic. The proprietary research methods and outreach templates are retrieved from CF using your authenticated account. Your agent does the work.

## Codex desktop / CLI and local Work

Install the public skills from a terminal with Codex available:

```sh
codex plugin marketplace add CreatorFinder/skills
codex plugin add creator-finder@creatorfinder
```

For a local export, replace CreatorFinder/skills with the absolute extracted marketplace root. Open a new session after installing. Where supported, type @, select Creator Finder, choose Get Started, and send **Start**. If your client uses a skills menu, select Get Started there or ask the agent to use it, then send **Start**. Configure CF data MCP separately through your CF workspace Connections page using secure API-key settings. Local Work support depends on its runtime mode; credentials from a terminal are not automatically available to a separately launched GUI or cloud Work.

## ChatGPT web / cloud Work: preparation only

Workspace administrators can import this skills-only GitHub marketplace where their workspace supports plugin import. **CF's cloud data connection is not available yet:** current CF OAuth supports Claude's callback only. Importing skills does not connect data, grant account access or enable authenticated playbook retrieval. Do not advertise a working cloud integration until supported authentication and end-to-end access are implemented and verified. A public Plugins Directory listing would require separate OpenAI review.

## Claude Code: install locally

In Claude Code, run:

```text
/plugin marketplace add /absolute/path/to/extracted-marketplace
/plugin install creator-finder@creatorfinder
```

Choose user scope for availability across projects. Then follow the explicit first-conversation launch below.

## Claude Code: repository installation

In Claude Code, install from the official Creator Finder skills repository:

```text
/plugin marketplace add CreatorFinder/skills
/plugin install creator-finder@creatorfinder
```

This skills-only package contains no bundled MCP server, API host, credentials or private playbook content. Use your existing CF API/MCP connection from your workspace's Connections page. Installing skills does not enable account access. Native Claude Code browser sign-in is not required to install these skills or use an existing API-key connection.

## Claude Code: start your first conversation

After installation finishes, exit the old Claude Code session. In a terminal, launch a new interactive session with:

```sh
claude "Use Creator Finder's Get Started skill to walk me through setup and my first useful result."
```

With an installed plugin in a ready session, /creator-finder:get-started is also available. Installing the package alone does not start a conversation. No SessionStart hook or persistent onboarding state is included; hooks remain a follow-up until client isolation can be validated.

## Cowork

Download the Cowork ZIP from your CF workspace. Upload it through Customize → Plugins, connect Creator Finder and approve account access. Open a new conversation, select Creator Finder's Get Started skill, and send **Start**. This repository marketplace is the skills-only distribution; Cowork's ZIP additionally contains the data connector.

## How it works

The selected skill calls get_creator_playbook for its instructions. Outreach uses list_outreach_templates and get_outreach_template. The backend checks account access and template visibility; unavailable access stops retrieval. These reads do not run hosted AI, charge data attempts or send messages. Your own agent then applies the instructions with your authorized tools.

API access and a current pilot grant are required. Optional browsing, verification and sending services are separate. Never put credentials or retrieved proprietary instructions into this public repository. Update through your client's plugin manager and start a fresh session afterward.
