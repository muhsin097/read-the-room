---
name: update-github-info
model: gpt-5-mini
description: Draft website updates for Mona's GitHub Info site from official GitHub sources.
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

Web fetch https://awesome-copilot.github.com/workflows/ and use it as an additional source when preparing updates for `site/content/github-info.md`.

Update `site/content/github-info.md` with concise, practical updates for readers and include source context when content comes from the GitHub Blog, GitHub Changelog, or Awesome Copilot workflows.

Open a pull request for Mona to review using `safe-outputs` with `create-pull-request`. Do not write directly to `main`.

Read external public guidance with web-fetch, and read repository guidance or reference files with GitHub repository API tools instead of terminal, CLI, or sandboxed commands.

Check that the YAML frontmatter and workflow configuration are valid before finishing. The workflow should run on daily or on demand with `workflow_dispatch`.
