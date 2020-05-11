---
layout: note
title: Github workflow
category: GIT
---

# Start from existing repo
If you don't already have a working directory clone the repository:
``` shell
git clone [url]
```
In the working directory ensure that there is a remote connection:

git remote -v

The remote repo can now be referred to as origin and the branch master.
To create a new repo

# To create a new repo from the current directory:
``` sql
git init
git add .
git commit -m "Initial commit"
```
To push this to GitHub create the new repository via the GitHub website and then follow the instructions there.

This will be
``` sql
git remote add origin  URL
git push origin master
```
Note that for GitHub URL will be in the form:

https://github.com/USER/REPONAME

# Making changes
To make changes:

Create a local feature branch:
``` sql
git branch some-feature
```
Switch to the new branch
``` sql
git checkout some-feature
```
To create a branch and switch in one command:
``` sql
git checkout -b some-feature
```
# Make changes to files.

Stage changes:
``` sql
git add .
```
Commit changes int the local branch
``` sql
git commit -m "some-feature done"
```
Alias to stage and commit in one go
``` sql
git com "Some-feature done"
```
To merge back into the master:
``` sql
git checkout master
git merge origin master
git merge some-feature --squash
```
Note that the squash option means that all commits in the some-feature branch are squashed into one commit. 

# Pulling and pushing Pull to get the latest version from the remote repo:
``` sql
git pull
```
Push to write back to the remote repo:
``` sql
git push
```
# Tagging

To release a version tag it as follows:
``` sql
git tag -a vX.Y.X -m "message"
```
It is necessary to push the tag to the remote repo:

To push a particular tag:
``` sql
git push TAGNAME
```
Or to push all tags (which should just be one anyway):
``` sql
git push --tags
```
