# gh cli

> *Configurations for `gh` cli tool*

---

## Authenticating `gh` with a token as a secret

### Create a token on GitHub

First we want to create a new classic token we will use for authenticating `gh`.

On GitHub website:

1. Click your avatar on top right
2. Settings
3. Developer Settings
4. Personal Access Tokens
5. Tokens (classic)
6. Generate New Token
7. Enter your password when prompted.
8. When it displays your token to you save it in your password manager.
  > [!note]
  > In Bitwarden I saved mine on my user GitHub login as a hidden custom field called `Personal Access token (classic)`.

### Authenticating `gh` with the token

In terminal type

```
gh auth login
```

1. Select `GitHub.com` ia where you use GitHub
2. Select `HTTPS` as protocol
3. Select `Paste an Authentication Token` to authenticate GitHub CLI
4. Paste in the token data you just made

Now your authenticated and can work with private repos (for this session anyway)

## Backup `gh` configuration to GitHub

Now it would be awesome to create a repo out of the `.config/gh` folder. However the token data is stored in plain text in the `hosts.yml` file twice.

__`hosts.yml`__

```
github.com:
  users
    8rents
      oauth_token: ghp_my-super-secret-token-value
  git_protocol: https
  oauth_token: ghp_my-super-secret-token-value
  user: 8rents
```

It needs to be in that file in order for authentication with the host to work, but I can't commit sensitive data like that into the repository.

1. In `hosts.yml` remove both `oautb_token` values so they are blank.