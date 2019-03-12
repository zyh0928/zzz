## Installation

### Modules

> dependencies

```sh
yarn add koa koa-router koa-bodyparser uuid
```

> dev dependencies

```sh
yarn add -D typescript @types/node @types/koa @types/koa-router @types/koa-bodyparser @types/uuid rimraf nodemon ts-node cross-env
```

### Eslint & Prettier

- Install dependency

  ```sh
  yarn add -D eslint prettier eslint-plugin-prettier eslint-config-prettier babel-eslint
  ```

- Add `.eslintrc.js` on root

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
    parser: "babel-eslint",
    parserOptions: {
      ecmaFeatures: {
        legacyDecorators: !0
      }
    }
  };
  ```

- Add a script in `package.json`

  ```json
  "scripts": {
    "lint": "eslint --fix --ext .js,.ts ./"
  }
  ```

### Babel

- Install dependency

  ```sh
  yarn add -D @babel/core @babel/register @babel/preset-env @babel/runtime @babel/plugin-transform-runtime
  ```

- Add `.babelrc` on root

  ```json
  {
    "presets": ["@babel/preset-env"],
    "plugins": ["@babel/plugin-transform-runtime"]
  }
  ```

- Add `start.js`

  ```js
  require("@babel/register");

  module.exports = require("path/to/entry/file");
  ```

### TypeORM

```sh
yarn add typeorm mysql
```

## Link

- [**Koa**](https://koajs.com/)
