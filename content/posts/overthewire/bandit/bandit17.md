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

SSH: `ssh bandit17@bandit.labs.overthewire.org -p 2220`

https://overthewire.org/wargames/bandit/bandit18.html


## Task

There are 2 files in the home directory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new.

## Solution

Use `diff` to compare lines of two files:

```bash
diff --suppress-common-lines -i -y passwords.old passwords.new
```

> `-i` is to ignore cases and `-y` is to display side by side.
