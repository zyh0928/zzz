## Commitizen

### Installation

```sh
# install cli tools
yarn add -D commitizen

# initialize the conventional changelog adapter
node_modules/.bin/commitizen init cz-conventional-changelog --yarn --dev --exact
```

### Command

```json
// package.json
"scripts": {
  "commit": "git-cz"
}
```

## Tip

### Generate a new SSH key

```sh
ssh-keygen -t rsa
```

### Identity

```sh
git config --global user.name "Zeez"

git config --global user.email tutwon@gmail.com
```

### Configure Proxy

```sh
git config --global http.proxy socks5://127.0.0.1:9099

git config --global https.proxy socks5://127.0.0.1:9099
```
