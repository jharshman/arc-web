---
title: "Token Auth"
date: 2019-07-25T14:34:39-06:00
draft: false
---

Arc supports Vault's default [token auth method]().
Token authentication is built-in to Vault, and requires no extra setup on your instance to start using it with Arc.

### Example arc.yaml
```
VaultAddr: "https://vault.example.com:8200"
Auth:
  Method: token
  Token: "<vault token>"
```
