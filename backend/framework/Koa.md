## Installation

### Modules

> dependencies

```sh
yarn add koa koa-router koa-bodyparser uuid
```

> dev dependencies

```sh
yarn add typescript @types/node @types/koa @types/koa-router @types/koa-bodyparser @types/uuid rimraf nodemon ts-node cross-env -D
```

### Eslint & Prettier

- Install dependency

  ```sh
  yarn add eslint prettier eslint-plugin-prettier eslint-config-prettier babel-eslint -D
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
  yarn add @babel/core @babel/register @babel/preset-env @babel/runtime @babel/plugin-transform-runtime -D
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

### pm2

- Command

  ```sh
  # Installation
  yarn global add pm2

  # show list
  pm2 ls

  # start and add a process to list
  pm2 start ecosystem.config.js [--only <app_name>] [--watch]

  # stop and delete a process from the list
  pm2 delete <app_name | all>

  # both stop and start
  pm2 restart <app_name | all>

  # stop the process (kill the process but keep it in the process list)
  pm2 stop <app_name | all>

  # user reload instead of restart for 0-seconds downtime reloads
  pm2 reload <app_name | all>
  ```

## Link

- [**Koa**](https://koajs.com/)
