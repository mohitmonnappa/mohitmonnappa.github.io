---
ShowToc: false
hiddenInList: true
title: "OverTheWire: Bandit — Level 14"
date: 2024-01-14
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough", "linux"]
prev:
  title: "Level 13"
  url: "/posts/overthewire/bandit/bandit13/"
next:
  title: "Level 15"
  url: "/posts/overthewire/bandit/bandit15/"
---

## Login

SSH: `ssh bandit14@bandit.labs.overthewire.org -p 2220`

## Task

The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

## Solution

While logged in as `bandit14`, use `nc` to send data:

```bash
nc localhost 30000
```

Then enter Level 14's password.
