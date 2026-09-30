# Data contract quick reference

Use the configured `/mcp/data` connector. Inspect its exposed tool names and input schemas rather than inventing parameters. Current tools include `list_data_usage`, `seed_creators`, `get_creator_profile`, and operation-specific data tools. MCP operation parameters are flat alongside `idempotencyKey`; REST `/v1/data/execute` wraps them as `operation`, `idempotencyKey`, and `params`.

| REST endpoint | Purpose |
| --- | --- |
| GET /v1/data/usage | No parameters; allowance and up to 50 request receipts |
| POST /v1/data/seeds | Instagram candidates; platform, idempotencyKey, source, query or hashtag, optional cursor |
| POST /v1/data/profile | Instagram profile; platform, idempotencyKey, handle |
| POST /v1/data/execute | Other supported data operations; operation, idempotencyKey, params |

The `/api/v1/data` alias has the same contract. The legacy `/mcp` and legacy OpenAPI document describe another service, not this data connector.

Data covers Instagram profiles, keyword/hashtag seeds and content; YouTube and TikTok search, profiles and content; public Meta Ad Library searches and ad details. Post details, transcripts and bounded comment pages depend on the specific tool and provider. Missing fields and captions remain unknown. These tools do not deliver hosted reasoning, guaranteed contact details or outreach sends; provider transcription may use AI.

A nonnegative integer `maxAttempts` is a finite pilot limit with no automatic monthly reset. Remaining attempts are `max(0, maxAttempts - reservedAttempts)` when both values are valid nonnegative integers. Only explicit `maxAttempts: null` means no pilot cap. Attempts are still counted; respect provider limits and a finite user-approved task ceiling. Missing or invalid usage means unknown access. Allowance is not a credit price or a promised lead count.

Save each unique `idempotencyKey` and exact input before a data call. Keep the first successful data response with its receipt and source. Identical key/input replay returns only a receipt, not data again; the same key with changed input conflicts. Only `receipt.state: completed` with data supplies new evidence. Failed, pending and unknown attempts remain consumed: stop the affected path instead of automatically switching tools or retrying with a new key. Paginate only within the agreed ceiling.
