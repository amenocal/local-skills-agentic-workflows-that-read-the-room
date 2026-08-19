---
name: update-github-info
description: Refresh site/content/github-info.md from the GitHub Blog and Changelog, then open a pull request for Mona to review.
on:
  schedule:
    - cron: "0 13 * * *"
  workflow_dispatch:
permissions:
  contents: read
tools:
  edit:
  web-fetch:
  github:
    toolsets: [repos]
network:
  allowed:
    - github.blog
    - github.com
safe-outputs:
  create-pull-request:
    allowed-files:
      - site/content/github-info.md
---

# Update GitHub Info

## Task

Refresh the GitHub Info website content with the latest official GitHub updates, then open a pull request for Mona to review.

1. Read `notes/mona-notes.md` using the GitHub repository API tools (not terminal, CLI, or sandboxed commands) to understand Mona's editorial guidance.
2. Web-fetch <https://github.blog/latest/> and <https://github.blog/changelog/> to gather the most recent GitHub Blog posts and Changelog entries.
3. Read the current `site/content/github-info.md` using the GitHub repository API tools to see what already exists.
4. Update `site/content/github-info.md` with concise, practical summaries of relevant new stories. Keep entries short, cite the source (GitHub Blog or Changelog), and follow Mona's notes.

## Safe Outputs

- Use the `create-pull-request` safe output to propose the edits to `site/content/github-info.md` so Mona can review before anything reaches `main`. Do not write directly to `main`.
- Use `noop` with a short explanation when there are no meaningful new updates to add.
