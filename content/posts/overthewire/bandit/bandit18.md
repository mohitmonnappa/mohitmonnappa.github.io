---
ShowToc: false
hiddenInList: true
title: "OverTheWire: Bandit — Level 18"
date: 2024-01-18
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough", "linux"]
prev:
  title: "Level 17"
  url: "/posts/overthewire/bandit/bandit17/"
next:
  title: "Level 19"
  url: "/posts/overthewire/bandit/bandit19/"
---

## Login

SSH: `ssh bandit17@bandit.labs.overthewire.org -p 2220`

## Task

There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new.

## Solution

After logging in, the `.bashrc` file automatically logs you out instantly — so pass the command in quotes after the SSH query to execute commands before it logs you out:

ssh -l bandit18 bandit.labs.overthewire.org -p 2220 "cat readme"

First use `ls` in quotes and we see `readme` file is present, so just `cat` the readme file.
