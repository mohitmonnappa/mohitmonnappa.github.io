---
title: "OverTheWire: Bandit — Level 6"
date: 2024-01-06
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough"]
prev:
  title: "Level 5"
  url: "/posts/overthewire/bandit/bandit05/"
next:
  title: "Level 7"
  url: "/posts/overthewire/bandit/bandit07/"
---

**Basic:** Go to root directory and find the entire directory with `-group`, `-user` and `-size`, pipe it to `file` and pipe it to `grep` to ASCII text.

**Full command:**

```bash
find . -group bandit6 -user bandit7 -size 33c -type f | xargs file * | grep "ASCII"
```
