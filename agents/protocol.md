# Queue protocol (all agents)

**Queue URL:** https://claude.ai/artifact/YJhmH2EtyXmB1MWPFKy7hm
**Brain:** `brain/preferences.md` in `glafurney/first-project` (branch `claude/affectionate-galileo-0ugr76`). Read it first, every run.

Read and write the queue with the `ArtifactData` tool (load it with ToolSearch), collection `queue`.

## Item fields
| field | values |
|---|---|
| `title` | One line, what Grant decides. |
| `lead` | `chief`, `inbox`, `research`, `ideas` |
| `kind` | `decision`, `review`, `draft`, `idea`, `fyi` |
| `priority` | 1 urgent today, 2 this week, 3 whenever |
| `summary` | 1-3 sentences of context. |
| `recommendation` | What you'd do. Always include one. |
| `draft` | Optional full text (email, note, message). |
| `links` | Optional `[{label, url}]`, https only. |
| `ref` | Optional ids you need later (Gmail thread id, Notion page id). |
| `status` | `open` when you create it. Grant sets `approved`, `rejected`, `snoozed`, or `revise`. |
| `note` | Grant's note, if any. |
| `processed` | You set `true` after acting on Grant's decision. |
| `createdAt` | ISO timestamp. |

Doc id: `<lead>-<yyyymmdd>-<short-slug>`.

## Every run
1. Read `brain/preferences.md`.
2. Query your items where `processed == false` and status is `approved`, `rejected` or `revise`. Act on each:
   - `approved`: do exactly what the item said, using the note if there is one.
   - `rejected`: undo any prep (e.g. delete the Gmail draft). Do nothing else.
   - `revise`: redo it using the note, post a new `open` item, and mark the old one processed.
   Then set `processed: true` (pin `if_version`).
3. Do your lead's work and post new `open` items. Avoid duplicates: check open items first.
4. Cap: at most 8 new items per run. Bundle the rest.
