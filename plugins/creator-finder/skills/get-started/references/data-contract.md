# Data contract quick reference

The camelCase `idempotencyKey`, receipt and pilot-attempt rules below are the PROVIDER data contract only. Offer-owner tools follow the separate ledger described in the offer-owner paragraph further down.

Use the configured `/mcp/data` connector. Inspect its exposed tool names and input schemas rather than inventing parameters. Current tools include `list_data_usage`, `seed_creators`, `get_creator_profile`, and operation-specific data tools. MCP operation parameters are flat alongside `idempotencyKey`; REST `/v1/data/execute` wraps them as `operation`, `idempotencyKey`, and `params`.

| REST endpoint | Purpose |
| --- | --- |
| GET /v1/data/usage | No parameters; allowance and up to 50 request receipts |
| POST /v1/data/seeds | Instagram candidates; platform, idempotencyKey, source, query or hashtag, optional cursor |
| POST /v1/data/profile | Instagram profile; platform, idempotencyKey, handle |
| POST /v1/data/execute | Other supported data operations; operation, idempotencyKey, params |

The `/api/v1/data` alias has the same contract. The legacy `/mcp` and legacy OpenAPI document describe another service, not this data connector.

Data covers Instagram profiles, keyword/hashtag seeds and content; YouTube and TikTok search, profiles and content; public Meta Ad Library searches and ad details. Post details, transcripts and bounded comment pages depend on the specific tool and provider. Missing fields and captions remain unknown. These tools do not deliver hosted reasoning, guaranteed contact details or outreach sends; provider transcription may use AI.

Before paid acquisition, explain the sources, relevant selection criteria and finite request ceiling within the user's authorized task. Check current usage; if allowance is unknown or invalid, stop paid CF acquisition and resolve access. Existing supplied evidence may still support an honestly scoped result after authenticated playbook retrieval.

Offer-owner database tools are a separate ledger on the same connection. Explicit founder accounts report `access=true`, `source=founder`, `usage.unlimited=true`, null period/day limits and remaining values, null `available_now` and null `access_until`; report unlimited founder access and actual delivered totals rather than a remaining balance, expiry or purchase requirement. Their usage is counted (`charged` and `charge_if_fulfilled`) without consuming a finite quota or adding a fee; max 50 per batch and one active pull remain. The finite allowance instructions that follow apply to finite accounts. They use snake_case `idempotency_key` and charge only people actually delivered, against a period and UTC-day delivered-person allowance read from `get_account`; they never consume provider attempts, and provider attempts never reduce that allowance. `start_offer_owner_setup`, `list_offer_owner_categories`, `preview_offer_owner_pull`, `get_account` and `get_offer_owner_deliveries` are free; `pull_offer_owners` spends allowance and runs only on the user's explicit request for a stated quantity (default 10, maximum 50) and filters. An identical retry with the same `idempotency_key` replays free; do not use a new key to repeat a completed pull. Previews show the maximum allowance cost, not inventory. Do not translate one ledger into the other, or infer inventory from allowance.

A nonnegative integer `maxAttempts` is a finite pilot limit with no automatic monthly reset. Remaining attempts are `max(0, maxAttempts - reservedAttempts)` when both values are valid nonnegative integers. Only explicit `maxAttempts: null` means no pilot cap. Attempts are still counted; respect provider limits and a finite user-approved task ceiling. Missing or invalid usage means unknown access. Allowance is not a credit price or a promised lead count.

Save each unique `idempotencyKey` and exact input before a data call. Keep the first successful data response with its receipt and source. Identical key/input replay returns only a receipt, not data again; the same key with changed input conflicts. Only `receipt.state: completed` with data supplies new evidence. Failed, pending and unknown attempts remain consumed: stop the affected path instead of automatically switching tools or retrying with a new key. Paginate only within the agreed ceiling.
