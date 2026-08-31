---
name: update-github-info
description: Draft updates for Mona's GitHub Info site from official GitHub sources.
on:
  workflow_dispatch:
  schedule:
    - cron: '17 9 * * *'
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    draft: true
    fallback-as-issue: false
tools:
  edit:
  web-fetch:
network:
  allowed:
    - github.com
    - github.blog
    - awesome-copilot.github.com
---

# Update Mona's GitHub Info website

Read `notes/mona-notes.md` before making changes.

Use these sources:
- `notes/mona-notes.md`
- GitHub Blog: https://github.blog/latest/
- GitHub Changelog: https://github.blog/changelog/
- Awesome Copilot workflows: https://awesome-copilot.github.com/workflows/

Web fetch https://github.blog/latest/, web fetch https://github.blog/changelog/, and web fetch https://awesome-copilot.github.com/workflows/ to capture the latest official updates and relevant workflow examples.

Update `site/content/github-info.md` with concise, practical summaries of the most relevant GitHub news and product updates. When content comes from the GitHub Blog or GitHub Changelog, include the source context so Mona can review the provenance of the update.

Read external public guidance with web-fetch and read repository guidance or reference files with GitHub repository API tools instead of terminal, CLI, or sandboxed commands.

Open a pull request for Mona to review. Use `safe-outputs` with `create-pull-request` so the agent can propose changes without writing directly to `main`. Do not write directly to `main`; create a pull request that Mona can review and approve.
