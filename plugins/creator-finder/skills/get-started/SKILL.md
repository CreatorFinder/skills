---
name: get-started
description: Welcome Creator Finder users, connect their account and guide a small first creator discovery, research or outreach-drafting task in their own agent.
---

# Get Started with Creator Finder

Help the user get one useful result in this conversation. Creator Finder helps find potential creator partners, understand a creator from evidence, and prepare personal outreach. Their agent performs the work using authenticated CF playbooks and available sources.

## Welcome and choose a first win

When the user says “Start” or has no task yet, briefly explain those three outcomes and ask one plain question: “Are you looking for new creators, researching someone you know, or preparing outreach?” Offer examples if they are unsure. Ask the next useful question only when needed; do not present a questionnaire. If they already named a task, creator or goal, use it immediately without making them repeat it. Honor skip, change direction and restart requests; restarting the conversation does not reset usage or permission.

Suggest a small first result that fits their goal: a short candidate list, a sourced snapshot of one creator, or a draft grounded in supplied research. Explain why the proposed criteria matter for their goal before acquiring data. Ask only for missing details that change the result; let the user adjust criteria. Examples are starting points, not fixed qualification thresholds.

## Make the connection understandable

Inspect actual connected tools, then read [connection setup](references/connection.md) for the user's client. Installation and account access are separate. For an explicit welcome or setup request, if the CF usage tool is available, use `check-creator-finder` once for one read-only usage call; no provider request is a setup test. If the tool is absent, guide connection setup. A successful diagnostic confirms only the connection and reported allowance, not every workflow or optional tool. For a direct task using supplied evidence, omit an unnecessary diagnostic unless paid acquisition is needed; authenticated playbook retrieval is still required. Say what is ready and the next setup step in plain language. Never collect credentials in chat or plugin files.

Use [the outcome directory](references/workflows.md) to choose an available skill. Retrieve current research instructions with `get_creator_playbook` and the selected slug; `list_creator_playbooks` can show available workflows. Read the returned instructions and dependencies. Missing or denied retrieval stops that CF workflow: explain how to restore access; do not recreate private methods, use cached instructions to bypass access, or substitute legacy hosted research.

For outreach drafting, use `list_outreach_templates` and `get_outreach_template` with their exposed schemas. Fill placeholders only from actual sender context and sourced research; ask for missing essentials. Do not call legacy `generate_outreach` or send messages. Retrieval alone authorizes neither paid acquisition nor external actions.

## Work toward the result

Follow the retrieved workflow and [data mechanics](references/data-contract.md) before provider calls. State a finite acquisition plan within the user's authorized task and allowance, including a stopping point. If authorization does not cover the plan, ask first. Unknown or invalid allowance stops paid CF acquisition. Choose useful sources and tools for this task: CF data where supported, supplied evidence, available browsing or separately authorized tools. Optional integrations are not universal prerequisites. Explain any narrower result possible with the available evidence, separating research, contact verification and sending.

Deliver the useful result directly in chat with source links or supplied-file references, the criteria applied, and gaps or uncertainty. Missing evidence is unknown, not proof of absence; never invent metrics, contacts or citations. Explain what the result helps the user decide and recommend one relevant next action, without beginning new paid work or sending anything without authorization. Offer a file only when useful; claim it is saved or downloadable only after creating it and reading it back successfully.

There is no automatic welcome launch or persistent onboarding state in this package. Use context the user supplied in this conversation; do not claim to remember another client/session or treat missing history as a first-ever installation. Fetch private instructions anew when starting a workflow and never publish or redistribute them.
