---
name: watch-pr
description: Watch the current PR for CI and reviews
---

# Watch PR

Watch the PR for any pending copilot or user reviews, and the CI (Github actions and checks) status. When CI is a complete success and all pending and requested reviews are complete with no comments, rebase and merge the PR. If and when any new reviews or comments arrive, address them: if a `resolve-reviews` skill is available, use it; otherwise read each review and comment, make the needed changes, push them, and reply to and resolve each thread. If CI or any checks fail, fix them.

## Status and merging

Judge every PR with `pr-ready` in this skill's directory, not a hand-written loop:

- `pr-ready <repo> <n>` prints one status line with a verdict. READY means the head commit was pushed over a minute ago, checks are green (a review bot's queued or in-progress check counts as pending), Copilot has reviewed the head commit when the branch ruleset requires it, and there's no open thread, new comment or pending request. BLOCKED lists what to address.
- `pr-ready <repo> <n> --merge` rebase-merges a READY PR, pinned to the head commit it checked, and prints `gh`'s output and a hint on failure.
- Exit 2 is WAITING: poll on it in a background loop with a deadline, because a bot that never reviews the head keeps a PR waiting. Exit 0 is READY or MERGED, 1 is BLOCKED, 3 is an error.
