---
hiddenInList: true
title: "OverTheWire: Bandit — Level 18"
date: 2024-01-18
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough"]
prev:
  title: "Level 17"
  url: "/posts/overthewire/bandit/bandit17/"
next:
  title: "Level 19"
  url: "/posts/overthewire/bandit/bandit19/"
---

After logging in, the `.bashrc` file automatically logs you out instantly — so pass the command in quotes after the SSH query to execute commands before it logs you out:

```bash
ssh -l bandit18 bandit.labs.overthewire.org -p 2220 "cat readme"
```

First use `ls` in quotes and we see `readme` file is present, so just `cat` the readme file.
