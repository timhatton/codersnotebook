---
layout: note
title: Git miscellanea
category: GIT
---

# GIT miscellaneous commands
## To discard all uncomitted local changes
```shell
git reset --hard
```
## To move commits in master to a new branch
Sometime changes are made in master and committed (but not pushed) and then the decision is made to move these to a different branch and roll master back.

> Note: Any changes not committed will be lost.

For example top remove the last 3 commits from master and move them to newbranch:
```shell
git branch newbranch      # Create a new branch, saving the desired commits
git reset --hard HEAD~3   # Move master back by 3 commits (GONE from master)
git checkout newbranch    # Go to the new branch that still has the desired commits
```

## To delete a local branch
```shell
git branch -d the_local_branch
```
## To merge
```shell
git mergetool
```

## List commits in branch (compared to master)
```shell
git --no-pager log master..BranchName
```

## List unpushed commits
Alias
```shell
git unpushed
```
Raw git
```shell
git --no-pager log @{u}..
```

## List recent (last 20) commit history
Alias
```shell
git hist
```
Raw git
```shell
git --no-pager log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short  -n 20
```

## List complete commit history
Alias
```shell
git lhist
```
Raw git
```shell
git --no-pager log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short
```
## List changes to individual gile
```shell
git log -p -- path/to/file
```

## List aliases
```shell
git config --get-regexp alias
```

## To setup a credential manager on Linux
```shell
git config --global credential.helper store
```
Pull the repository and the next time the it is pushed the credentials will be cached.

> "The credentials are stored in a file on the disk, with the disk permissions of "just user readable/writable" but still in plaintext."

Reference: [See Stackoverflow question](https://stackoverflow.com/questions/35942754/how-to-save-username-and-password-in-git-gitextension)