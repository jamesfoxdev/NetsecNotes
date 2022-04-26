---
tags: [Enumeration]
title: Enumeration/NSE
created: '2019-12-18T05:36:03.759Z'
modified: '2020-01-16T05:02:20.115Z'
---

# Enumeration/NSE
Find NSE scripts to scan for vulnerabilities
```
ls -l /usr/share/nmap/scripts | awk '{print $9}' | grep <service>
```
