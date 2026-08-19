---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
  pull-requests: read
engine: copilot
tools:
  edit:
  web-fetch:
  github:
    toolsets: [repos]
network:
  allowed:
    - defaults
    - github.blog
    - github.com
safe-outputs:
  create-pull-request:
    reviewers: [mona]
    draft: false
    max: 1
---

# Update GitHub Information

Maintain the repository's GitHub information page and propose every change through a pull request for Mona to review.

1. Read `notes/mona-notes.md` for the repository's context and instructions.
2. Use web-fetch to read `https://github.blog/latest/`.
3. Use web-fetch to read `https://github.blog/changelog/`.
4. Use the GitHub repository API tools to read any repository guidance or reference files needed to make the update.
5. Update `site/content/github-info.md` with accurate, relevant information based on the notes and fetched sources. Keep the existing structure and style unless a change is necessary.
6. Review the resulting diff for accuracy and scope.
7. Open one pull request containing the update, with Mona requested as a reviewer. Do not write directly to the default branch.