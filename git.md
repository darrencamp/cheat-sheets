---
tags:
  - git
  - code
---

# Worktree
Use a worktree when working on multiple branches at the same time or when want to checkout and test a PR branch etc without having to stash or check-in current WIP if its not convienient

## Add a worktree
`git worktree add --track -b newbranch <dest-path> origin/branch`

## Remove a worktree
`git worktree remove <dest-path>`

# Rename branch
`git branch -m <newname>`

