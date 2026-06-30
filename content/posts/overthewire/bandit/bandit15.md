---
ShowToc: false
hiddenInList: true
title: "OverTheWire: Bandit — Level 15"
date: 2024-01-15
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough", "linux"]
prev:
  title: "Level 14"
  url: "/posts/overthewire/bandit/bandit14/"
next:
  title: "Level 16"
  url: "/posts/overthewire/bandit/bandit16/"
---

## Login

ssh bandit14@bandit.labs.overthewire.org -p 2220

## Task

The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

## Solution

Use `openssl` with `s_client` to connect to the server. Login and type:

```bash
openssl s_client -host localhost -port 30001
```
