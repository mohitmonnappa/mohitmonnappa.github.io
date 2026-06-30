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

SSH: `ssh bandit6@bandit.labs.overthewire.org -p 2220`

## Task

The password for the next level is stored somewhere on the server and has all of the following properties: owned by user bandit7, owned by group bandit6, 33 bytes in size.

## Solution

Just `cat` the file and pass it to `grep` with the word `millionth`:

```bash
cat data.txt | grep "millionth"
```
