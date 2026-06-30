---
hiddenInList: true
title: "OverTheWire: Bandit — Level 12"
date: 2024-01-12
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough"]
prev:
  title: "Level 11"
  url: "/posts/overthewire/bandit/bandit11/"
next:
  title: "Level 13"
  url: "/posts/overthewire/bandit/bandit13/"
---

We have the hexdump in ASCII. Use `mktemp -d` and do all the changes in the tmp folder.

We need to reverse the hexdump using `xxd -r`:

```bash
xxd -r filename.txt newfile
```

Use the `file` command to get the file signature, then use `mv` to rename to that extension.

| Extension | Format |
|-----------|--------|
| `.gz`     | gzip   |
| `.tar`    | tar    |
| `.bz2`    | bzip2  |

**To uncompress:**

```bash
# gzip
gunzip filename

# tar
tar -x -f archivename

# bzip2
bzip2 filename
```
