---
tags: [PostEx, Powershell]
title: PostEx/Powershell Credentials
created: '2020-01-04T22:37:48.799Z'
modified: '2020-01-04T23:02:43.741Z'
---

# PostEx/Powershell Credentials

## Creating a Credentials Object From Username and Password
```
$password = ConvertTo-SecureString "<plaintext-password>" -AsPlainText -Force
$cred = NewObject System.Managment.Automation.PSCredential ("<username>", $password)
```
