---
ShowToc: false
hiddenInList: true
title: "OverTheWire: Bandit — Level 1"
date: 2024-01-01
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough", "linux"]
next:
  title: "Level 2"
  url: "/posts/overthewire/bandit/bandit02/"
---

## Login

SSH: `ssh bandit1@bandit.labs.overthewire.org -p 2220`

## Task

The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

## Solution
'-' is a special symbol in linux, which is the standard option character. It is used for adding flags for commands.  
This is why files with this symbol as the first symbol can't be referenced like other files.

The `cat -` command doesn't return anything. Therefore, we add the current path to the beginning.  
We can use shell redirection also using the `<`.

```bash
cat ./-
# or 
cat < -
```

> **Extra:** To create a dashed file: `touch ./-`
