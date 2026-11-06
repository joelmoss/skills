---
name: watch-pr
description: Watch the current PR for CI and reviews
---

# Watch PR

Watch the PR for any pending copilot or user reviews, and the CI (Github actions and checks) status. When CI is a complete success and all pending and requested reviews are complete with no comments, rebase and merge the PR. If and when any new reviews or comments arrive, address them: if a `resolve-reviews` skill is available, use it; otherwise read each review and comment, make the needed changes, push them, and reply to and resolve each thread. If CI or any checks fail, fix them.
