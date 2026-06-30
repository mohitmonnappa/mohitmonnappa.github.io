---
hiddenInList: true
title: "OverTheWire: Bandit — Level 10"
date: 2024-01-10
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough"]
prev:
  title: "Level 9"
  url: "/posts/overthewire/bandit/bandit09/"
next:
  title: "Level 11"
  url: "/posts/overthewire/bandit/bandit11/"
---

## Login

```bash
ssh bandit9@bandit.labs.overthewire.org -p 2220
```

## Task

The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several '=' characters.

## Solution

Use `base64 -d` to decode the string:

```bash
cat data.txt | base64 -d
```
