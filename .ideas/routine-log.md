# Routine log

Plumbing test entries for the scheduled routine — proving clone/write/push works end to end.

## 2026-09-10 19:15 BST — plumbing test
- Clone: ok
- Write: ok
- Push: ok
- Model: claude-sonnet-5
- Notes: dry-run push succeeded before real push; no blockers, no permission prompts

## 2026-09-10 20:30 BST - egress probe

WebFetch tested against 10 domains. Result: **9/10 blocked.** Same pattern as the previous
routine — egress is not fixed.

| URL | Result | Error type |
|---|---|---|
| challonge.com/pricing | blocked | EGRESS_BLOCKED |
| g2.com | blocked | EGRESS_BLOCKED |
| news.ycombinator.com | blocked | EGRESS_BLOCKED |
| indiehackers.com | blocked | EGRESS_BLOCKED |
| github.com/trending | **ok** | - |
| en.wikipedia.org | blocked | EGRESS_BLOCKED |
| web.archive.org | blocked | generic fetch failure (not EGRESS_BLOCKED - different error path) |
| reddit.com | blocked | generic fetch failure (not EGRESS_BLOCKED - different error path) |
| stackoverflow.com | blocked | generic fetch failure (not EGRESS_BLOCKED - different error path) |
| crunchbase.com | blocked | EGRESS_BLOCKED |

- **WebSearch: works.** Returned real results + snippets (tested on league-software pricing).
- Only `github.com` was fetchable directly. Everything else — including sites with public
  pricing pages — is proxy-blocked.
- Task 2 report is downgraded to WebSearch-snippets-only, marked low-confidence, per the task
  rules.
