## [Installation](https://koajs.com)

### Modules

> dependencies

```sh
yarn add @koa/cors dotenv jsonwebtoken koa koa-{bodyparser,helmet,router} uuid
```

> dev dependencies

```sh
yarn add -D @types/{dotenv,jsonwebtoken,koa{,-bodyparser,-helmet,-router,__cors},uuid,webpack} {copy,terser}-webpack-plugin cross-env nodemon rimraf ts-{loader,node} tsconfig-paths{,-webpack-plugin} typescript webpack{,-cli,-filter-warnings-plugin,-merge}
```

### TypeORM

```sh
yarn add mysql reflect-metadata typeorm
```

## Tip

### Configuration

- `tsconfig.json`

  ```json
  {
    "compilerOptions": {
      "allowJs": true,
      "baseUrl": ".",
      "emitDecoratorMetadata": true,
      "esModuleInterop": true,
      "experimentalDecorators": true,
      "lib": ["esnext", "dom", "dom.iterable", "scripthost"],
      "paths": {
        "@/*": ["src/*"]
      },
      "target": "es5"
    },
    "include": ["src/**/*.ts"],
    "exclude": ["node_modules"]
  }
  ```

- `package.json`

  ```json
  "scripts": {
    "serve": "cross-env NODE_ENV=development nodemon --watch 'src/**/*' -e ts,tsx --exec ts-node -r tsconfig-paths/register src",
    "build:test": "rimraf dist && webpack --config build/webpack.config.test",
    "build:prod": "rimraf dist && webpack --config build/webpack.config.prod"
  }
  ```
