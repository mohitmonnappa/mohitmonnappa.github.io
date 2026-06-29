---
title: "OverTheWire: Bandit — Level 23"
date: 2024-01-23
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough"]
prev:
  title: "Level 22"
  url: "/writeups/overthewire/bandit/level-22/"
next:
  title: "Level 24"
  url: "/writeups/overthewire/bandit/level-24/"
---

The script will run as `bandit24` and it executes all the files in `/var/spool/bandit24/foo/` directory, then deletes them after a minute. We have to write a script to print bandit24's password and save it to a file so that the cron job will execute it.

```bash
mktemp -d
cd location
cat > script.sh
```

Script contents:

```bash
#!/bin/bash
cat /etc/bandit_pass/bandit24 > password
```

Then:

```bash
chmod 777 script.sh
touch password
chmod 666 password
cp script.sh /var/spool/bandit24/foo/
cat password
```

Wait for a minute for the password to appear.

> **Note:** If the script says "no permission" when executed manually, try changing the permissions of the temp directory so that everybody can write to it.
