---
tags: [AD, Enumeration]
title: Enumeration/AD-CS
created: '2020-01-04T22:14:03.310Z'
modified: '2020-01-04T22:50:33.559Z'
---

# Enumeration/AD-CS
Active Directory Certificate Service allows administrators to customize services in order to issue and manage public key certificates. As such it handles network enrollment, wifi certificates, SSL certificates, etc. 

## Interacting via HTTP (authenticated)
```
firefox http://<target>/certsrv
```

## Generate and Sign a Certificate
1. Create the rsa key 
```
openssl genrsa -aes256 -out <outfile>.key 2048
```
2. Create the certificate signing request
```
openssl req -new -key <outfile>.key -out <outfile>.csr
```
3. Copy the CSR
```
cat <outfile>.csr | xclip -sel c
```
4. Login to certsrv
5. Request a certificate
6. Advanced certficate request
7. Submit
8. Download the signed cert
