---
title: "Okta Auth"
date: 2019-07-25T14:34:28-06:00
draft: false
---

Arc supports Vault's [Okta Auth Backend](https://www.vaultproject.io/docs/auth/okta.html).
Below is an example configuration for using the Okta auth method.

### Example arc.yaml
```
VaultAddr: "https://vault.example.com:8200"
Auth:
  Method: okta
  Username: "<okta username>"
  Password: "<okta password>"
```
