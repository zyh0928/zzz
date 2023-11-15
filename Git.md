## Tip

### Generate a new SSH key

```sh
ssh-keygen -t rsa
```

### Identity

```sh
# global
git config --global user.name Zeez
git config --global user.email tutwon@gmail.com

# local
git config user.name Zeez
git config user.email tutwon@gmail.com

```

### Rebase

```sh
# can use commit id or HEAD~n
git rebase -i HEAD~n

# change commit message, pick -> reword or r

# change author & email, pick -> edit or e
git commit --amend --author="Zeez <tutwon@gmail.com>" --no-edit
git rebase --continue

```

### Configure Proxy

```sh
git config --global http.proxy socks5://127.0.0.1:9099
git config --global https.proxy socks5://127.0.0.1:9099

```

## [Commitizen](https://github.com/commitizen/cz-cli)
