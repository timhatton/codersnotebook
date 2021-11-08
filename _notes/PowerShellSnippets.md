---
layout: note
title: Powershell snippets
category: Powershell
---

To bulk rename files, e.g. rename all *.old to *.new:
```powershell
Get-ChildItem -Filter "*old*" | Rename-Item -NewName {$_.name -replace 'old','new' }  
```

To do this recursively for subdirectories as well:
```powershell
Get-ChildItem -Filter "*current*" -Recurse | Rename-Item -NewName {$_.name -replace 'current','old' }  
```
