---
title: "OverTheWire: Bandit — Level 13"
date: 2024-01-13
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough"]
prev:
  title: "Level 12"
  url: "/writeups/overthewire/bandit/level-12/"
next:
  title: "Level 14"
  url: "/writeups/overthewire/bandit/level-14/"
---

The private key is present in the home directory. Use it to login as `bandit14` using SSH. The `-i` flag specifies the private key:

```bash
ssh -p 2220 bandit14@localhost -i sshkey.private
```

> **Note:** The permissions of the private key file should be `700`.
