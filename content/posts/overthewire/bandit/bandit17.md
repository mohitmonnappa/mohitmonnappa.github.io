---
ShowToc: false
hiddenInList: true
title: "OverTheWire: Bandit — Level 17"
date: 2024-01-17
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough", "linux"]
prev:
  title: "Level 16"
  url: "/posts/overthewire/bandit/bandit16/"
next:
  title: "Level 18"
  url: "/posts/overthewire/bandit/bandit18/"
---

## Login

SSH: `ssh bandit16@bandit.labs.overthewire.org -p 2220`

## Task

The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL/TLS and which do not. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

## Solution

Use `diff` to compare lines of two files:

```bash
diff --suppress-common-lines -i -y passwords.old passwords.new
```

> `-i` is to ignore cases and `-y` is to display side by side.
