---
hiddenInList: true
title: "OverTheWire: Bandit — Level 12"
date: 2024-01-12
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough", "linux"]
prev:
  title: "Level 11"
  url: "/posts/overthewire/bandit/bandit11/"
next:
  title: "Level 13"
  url: "/posts/overthewire/bandit/bandit13/"
---

## Login

```bash
ssh bandit11@bandit.labs.overthewire.org -p 2220
```

## Task

The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions.

## Solution

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
