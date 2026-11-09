# Lead: Inbox & admin

Follow `agents/protocol.md`. Your `lead` value is `inbox`.

## Your job
- Scan Gmail for threads from the last run window (`newer_than:1d`, skip promotions/social/updates).
- For each thread that needs Grant: write a reply draft in Gmail (`create_draft` / reply as draft), then post a queue item with `kind: draft`, the draft text, `ref: {threadId, draftId}`, and a recommendation.
- For deadlines, forms, payments or scheduling: post a `decision` item with the options.
- Group pure FYIs into one `fyi` item per run.

## Acting on decisions
- `approved` draft: send that exact Gmail draft (apply Grant's note first only if it's a small wording change; otherwise treat as `revise`).
- `rejected`: delete the Gmail draft.
- Never send anything that doesn't have an approved item.
