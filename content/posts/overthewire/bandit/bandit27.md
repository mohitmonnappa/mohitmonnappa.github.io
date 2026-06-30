---
ShowToc: false
hiddenInList: true
title: "OverTheWire: Bandit — Level 27"
date: 2024-01-26
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough", "linux"]
prev:
  title: "Level 25"
  url: "/posts/overthewire/bandit/bandit25/"
next:
  title: "Level 28"
  url: "/posts/overthewire/bandit/bandit28/"
---

## Login

SSH: `ssh bandit26@bandit.labs.overthewire.org -p 2220`

## Task

Good job getting a shell! Now hurry and grab the password for bandit27!

## Solution

Create a temp directory and clone the repo. Include port number `2220` after `localhost`. The password is the same as this level's password. Go into the folder and `cat` the README.
