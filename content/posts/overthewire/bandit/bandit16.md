---
hiddenInList: true
title: "OverTheWire: Bandit — Level 16"
date: 2024-01-16
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough"]
prev:
  title: "Level 15"
  url: "/posts/overthewire/bandit/bandit15/"
next:
  title: "Level 17"
  url: "/posts/overthewire/bandit/bandit17/"
---

## Login

```bash
ssh bandit15@bandit.labs.overthewire.org -p 2220
```

## Task

The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL/TLS encryption.

## Solution

Run `nmap` to see the services on the ports. Use the version argument and specify the port numbers:

```bash
nmap -sV -p 31000-32000
```

Then through `ncat`, use the SSL option, connect, and submit the current level's password.
