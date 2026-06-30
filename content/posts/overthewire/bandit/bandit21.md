---
ShowToc: false
hiddenInList: true
title: "OverTheWire: Bandit — Level 21"
date: 2024-01-21
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough", "linux"]
prev:
  title: "Level 20"
  url: "/posts/overthewire/bandit/bandit20/"
next:
  title: "Level 22"
  url: "/posts/overthewire/bandit/bandit22/"
---

## Login

SSH: `ssh bandit20@bandit.labs.overthewire.org -p 2220`

## Task

There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

## Solution

Go to the cron directory to see the cron jobs. We get the path of the script that is being executed — `cat` the file to see what the script is doing. It reads the contents of the passwd file and redirects it to a file in the `/tmp` directory. Just `cat` that file:

```bash
cat /etc/cron.d/cronjob_bandit22
cat /usr/bin/cronjob_bandit22.sh
cat /tmp/whatever_file_the_above_command_gave
```
