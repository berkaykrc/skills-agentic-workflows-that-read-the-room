---
name: update-github-info
description: Draft website updates for Mona's GitHub Info site from official GitHub sources.
model: gpt-5-mini
on:
  workflow_dispatch:
  schedule:
    - cron: "17 9 * * *"
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
    - github
    - awesome-copilot.github.com
---

# Update Mona's GitHub Info website

Read `notes/mona-notes.md` before making changes.

Use these sources:

- `notes/mona-notes.md`
- GitHub Blog: https://github.blog/latest/
- GitHub Changelog: https://github.blog/changelog/
- Awesome Copilot workflows: https://awesome-copilot.github.com/workflows/

Web fetch https://awesome-copilot.github.com/workflows/ when gathering the
workflow sources.

Update `site/content/github-info.md` with concise, practical updates for
readers. Include source context when content comes from the GitHub Blog or
GitHub Changelog, and preserve the existing structure and style of the file.

Open a pull request for Mona to review. Use a pull request title that mentions
Mona or GitHub Info. Do not write directly to `main`; rely on `safe-outputs`
with `create-pull-request`.
