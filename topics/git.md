# git
---


## Undoing things

| Command        | Scope        | Common use cases                                             |
| -------------- | ------------ | ------------------------------------------------------------ |
| `git reset`    | Commit-level | Discard commits in a private branch or throw away uncommited changes |
| `git reset`    | File-level   | Unstage a file                                               |
| `git checkout` | Commit-level | Switch between branches or inspect old snapshots             |
| `git checkout` | File-level   | Discard changes in the working directory                     |
| `git revert`   | Commit-level | Undo commits in a public branch |
| `git restore` | File-level | Restore file(s) like with `git checkout`on File-level |
| `git commit --amend`| Commit-level | Replace the most recent commit |
| `git rebase -i`| Commit-level | Change past commits |

If you ever need to remove something not only from your commit, but also from the entire history of the repo (e.g. an access token you accidentally commited) you can use `git filter-repo`. This is not a git core functionality but a commandline tool you need to install (e.g. via `brew install git-filter-repo`. Then you can purge a file from your repo with `git filter-repo --invert-paths --path PATH-TO-YOUR-FILE-WITH-SENSITIVE-DATA`.

further infos: [Removing sensitive data from a repository
](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository)

---



## Commits

Create commits that only include changes from a **single** topic.

- You can partially add a file with `git add -p`

Craft better commit messages by adding a message body to your message subject. Type `git commit`and in the editor add a blank line after the subject. The following block will automatically be interpreted as the message body.

---



## Branching

Branching strategies differ from team to team. Make sure to put your strategy into writing. This minimizes conflicts and makes the onboarding process easier.

Branching strategies depend on the way you integrate changes & structure your releases. Consider your project, your release cycle and your team when picking a branching strategy. Let's look at two different approaches:

#### Mainline Development

> Allway be integrating

- few branches
- small commits
- High-quality testing & QA standards

#### State, Release, and Feature Branches

- more branches
- different branches fulfill different roles



### Long-Running vs. Short-Lived Branches

#### Long-Running Branches

- exist throughout the complete lifetime of a project
- often correspond to stages of your developement lifecycle, eg. development, production, staging (called integration branches)
- don't directly commit to Long-Running Branches. Commits only get integrated through merging or rebasing.
  - To ensure quality: code wil go through Testing and Review stages (with corresponding branches) before getting integrated into production
  - For release bundling and scheduling

#### Shot-Lived Branches

- for new features, bug fixes, refactoring, experiments...
- based on a long running branch
- will be deleted after integration



### Example Branching Strategies

#### GitHub Flow

- Simple & lean
- 1 long running branch ("main")
- everything you are working on lives in a seperate short lived branch

#### GitFlow

- more structure, more rules

- Long-running branches: 

  - "main" - reflects production state, base for dev-branch
  - "develop" - base for release & feature branches, merges features back into it once they are done

- Short-Lived Branches:

  - Features

  - Releases

    1. Do testing

    2. Commit bugfixes

    3. Merge it back into main

    4. Add a tag for the release commit on main
    5. close the release branch

  - Hotfixes

---



## Pull Requests

- Are not a feature of git. They are provided by your git hosting platform and therefore can differ slightly
- invite reviewers to provide **feedback** before merging
- provide a way to contribute to repos you can't directly write to
- are based on branches, not commits

---



## Merge Conflicts

Solve Merge Conflicts by cleaning up the files that triggered it. Sometimes it is helpfull to use a mergetool. You can configure a merge tool as follows:

```bash
git config --global merge.tool <tool>
git config --global mergetool.<tool>.cmd <command>
# if you can't use your editors exit code to determine wether the merge conflict got resolved, add the following line:
git config --global mergetool.<tool>.trustExitCode false
```



Visual Studio Code Example:

```bash
# Add VS Code as your mergetool
git config --global merge.tool vscode
git config --global mergetool.vscode.cmd 'code --wait $MERGED'
# Add VS Code as your difftool
git config --global diff.tool vscode
git config --global difftool.vscode.cmd 'code --wait --diff $LOCAL $REMOTE'
# Add VS Code as your default editor
git config --global core.editor vscode
```



Merge Conflicts don't allways have to be resolved. They can be aborted via `git merge --abort`or `git rebase abort`.

---



## Merge vs. Rebase

### Merge
Merging is based on three commits. The common ancestor (where the two branches divert from), the latest commit on the current branch and the latest commit on the branch to be merged. If the current branch did not change after the other branch diverged, git will do a "fast forward commit" meaning both branches share a common history.
Usually branches do evolve differently, in this case a merge commit is commited automatically to the current branch.

### Rebase
Will base the branch to be integrated on the current branch, whereby rewriting the commit history. This makes for a cleaner commit history with less forks in the road. But be careful - this strategy can lead to problems if applied to commits that have been made public (pushed to a shared repository). Only use rebasing to clean up your local commit history. The rebase process in detail:

1. git removes all commits that happened after the common ancestor commit from the branch we want to rebase.
2. git applies the new commits from the current. Now both branches temporarily look exactly the same.
3. git reapplies the commits from the branch we want to rebase.

### Interactive Rebase
Use interactive rebase to optimise & clean up your commit history. As with normal rebasing be careful not to interactively rebase branches that have been made public. You can:

- change a commit's message
- delete commits
- reorder commits
- combine multiple commits into one
- edit/split an existing commit into multiple new ones


---



## Cherry-Pick

Cherry-pick is used to select individual commits to be integrated. It can be used to:

- move a commit to a different branch

---



## The Reflog

The reflog records when the tip of branches and other references were updated. The `git reflog`command can be used to:

- restore deleted commits
- restore deleted branches

---



## Submodules

The submodules command can be used to store another repositories in the directory of your git repository without adding them to your repository. The repository will only store its submodule's configurations. If you clone a repository that contains submodules the submodules will not be copied to your working directory. In order to change that you need to set an extra flag. `git clone --recurse-submodules` will clone the repository including submodules. If you forgot to set the flag you can use `git submodules update --init --recursive` to clone the submodules.

Submodules don't get checked out on a branch but a specific revision.

---



## Searching & Finding

| Search by | Command |
| --- | --- |
|  date | `git log --before=<date>` `git log --after=<date>` |
| message | `git log --grep=<pattern>`|
| author | `git log --author=<pattern>`|
| file | `git log -- <filename>` |
| branch | `git log <branch1>..<branch2>` (will show all files that are in branch1 but not in branch2) |

---



## Sources

[Atlassian](https://www.atlassian.com/git)
[The Advanced Git Kit](https://www.git-tower.com/learn/git/advanced-git-kit/)
[Git Homepage](https://git-scm.com/)