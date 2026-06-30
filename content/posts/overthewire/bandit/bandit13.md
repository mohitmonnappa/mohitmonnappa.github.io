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

SSH: `ssh bandit13@bandit.labs.overthewire.org -p 2220`

## Task

The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you do not get the next password, but you get a private SSH key that can be used to log into the next level.

## Solution

The private key is present in the home directory. Use it to login as `bandit14` using SSH. The `-i` flag specifies the private key:

ssh -p 2220 bandit14@localhost -i sshkey.private

> **Note:** The permissions of the private key file should be `700`.
