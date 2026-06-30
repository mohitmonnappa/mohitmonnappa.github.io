---
ShowToc: false
hiddenInList: true
title: "OverTheWire: Bandit — Level 28"
date: 2024-01-27
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough", "linux"]
prev:
  title: "Level 27"
  url: "/posts/overthewire/bandit/bandit27/"
next:
  title: "Level 29"
  url: "/posts/overthewire/bandit/bandit29/"
---

## Login

SSH: `ssh bandit27@bandit.labs.overthewire.org -p 2220`

## Task

There is a git repository at ssh://bandit27-git@localhost/home/bandit27-git/repo via port 2220. The password for the user bandit27-git is the same as for the user bandit27. Clone the repository and find the password for the next level.

## Solution

Clone the repo and go inside. See the git log:

```bash
git log
```

Go to a commit using:

```bash
git checkout commit_hash
git show
```

Or in a single line:

```bash
git show commit_hash
```
