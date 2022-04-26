---
tags: [Enumeration]
title: Enumeration/CGI
created: '2020-01-17T23:49:04.841Z'
modified: '2020-01-21T23:30:35.241Z'
---

# Enumeration/CGI
Check for CGI files in `cg-bin`
```
gobuster -u <target> -w /opt/SecLists-master/Discovery/Web-Content/CGIs.txt
```
Other wordlists:
1. `CGI-Microsoft.fuzz.txt`
2. `CGI-XPlatform.fuzz.txt`
