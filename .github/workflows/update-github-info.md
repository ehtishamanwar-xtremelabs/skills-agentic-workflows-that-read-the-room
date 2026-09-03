---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:

permissions:
  contents: read
  pull-requests: read

tools:
  github:
    toolsets: [repos]
  web-fetch:
  edit:

network:
  allowed:
    - github.blog
    - github.com

safe-outputs:
  create-pull-request:
    title-prefix: "[github-info] "
    draft: true
---

# Update GitHub Info

Keep the GitHub Info website current with useful, concise updates for developers.

## Instructions

1. Read `notes/mona-notes.md` using the GitHub repository API tools. Do not use terminal, CLI, or sandboxed shell commands to read repository guidance or reference files.
2. Use web-fetch to read `https://github.blog/latest/`.
3. Use web-fetch to read `https://github.blog/changelog/`.
4. Select relevant updates that help developers learn GitHub faster. Keep summaries short and practical, and mention the source whenever an update comes from the GitHub Blog or GitHub Changelog.
5. Use the edit tool to update `site/content/github-info.md` with the selected updates. Preserve the existing file's structure and make only focused content changes.
6. Use the `create-pull-request` safe output to open a pull request containing the changes for Mona to review. Do not write directly to the default branch.
