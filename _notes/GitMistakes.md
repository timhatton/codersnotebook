---
layout: note
title: Fixing Git mistakes
category: GIT
---

# To fix mistakes in Git
## To include minor changes in the last commit
If you realise there is a minor mistake after a commit has 
been done it is possible to *amend* the previous commit with new changes.
```
git commit --amend --no-edit
```
The *--no-edit* means that you will not be prompted to change the message.

> This can't be done after a commit has been pushed.

## To recover a deleted filr
```
git checkout -- filename
```

## To undo the last (unpushed) commit
To undo the last commit and return the changes to the staged area:

```
git reset HEAD^
```

This is ideal when you make a commit and then realise you should should have split the commit.