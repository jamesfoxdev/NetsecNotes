---
tags: [Enumeration]
title: Enumeration/POP3 SSL Login
created: '2020-01-09T00:08:53.738Z'
modified: '2020-01-10T01:31:36.004Z'
---

# Enumeration/POP3 SSL Login
```
openssl s_client -connect mail.example.com:995
```
Or for Microsoft Exchange Servers
```
openssl s_client -crlf -connect mail.example.com:110 -starttls pop3
```
