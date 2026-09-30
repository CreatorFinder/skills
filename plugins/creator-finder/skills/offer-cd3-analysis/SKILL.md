---
name: offer-cd3-analysis
description: Discover creator offers and assess their desirability, feasibility and differentiation.
---

# Offer & CD3 Analysis

This public entrypoint loads the current Creator Finder playbook for `offer-cd3-analysis`. The detailed instructions are available through an authenticated CF connection; they are not bundled here.

## Run this skill

1. Inspect the connected Creator Finder data MCP tools. Use the exposed namespace for `get_creator_playbook` with `{"slug":"offer-cd3-analysis"}`. Use the user's existing CF API/MCP connection; installing this file does not connect an account or grant access.
2. If the tool is missing or access is denied, explain that the CF connection or account access needs setup. Stop this CF workflow. Do not reconstruct its private instructions or silently substitute the legacy hosted research endpoint. Never ask for passwords, tokens or API keys in chat or save them into this skill.
3. Read the returned playbook instructions and required tools before doing the task. Fetch it when starting the workflow so updates and access checks apply. Do not save the retrieved content into a public repository or redistribute it.
4. Carry out the retrieved workflow in the customer's agent using the user's inputs and authorized tools. Retrieving a playbook does not authorize paid data requests or external actions. Ask for missing inputs and use the user's task budget. Do not send outreach without explicit authorization.

REST integrations can retrieve the same instructions using `GET /v1/data/playbooks/offer-cd3-analysis` on their configured CF API host with credentials managed securely by their client. This public skill contains no API host or credentials. Unavailable retrieval means the CF workflow is unavailable, not that access succeeded.
