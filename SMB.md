---
tags: [AD, Enumeration, SMB]
title: Enumeration/SMB
created: '2019-12-17T03:58:57.779Z'
modified: '2020-01-05T04:25:00.061Z'
---

# Enumeration/SMB
## SMB Versions
> SMB1 – Windows 2000, XP and Windows 2003.
  SMB2 – Windows Vista SP1 and Windows 2008
  SMB2.1 – Windows 7 and Windows 2008 R2
  SMB3 – Windows 8 and Windows root2012

## Scan a subnet for SMB service
```
nbtscan -r <network-range>
```

## Null sessions
> "A null session refers to an unauthenticated NetBIOS session between two computers.
This feature exists to allow unauthenticated machines to obtain browse lists from other
Microsoft servers"

Using RPCclient
```
rpcclient -U "" <target>
rpcclient $> srvinfo
rpcclient $> enumdomusers
rpcclient $> getdompwinfo
```
Simplification using enum4linux
```
enum4linux -a <target>
```

## List available SMB Shares
```
smclient -L //<target>
```
With null authentication
```
smbclient -N -L //<target>
```

## Mounting and Exploring Shares
Check SMB connection
```
smbclient //<target>/<share>
```
Mount the share
```
mkdir /mnt/smbshare
mount -t cifs //<target>/<share> /mnt/smbshare
```
Check access controls on share subdirectories
```
smbcacls //<target><share> /<directory>
```
For example, null authenticate then check all subdirectories for access
```
for i in $(ls /mnt/smbshare); do echo $i; smbcacls -N //<target>/<share> $i; done
```

## Authenticated SMB Enumeration
```
smbmap -u <username> -d <domain> -p <password> -H <target>
```

## SMB Vulnerability Checking
### Nmap SMB NSE Scripts
Find scripts
```
ls -l /usr/share/nmap/scripts/smb*
```
Test for MS08-067
```
nmap -v -p 139,445 --script=smb-vuln-ms08-067 --script-args=unsafe=1 <target>
```
Test for other SMB vulns
```
nmap -v -p 139,445 --script vuln --script-args=unsafe=1 <target>
```

#### Example NSE scripts
> smb2-capabilities.nse
  smb2-security-mode.nse
  smb2-time.nse
  smb2-vuln-uptime.nse
  smb-brute.nse
  smb-double-pulsar-backdoor.nse
  smb-enum-domains.nse
  smb-enum-groups.nse
  smb-enum-processes.nse
  smb-enum-services.nse
  smb-enum-sessions.nse
  smb-enum-shares.nse
  smb-enum-users.nse
  smb-flood.nse
  smb-ls.nse
  smb-mbenum.nse
  smb-os-discovery.nse
  smb-print-text.nse
  smb-protocols.nse
  smb-psexec.nse
  smb-security-mode.nse
  smb-server-stats.nse
  smb-system-info.nse
  smb-vuln-conficker.nse
  smb-vuln-cve2009-3103.nse
  smb-vuln-cve-2017-7494.nse
  smb-vuln-ms06-025.nse
  smb-vuln-ms07-029.nse
  smb-vuln-ms08-067.nse
  smb-vuln-ms10-054.nse
  smb-vuln-ms10-061.nse
  smb-vuln-ms17-010.nse
  smb-vuln-regsvc-dos.nse

