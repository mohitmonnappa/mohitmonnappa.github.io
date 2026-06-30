---
ShowToc: false
hiddenInList: true
title: "OverTheWire: Bandit — Level 4"
date: 2024-01-04
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough", "linux"]
prev:
  title: "Level 3"
  url: "/posts/overthewire/bandit/bandit03/"
next:
  title: "Level 5"
  url: "/posts/overthewire/bandit/bandit05/"
---

## Login

SSH: `ssh bandit3@bandit.labs.overthewire.org -p 2220`

## Task

The password for the next level is stored in a hidden file in the inhere directory.

## Solution

**Basic:** `cat` the entire directory because only one file is human readable.

To find which file has ASCII text in the entire directory: find all files and pipe it to `file`.  
We have to use `xargs` before `file`. This will give the info about the files, then we can use `grep "ASCII"` to filter out human readable files.
