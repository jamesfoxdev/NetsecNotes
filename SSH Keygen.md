---
tags: [Tricks]
title: Tricks/SSH Keygen
created: '2020-01-10T00:21:24.679Z'
modified: '2020-01-10T01:31:50.444Z'
---

# Tricks/SSH Keygen
On attackers side
```
chmod 0700 ~/.ssh
ssh-keygen -t rsa -C <label>
cat ~/.ssh/id_rsa.pub | xclip -sel c
```
On victim side paste the public key under `~/.ssh/authorized_keys`

