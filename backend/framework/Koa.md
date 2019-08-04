## Installation

### Modules

> dependencies

```sh
yarn add @koa/cors dotenv jsonwebtoken koa koa-{bodyparser,jwt,router} uuid
```

> dev dependencies

```sh
yarn add @types/{dotenv,jsonwebtoken,koa{,-bodyparser,-router,__cors},uuid} cross-env nodemon rimraf ts-node typescript -D
```

### TypeORM

```sh
yarn add typeorm mysql
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
    "module": "commonjs",
    "moduleResolution": "node",
    "outDir": "/tmp/admin",
    "target": "es5"
  },
  "include": ["src/**/*.ts"],
  "exclude": ["node_modules"]
}
```

- `package.json`

```json
"scripts": {
  "serve": "cross-env NODE_ENV=development nodemon --watch 'src/**/*' -e ts,tsx --exec ts-node ./src",
  "build": "rimraf /tmp/admin && tsc",
  "go-test": "pm2 delete picoll-service-admin && pm2 start ecosystem.config.js --env test --only picoll-service-admin",
  "go-production": "pm2 delete picoll-service-admin && pm2 start ecosystem.config.js --env production --only picoll-service-admin"
}
```

- `ecosystem.config.js`

```js
```
