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