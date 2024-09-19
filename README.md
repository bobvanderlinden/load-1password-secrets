# load-1password-secrets

Loads secrets from 1password into environment variables.
This uses a file similar to the file described in [op run](https://developer.1password.com/docs/cli/reference/commands/run).

This action is intended to be used in combination with [direnv-1password](https://github.com/tmatilai/direnv-1password), to share secrets across CI _and_ development environments.

## Usage

Create a file `.1password` like:

```txt
DB_USERNAME=op://My Vault/db/username
DB_PASSWORD=op://My Vault/db/password
```

Add the following to your GitHub Action workflow:

```yaml
steps:
  ...
  - uses: bobvanderlinden/load-1password-secrets
    with:
      service-account-token: ${{ secrets.OP_SERVICE_ACCOUNT_TOKEN }}
      path: .1password
```
