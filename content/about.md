---
title: "About"
date: 2019-07-15T13:14:36-06:00
draft: false
---

Arc is a simple Go template rendering utility developed with the goal of providing software developers a secure method to render templates that may include secrets such as passwords, keys, tokens, and the like. Arc is designed with minimalism as the first and foremost concern.

## Real World Example
```
$ arc --vars values.yaml ./path/to/templates | kubectl apply -f -
```

## Vault Secret Storage Integration
Secret values can be referenced through the YAML file supplying the values for the templates.
To reference a secret in Vault, it must be in the form of `key: '%vault%/path'`.  The `%vault%` designation instructs Arc that this value is a secret that needs to be resolved to it's proper value.  The path following the `%vault%` designation is that path to the secret stored within Vault.  Since there can be many key/value pairs under one path, the `key` corresponds to which field Arc should retrieve from the path.

Take for example, the following secret in Vault
```
$ vault kv get secret/credentials
...

====== Data ======
Key         Value
---         -----
username    jharshman
password    P@SSW0RD1
```

To reference these values in your YAML, you would do the following:
```
username: '%vault%/secret/data/credentials'
password: '%vault%/secret/data/credentials'
```

### Supported Vault Auth Methods

  * [Token]( {{< ref "auth-methods/token.md" >}})
  * [JWT/OIDC]( {{< ref "auth-methods/jwt.md" >}} )
  * [GitHub]( {{< ref "auth-methods/github.md" >}})
  * [Okta]( {{< ref "auth-methods/okta.md" >}} )

## Usage

```
$ arc --vars values.yaml .
```

To take advantage of Arc's integration with Vault, you will need to supply Arc with some configuration properties.
```
$ cat << EOF > ~/.arc.yaml
---
VaultAddr: "https://vault.example.com:8200"
Auth:
  Method: token
  Token: "<your vault token>"
EOF
```

Once that is complete you can run Arc as before.  Since the configuration file we created is located in the home directory, Arc will find it automatically without needing to be explicit with the `--config` flag.  This option is shown below for demonstration sake.
```
$ arc --config ~/.arc.yaml --vars values.yaml .
```

