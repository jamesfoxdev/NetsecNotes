---
tags: [DNS, Enumeration]
title: Enumeration/DNS
created: '2019-12-21T04:23:00.944Z'
modified: '2020-01-04T23:22:29.254Z'
---

# Enumeration/DNS
## DNS host queries
Find name servers for a given domain
```
host -t ns <domain>
```
Find mail servers for a given domain
```
host -t mx <domain>
```
## Attempt a DNS Zone Transfer
If the DNS server supports TCP, try and attempt a zone transfer
```
dig axfr @<target>
```
