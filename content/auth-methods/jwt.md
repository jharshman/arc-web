---
title: "JWT/OIDC Auth"
date: 2019-07-25T14:34:23-06:00
draft: false
---

Arc supports Vault's [JWT/OIDC Auth Backend](https://www.vaultproject.io/docs/auth/jwt.html#jwt-authentication).
Below is an example configuration for using the JWT auth method.

### Example arc.yaml
```
VaultAddr: "https://vault.example.com:8200"
Auth:
  Method: jwt
  Role: "<jwt/oidc role>"
  Token: "<jwt/oidc token>"
```

