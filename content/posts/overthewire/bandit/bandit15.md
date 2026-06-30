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

SSH: `ssh bandit15@bandit.labs.overthewire.org -p 2220`

https://overthewire.org/wargames/bandit/bandit16.html


## Task

The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL/TLS encryption.

## Solution

Use `openssl` with `s_client` to connect to the server. Login and type:

```bash
openssl s_client -host localhost -port 30001
```
