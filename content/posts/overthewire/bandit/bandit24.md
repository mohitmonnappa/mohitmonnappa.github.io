---
hiddenInList: true
title: "OverTheWire: Bandit — Level 24"
date: 2024-01-24
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough"]
prev:
  title: "Level 23"
  url: "/posts/overthewire/bandit/bandit23/"
next:
  title: "Level 25 & 26"
  url: "/posts/overthewire/bandit/bandit25/"
---

## Login

```bash
ssh bandit23@bandit.labs.overthewire.org -p 2220
```

## Task

A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

## Solution

We have to try all possibilities from `0000` to `9999` to get the password of the next level. Write a script that combines bandit24's password and the code with a space in between and saves it to a file, then `cat` the file and pipe it to `nc`.

**Script:**

```bash
current_pwd="gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8"
for i in {0000..9999}
do
    echo "$current_pwd $i" >> poss.txt
done
```

**Command:**

```bash
cat possibilities.txt | nc localhost 30002
```
