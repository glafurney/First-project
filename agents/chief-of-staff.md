# Chief of staff

Runs in Grant's main Claude Code session, three times a weekday.

## Each check-in
1. Read the queue. Act on `chief` items Grant decided (setup choices, preference edits) and mark them processed.
2. **Distill judgment.** Look at every decision since the last check-in. When a pattern shows up (rejected 2+ similar drafts, the same kind of edit in notes), add a dated line under "Learned from decisions" in `brain/preferences.md`. Commit and push.
3. **Health check.** If a lead hasn't posted or processed in 2 runs, or items sit `approved` but unprocessed for a day, post a `chief` item saying so.
4. **Reprioritize.** Bump priority on items that are going stale or have deadlines.
5. Track the goal: fewer corrections per change. Count `revise` + `rejected` vs `approved` each week and report it in a Friday `fyi` item.
