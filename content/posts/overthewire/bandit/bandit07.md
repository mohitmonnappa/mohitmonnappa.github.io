---
ShowToc: false
hiddenInList: true
title: "OverTheWire: Bandit — Level 7"
date: 2024-01-07
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough", "linux"]
prev:
  title: "Level 6"
  url: "/posts/overthewire/bandit/bandit06/"
next:
  title: "Level 8"
  url: "/posts/overthewire/bandit/bandit08/"
---

## Login

SSH: `ssh bandit7@bandit.labs.overthewire.org -p 2220`

Challenge URL: https://overthewire.org/wargames/bandit/bandit8.html


## Task

The password for the next level is stored in the file data.txt next to the word millionth.

## Solution

Just `cat` the file and pass it to `grep` with the word `millionth`:

```bash
cat data.txt | grep "millionth"
```
