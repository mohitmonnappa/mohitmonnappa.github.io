---
ShowToc: false
hiddenInList: true
title: "OverTheWire: Bandit — Level 9"
date: 2024-01-09
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough", "linux"]
prev:
  title: "Level 8"
  url: "/posts/overthewire/bandit/bandit08/"
next:
  title: "Level 10"
  url: "/posts/overthewire/bandit/bandit10/"
---

## Login

ssh bandit8@bandit.labs.overthewire.org -p 2220

## Task

The password for the next level is stored in the file data.txt and is the only line of text that occurs only once.

## Solution

Use `strings` to print human readable content from a file and pass it to `grep` with `"=="` (2 equals signs since "a few" is more than 1):

```bash
strings data.txt | grep "=="
```
