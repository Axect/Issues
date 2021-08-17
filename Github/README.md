# Personal Access Token (After August 13, 2021)

```sh
remote: Support for password authentication was removed on August 13, 2021. Please use a personal access token instead.
```

1. Unset cached password
    ```git
    git config --global --unset credential.helper
    ```

2. Go to GitHub Account settings

3. Settings > Developer Settings > Personal access tokens > Generate token

4. Select `repo`, `admin:org`, `admin:public_key`, `admin:repo_hook`, `admin:org_hook`, `user`, `admin:gpg_key`

5. `git config --global credential.helper libsecret`

6. `git pull` in your git projects

7. Provide username and generated token as a password
