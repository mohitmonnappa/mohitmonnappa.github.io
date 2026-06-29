---
title: "OverTheWire: Bandit — Level 19"
date: 2024-01-19
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough"]
prev:
  title: "Level 18"
  url: "/posts/overthewire/bandit/bandit18/"
next:
  title: "Level 20"
  url: "/posts/overthewire/bandit/bandit20/"
---

The setuid binary is set to `bandit20`'s user. Check the file type of the given file — it says it is an executable, so try running it. The `euid` is set to `bandit20`, which means this gives the current user the privileges of the creator of the file. So just `cat` bandit20's password:

```bash
./bandit20-do cat /etc/bandit_pass/bandit20
```
