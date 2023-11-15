## [Installation](https://nodejs.org)

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
