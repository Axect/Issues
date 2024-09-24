# Permission denied (publickey)

- Setup `.ssh/config`

```
Host <ARBITRARY_NAME>
User <USERNAME>
PubKeyAuthentication yes
IdentityFile ~/.ssh/id_rsa
```
