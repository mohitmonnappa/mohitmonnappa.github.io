---
title: "OverTheWire: Bandit — Level 4"
date: 2024-01-04
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough"]
prev:
  title: "Level 3"
  url: "/writeups/overthewire/bandit/bandit03/"
next:
  title: "Level 5"
  url: "/writeups/overthewire/bandit/bandit05/"
---

**Basic:** `cat` the entire directory because only one file is human readable.

To find which file has ASCII text in the entire directory: find all files and pipe it to `file`.  
We have to use `xargs` before `file`. This will give the info about the files, then we can use `grep "ASCII"` to filter out human readable files.
