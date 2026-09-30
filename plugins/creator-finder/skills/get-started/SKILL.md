---
name: get-started
description: Connect Creator Finder's public skill entrypoints to authenticated playbooks and choose a first task in your own agent.
---

# Get Started with Creator Finder

The installed skills are public entrypoints. Detailed CF research instructions, rubrics and outreach templates are retrieved from your authenticated CF connection. Your agent performs the work; CF does not run hosted reasoning through these tools.

1. Read [connection setup](references/connection.md). Inspect your connected CF data MCP tools. Installation does not grant account access. Never collect credentials in chat or write them into plugin files.
2. If the user wants to check the connection, use `check-creator-finder` for one read-only usage call. Do not acquire creator data as a setup test.
3. For research, select an entrypoint from [the workflow directory](references/workflows.md), then retrieve the current instructions using `get_creator_playbook` with its slug. `list_creator_playbooks` lists the available research workflows. Read the returned instructions and dependencies before execution. If retrieval is missing or denied, stop the CF workflow and explain the setup gap; do not recreate its private method.
4. For outreach drafting, call `list_outreach_templates`, let the user select the appropriate template, and call `get_outreach_template` using its exposed input schema. Read its returned instructions and required inputs. Fill placeholders only with the user's actual sender context and sourced research; ask for missing inputs. Do not call legacy `generate_outreach`, launch a hosted job or send messages.
5. Follow the retrieved instructions in the user's agent within the user's authorized task and tool budget. Optional services require separate connections. Read [data mechanics](references/data-contract.md) before provider calls. Retrieval does not authorize paid acquisition or external actions. Sending requires explicit user authorization.

Retrieve instructions when starting a workflow so updates and account checks apply. Do not commit, publish or redistribute the responses. Missing access is not permission to bypass CF's retrieval or use a cached copy.
