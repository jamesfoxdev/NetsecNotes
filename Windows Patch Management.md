---
tags: [PostEx]
title: PostEx/Windows Patch Management
created: '2020-01-22T10:34:54.819Z'
modified: '2020-01-23T02:13:59.034Z'
---

# PostEx/Windows Patch Management
List patches and hotfixes
```
wmic qfe get Caption,Description,HotFixID,InstalledOn
```
Common vulnerable patches
- KiTrap0D (`KB979682`)
- MS11-011 (`KB2393802`)
- MS10-059 (`KB982799`)

Search for these vulnerable versions
```
wmic qfe get Caption,Description,HotFixID,InstalledOn | findstr /C:<patch>
```
