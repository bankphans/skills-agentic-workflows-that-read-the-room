---
name: update-github-info
description: Draft website updates for Mona's GitHub Info site from official GitHub sources.
on:
  workflow_dispatch:
  schedule:
    - cron: "17 9 * * *"
permissions:
  contents: read
  copilot-requests: write
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    draft: true
    fallback-as-issue: false
    allowed-files:
      - site/content/github-info.md
tools:
  edit:
  web-fetch:
network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com
engine:
  id: copilot
  copilot-sdk: true
---

# Update Mona's GitHub Info website

Read `notes/mona-notes.md` before making changes.

Use these official sources:

- GitHub Blog: https://github.blog/latest/
- GitHub Changelog: https://github.blog/changelog/
- Awesome Copilot workflows: https://awesome-copilot.github.com/workflows/

Use `web-fetch` to read all three sources. Identify practical updates that help
developers learn GitHub faster, and keep summaries concise. Update only
`site/content/github-info.md`. Mention the source whenever an update comes
from the GitHub Blog, GitHub Changelog, or Awesome Copilot workflows.

Open a pull request for Mona to review with the proposed update. Use a pull
request title that mentions Mona or GitHub Info. Do not write directly to
`main`; use the configured `safe-outputs` `create-pull-request` operation.
If there are no useful updates, make no file changes and call `noop` with a
brief reason.
