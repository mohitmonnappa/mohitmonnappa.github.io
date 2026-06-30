---
ShowToc: false
hiddenInList: true
title: "OverTheWire: Bandit — Level 6"
date: 2024-01-06
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough", "linux"]
prev:
  title: "Level 5"
  url: "/posts/overthewire/bandit/bandit05/"
next:
  title: "Level 7"
  url: "/posts/overthewire/bandit/bandit07/"
---

## Login

SSH: `ssh bandit6@bandit.labs.overthewire.org -p 2220`

https://overthewire.org/wargames/bandit/bandit7.html


## Task

The password for the next level is stored somewhere on the server and has all of the following properties: owned by user bandit7, owned by group bandit6, 33 bytes in size.

## Solution

**Basic:** Go to root directory and find the entire directory with `-group`, `-user` and `-size`, pipe it to `file` and pipe it to `grep` to ASCII text.

**Full command:**

```bash
find . -group bandit6 -user bandit7 -size 33c -type f | xargs file * | grep "ASCII"
```
