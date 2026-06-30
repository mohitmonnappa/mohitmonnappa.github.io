---
ShowToc: false
hiddenInList: true
title: "OverTheWire: Bandit — Level 30"
date: 2024-01-29
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough", "linux"]
prev:
  title: "Level 29"
  url: "/posts/overthewire/bandit/bandit29/"
next:
  title: "Level 31"
  url: "/posts/overthewire/bandit/bandit31/"
---

## Login

SSH: `ssh bandit29@bandit.labs.overthewire.org -p 2220`

## Task

There is a git repository at ssh://bandit29-git@localhost/home/bandit29-git/repo via port 2220. The password for the user bandit29-git is the same as for the user bandit29. Clone the repository and find the password for the next level.

## Solution

There is a feature called **tag** in git. Git tagging is a way to mark specific points in the history of the repository.

To see tags:

```bash
git tag
```

To show the tag message:

```bash
git show tag_name
```

Here:

```bash
git tag
git show secret
```
