---
title: "OverTheWire: Bandit — Level 29"
date: 2024-01-28
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough"]
prev:
  title: "Level 28"
  url: "/writeups/overthewire/bandit/bandit28/"
next:
  title: "Level 30"
  url: "/writeups/overthewire/bandit/bandit30/"
---

Clone the repo and go inside. There are multiple branches — check by:

```bash
git branch -a
```

To go to a branch:

```bash
git checkout branch_name
```

Check the `dev` branch. Once you switch to a branch the file contents will be of that branch. Check the contents of the files — here, the README file has the password:

```bash
cat README.md
```
