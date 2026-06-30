---
hiddenInList: true
title: "OverTheWire: Bandit — Level 14"
date: 2024-01-14
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough"]
prev:
  title: "Level 13"
  url: "/posts/overthewire/bandit/bandit13/"
next:
  title: "Level 15"
  url: "/posts/overthewire/bandit/bandit15/"
---

## Login

```bash
ssh bandit13@bandit.labs.overthewire.org -p 2220
```

## Task

The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you do not get the next password directly, but you get a private SSH key that can be used to log into the next level.

## Solution

While logged in as `bandit14`, use `nc` to send data:

```bash
nc localhost 30000
```

Then enter Level 14's password.
