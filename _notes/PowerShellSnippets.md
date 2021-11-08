---
layout: note
title: SQL tips and tricks
category: Powershell
---

To bulk rename files, e.g. rename all *.old to *.new.
```powershell
Get-ChildItem -Filter “*old*” -Recurse | Rename-Item -NewName {$_.name -replace ‘old’,’new’ }  
```
