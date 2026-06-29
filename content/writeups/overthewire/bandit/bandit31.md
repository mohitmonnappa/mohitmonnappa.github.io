---
title: "OverTheWire: Bandit — Level 31"
date: 2024-01-30
category: "Linux"
tags: ["CTF", "bandit", "overthewire", "walkthrough"]
prev:
  title: "Level 30"
  url: "/writeups/overthewire/bandit/bandit30/"
next:
  title: "Level 32"
  url: "/writeups/overthewire/bandit/bandit32/"
---

Read the `README.md` — it says we have to push a file named `key.txt` with the text `May I come in?`. But the `.gitignore` file ignores `.txt` files, so delete the `.gitignore` file and add the text to `key.txt`, then push it to the master branch to get the password:

```bash
rm .gitignore
cat > key.txt
# May I come in?
# ^C
git add .
git push origin master
```
