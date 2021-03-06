+++
date = "2017-04-15T14:39:04+02:00"
title = "Vault Integration"
url = "setup-vault-integration"

[menu.install]
  parent = "install_globals"
  identifier = "setup-vault-integration"
  weight = 1
+++

{{% alert enterprise %}}
This feature is only available in the [Enterprise Edition](https://drone.io/enterprise/)
{{% /alert %}}

The enterprise edition supports global environment variables, sourced from a vault server. Update your drone server configuration to include the vault connection details, including the vault server address and token.

```diff
services:
  drone-server:
    image: drone/drone:{{% version %}}
    ports:
      - 80:8000
    volumes:
      - /var/lib/drone:/var/lib/drone/
    restart: always
    environment:
+     VAULT_ADDR=http://vault.company.com:8200
+     VAULT_TOKEN=adb0c2b6-246f-10b3-bd9e-c23a0982043e
```

Please note that you can use any of the following vault configuration parameters:
https://www.vaultproject.io/docs/commands/environment.html

# Token

Please note that you must provide drone with the root token at this time. We are actively working to provide support for periodic tokens and automatic token renewal in a future release.

# Usage

Please see the vault usage [documentation]({{< ref "usage/secrets/secrets_vault.md" >}}) which include details usage instructions for creating and consuming vault secrets in your pipelines.
