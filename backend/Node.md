## Eslint & Prettier

- install dependency

  ```sh
  yarn add eslint prettier eslint-plugin-prettier eslint-config-prettier babel-eslint -D
  ```

- Add .eslintrc.js on root

  ```js
  module.exports = {
    root: !0,
    env: {
      node: !0
    },
    extends: ["plugin:prettier/recommended"],
    rules: {
      "prettier/prettier": 1
    },
    parser: "babel-eslint"
  };
  ```

## Tip

### Proxy

```sh
# Yarn
yarn config set proxy http://127.0.0.1:9099

yarn config set https-proxy http://127.0.0.1:9099

# NPM
npm config set proxy http://127.0.0.1:9099

npm config set https-proxy http://127.0.0.1:9099
```

## Link

- [**Node.js**](https://nodejs.org/en/)
- [**Yarn**](https://yarnpkg.com)
- [**npm**](https://www.npmjs.com/)
