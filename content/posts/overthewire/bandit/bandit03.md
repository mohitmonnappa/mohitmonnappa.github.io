---
ShowToc: false
hiddenInList: true
title: "OverTheWire: Bandit — Level 3"
date: 2024-01-03
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough", "linux"]
prev:
  title: "Level 2"
  url: "/posts/overthewire/bandit/bandit02/"
next:
  title: "Level 4"
  url: "/posts/overthewire/bandit/bandit04/"
---

## Login

SSH: `ssh bandit2@bandit.labs.overthewire.org -p 2220`

## Task

The password for the next level is stored in a file called spaces in this filename located in the home directory.

## Solution

Use `ls -la` to show all files including hidden ones.
