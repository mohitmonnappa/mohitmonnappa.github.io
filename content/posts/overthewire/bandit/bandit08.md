---
ShowToc: false
hiddenInList: true
title: "OverTheWire: Bandit — Level 8"
date: 2024-01-08
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough", "linux"]
prev:
  title: "Level 7"
  url: "/posts/overthewire/bandit/bandit07/"
next:
  title: "Level 9"
  url: "/posts/overthewire/bandit/bandit09/"
---

## Login

SSH: `ssh bandit8@bandit.labs.overthewire.org -p 2220`

https://overthewire.org/wargames/bandit/bandit9.html


## Task

The password for the next level is stored in the file data.txt and is the only line of text that occurs only once.

## Solution

Use `sort` to sort the words in dictionary order so that repeated words will be together.  
Next use `uniq` to see the unique lines and count the number of words.  
`uniq -u` will directly give the unique word in the file, or you can display the count and grep `1` from there.

**Simplest:**

```bash
cat data.txt | sort -f -d | uniq -u
```

> `-f` is to ignore the case of the letter and `-d` is for dictionary ordering.

**Second method:**

```bash
cat data.txt | sort -f -d | uniq -c | grep " 1 "
```

> `-c` is to display the count, i.e. number of times it has been repeated.
