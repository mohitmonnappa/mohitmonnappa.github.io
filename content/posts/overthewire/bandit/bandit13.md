---
ShowToc: false
hiddenInList: true
title: "OverTheWire: Bandit — Level 13"
date: 2024-01-13
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough", "linux"]
prev:
  title: "Level 12"
  url: "/posts/overthewire/bandit/bandit12/"
next:
  title: "Level 14"
  url: "/posts/overthewire/bandit/bandit14/"
---

## Login

SSH: `ssh bandit12@bandit.labs.overthewire.org -p 2220`

## Task

The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command "mktemp -d". Then copy the datafile using cp, and rename it using mv.

## Solution

The private key is present in the home directory. Use it to login as `bandit14` using SSH. The `-i` flag specifies the private key:

ssh -p 2220 bandit14@localhost -i sshkey.private

> **Note:** The permissions of the private key file should be `700`.
