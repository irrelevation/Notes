# git
---
## Undoing things

| Command        | Scope        | Common use cases                                             |
| -------------- | ------------ | ------------------------------------------------------------ |
| `git reset`    | Commit-level | Discard commits in a private branch or throw away uncommited changes |
| `git reset`    | File-level   | Unstage a file                                               |
| `git checkout` | Commit-level | Switch between branches or inspect old snapshots             |
| `git checkout` | File-level   | Discard changes in the working directory                     |
| `git revert`   | Commit-level | Undo commits in a public branch                              |
| `git revert`   | File-level   | (N/A)                                                        |
| `git restore` |  Commit-level | (N/A) |
| `git restore` | File-level | Restore file(s) like with `git checkout`on File-level |
