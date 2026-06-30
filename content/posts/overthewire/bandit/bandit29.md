---
hiddenInList: true
title: "OverTheWire: Bandit — Level 29"
date: 2024-01-28
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough"]
prev:
  title: "Level 28"
  url: "/posts/overthewire/bandit/bandit28/"
next:
  title: "Level 30"
  url: "/posts/overthewire/bandit/bandit30/"
---

## Login

```bash
ssh bandit28@bandit.labs.overthewire.org -p 2220
```

## Task

There is a git repository at ssh://bandit28-git@localhost/home/bandit28-git/repo via port 2220. The password for the user bandit28-git is the same as for the user bandit28. Clone the repository and find the password for the next level.

## Solution

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
