---
name: find-verify-email
description: Find source-backed business contacts and verify candidates using the user’s connected verifier.
---

# Find & Verify Business Email

This public entrypoint loads the current Creator Finder playbook for `find-verify-email`. The detailed instructions are available through an authenticated CF connection; they are not bundled here.

## A useful first result

Help the user find contact evidence and check deliverability. Honor their stated goal, requested scope and inputs; ask one plain question at a time only for missing essentials, starting with the creator or contact source. Only when scope is unspecified, if they say “Start” without detail, offer a sourced address and its actual verification status as a small first win. Skip or restart the conversation when asked without resetting usage. Explain the relevant criteria and why they serve the user's goal; do not impose universal thresholds.

After authenticated retrieval below, adapt the workflow to available evidence: supplied contact evidence; available browsing; separate verifier. Optional tools are not universal setup requirements; explain when a narrower result is useful. Remember: finding an address alone does not verify deliverability. Never invent access, measurements or missing evidence. Deliver a sourced address and its actual verification status in chat with source links or supplied-file references, applied criteria and uncertainty, then recommend one next step such as verify with a connected verifier if available and authorized. Claim an optional file exists only after creating and reading it back. Research, contact verification and sending are separate actions; sending needs an available tool and explicit authorization. Do not assume cross-session memory.

## Before acquiring data

State a finite acquisition plan and stopping point within the user's authorized task; obtain authorization if it does not cover that plan. Inspect actual tool schemas and current `list_data_usage` before paid CF requests. A valid nonnegative integer `maxAttempts` is a pilot limit, with remaining attempts `max(0, maxAttempts - reservedAttempts)` when both are valid nonnegative integers. Only explicit `maxAttempts: null` means no pilot cap; still respect a finite task ceiling and provider limits. Missing or invalid usage means unknown access: halt paid CF acquisition. Allowance is not a price or guaranteed result count.

Save the unique `idempotencyKey` and exact input before each CF data request, and retain the first successful response with receipt/source. Identical replay returns a receipt, not the original data; changed input with that key conflicts. Only `receipt.state: completed` with data supplies new evidence. Failed, pending and unknown attempts remain consumed: stop the affected path instead of retrying with a new key or switching paid tools. Pagination stays within the agreed ceiling. Use supplied evidence where sufficient; it never substitutes for required private playbook access.

## Run this skill

1. Inspect the connected Creator Finder data MCP tools. Use the exposed namespace for `get_creator_playbook` with `{"slug":"find-verify-email"}`. Use the user's existing CF API/MCP connection; installing this file does not connect an account or grant access.
2. If the tool is missing or access is denied, explain that the CF connection or account access needs setup. Stop this CF workflow. Do not reconstruct its private instructions or silently substitute the legacy hosted research endpoint. Never ask for passwords, tokens or API keys in chat or save them into this skill.
3. Read the returned playbook instructions and required tools before doing the task. Fetch it when starting the workflow so updates and access checks apply. Do not save the retrieved content into a public repository or redistribute it.
4. Carry out the retrieved workflow in the customer's agent using the user's inputs and authorized tools. Retrieving a playbook does not authorize paid data requests or external actions. Ask for missing inputs and use the user's task budget. Do not send outreach without explicit authorization.

REST integrations can retrieve the same instructions using `GET /v1/data/playbooks/find-verify-email` on their configured CF API host with credentials managed securely by their client. This public skill contains no API host or credentials. Unavailable retrieval means the CF workflow is unavailable, not that access succeeded.
