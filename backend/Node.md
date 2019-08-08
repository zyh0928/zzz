## pm2

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

## Eslint & Prettier

### General

```sh
# Install dependency
yarn add -D {babel-,}eslint {eslint-{config,plugin}-,}prettier
```

```json
// package.json
"eslintConfig": {
  "root": true,
  "env": {
    "node": true
  },
  "extends": [
    "plugin:prettier/recommended"
  ],
  "rules": {
    "prettier/prettier": 1,
    "no-console": 1
  },
  "parser": "babel-eslint"
},
"prettier": {
  // prettier options
}
```

### TypeScript

```sh
# Install dependency
yarn add -D @typescript-eslint/{eslint-plugin,parser} eslint {eslint-{config,plugin}-,}prettier
```

```json
// package.json
"eslintConfig": {
  "root": true,
  "env": {
    "node": true
  },
  "parser": "@typescript-eslint/parser",
  "plugins": [
    "@typescript-eslint"
  ],
  "extends": [
    "plugin:@typescript-eslint/recommended",
    "plugin:prettier/recommended",
    "prettier/@typescript-eslint"
  ],
  "rules": {
    "prettier/prettier": 1,
    "no-console": 1
  }
},
"prettier": {
  // prettier options
}
```

### Command

```json
// package.json
"scripts": {
  "lint": "eslint --fix --ext .js,.ts ."
}
```

## Babel

- Install dependency

  ```sh
  yarn add -D @babel/{core,plugin-transform-runtime,preset-env,register,runtime}
  ```

- Add `babel.config.js` on root

  ```js
  module.exports = {
    presets: ["@babel/preset-env"],
    plugins: ["@babel/plugin-transform-runtime"]
  };

  // or
  module.exports = function(api) {
    const env = api.env();

    const config = {
      presets: ["@babel/preset-env"],
      plugins: ["@babel/plugin-transform-runtime"]
    };

    return config;
  };
  ```

- Add `start.js`

  ```js
  require("@babel/register");

  module.exports = require("path/to/entry/file");
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
