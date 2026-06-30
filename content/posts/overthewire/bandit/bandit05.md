---
ShowToc: false
hiddenInList: true
title: "OverTheWire: Bandit — Level 5"
date: 2024-01-05
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough", "linux"]
prev:
  title: "Level 4"
  url: "/posts/overthewire/bandit/bandit04/"
next:
  title: "Level 6"
  url: "/posts/overthewire/bandit/bandit06/"
---

## Login

ssh bandit4@bandit.labs.overthewire.org -p 2220

## Task

The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the "reset" command.

## Solution

**Basic:** Find the entire directory with size parameter set to 1033 bytes, then pipe it to `file` which checks for dashed file using `--` and then pipe it to `grep` for ASCII text.

It works only with the file size that is `find . -size 1033c` (bytes is represented as `c`).

**Full command:**

```bash
find . -size 1033c | xargs file -- * | grep "ASCII"
```
