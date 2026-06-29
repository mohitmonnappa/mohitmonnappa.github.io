---
title: "OverTheWire: Bandit — Level 16"
date: 2024-01-16
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough"]
prev:
  title: "Level 15"
  url: "/writeups/bandit-level-15/"
next:
  title: "Level 17"
  url: "/writeups/bandit-level-17/"
---

Run `nmap` to see the services on the ports. Use the version argument and specify the port numbers:

```bash
nmap -sV -p 31000-32000
```

Then through `ncat`, use the SSL option, connect, and submit the current level's password.
