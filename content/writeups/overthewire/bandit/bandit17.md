---
title: "OverTheWire: Bandit — Level 17"
date: 2024-01-17
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough"]
prev:
  title: "Level 16"
  url: "/writeups/overthewire/bandit/bandit16/"
next:
  title: "Level 18"
  url: "/writeups/overthewire/bandit/bandit18/"
---

Use `diff` to compare lines of two files:

```bash
diff --suppress-common-lines -i -y passwords.old passwords.new
```

> `-i` is to ignore cases and `-y` is to display side by side.
