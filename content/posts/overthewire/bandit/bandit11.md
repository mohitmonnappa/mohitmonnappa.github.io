---
ShowToc: false
hiddenInList: true
title: "OverTheWire: Bandit — Level 11"
date: 2024-01-11
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough", "linux"]
prev:
  title: "Level 10"
  url: "/posts/overthewire/bandit/bandit10/"
next:
  title: "Level 12"
  url: "/posts/overthewire/bandit/bandit12/"
---

## Login

SSH: `ssh bandit11@bandit.labs.overthewire.org -p 2220`

https://overthewire.org/wargames/bandit/bandit12.html


## Task

The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions.

## Solution

To rotate the characters use the tool `tr`. To rotate by 13 positions:

```bash
cat file_name | tr 'a-z' 'n-za-m' | tr 'A-Z' 'N-ZA-M'
```

The first argument takes the input string format, the second takes the output format — if `a` is rotated by 13 positions it becomes `n` and goes till `z`, then starts over from `a` to `m`. The second pipe is for uppercase characters.
