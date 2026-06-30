---
hiddenInList: true
title: "OverTheWire: Bandit — Level 21"
date: 2024-01-21
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough"]
prev:
  title: "Level 20"
  url: "/posts/overthewire/bandit/bandit20/"
next:
  title: "Level 22"
  url: "/posts/overthewire/bandit/bandit22/"
---
hiddenInList: true

Go to the cron directory to see the cron jobs. We get the path of the script that is being executed — `cat` the file to see what the script is doing. It reads the contents of the passwd file and redirects it to a file in the `/tmp` directory. Just `cat` that file:

```bash
cat /etc/cron.d/cronjob_bandit22
cat /usr/bin/cronjob_bandit22.sh
cat /tmp/whatever_file_the_above_command_gave
```
