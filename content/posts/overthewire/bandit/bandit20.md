---
ShowToc: false
hiddenInList: true
title: "OverTheWire: Bandit — Level 20"
date: 2024-01-20
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough", "linux"]
prev:
  title: "Level 19"
  url: "/posts/overthewire/bandit/bandit19/"
next:
  title: "Level 21"
  url: "/posts/overthewire/bandit/bandit21/"
---

## Login

SSH: `ssh bandit19@bandit.labs.overthewire.org -p 2220`

## Task

To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.

## Solution

The setuid binary makes a connection to `localhost` on the port you specify as a command-line argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

To achieve this, set up a netcat listener to get back the password. Start a netcat server in the background using `&` (ampersand):

```bash
echo "0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO" | nc -l -p 5555 &
./suconnect 5555
```

> We need to start `nc` in server mode so `-l` and `-p` will be separate flags.
