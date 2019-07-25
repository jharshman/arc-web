---
title: "Github Auth"
date: 2019-07-25T14:34:33-06:00
draft: false
---

Arc supports Vault's [GitHub Auth Backend](https://www.vaultproject.io/docs/auth/github.html).
Below is an example configuration for using the GitHub auth method.

### Example arc.yaml
```
VaultAddr: "https://vault.example.com:8200"
Auth:
  Method: github
  Token: "<github personal access token>"
```
