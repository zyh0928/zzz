## [acme.sh](https://github.com/Neilpang/acme.sh)

### Install online

```sh
curl https://get.acme.sh | sh
# or
wget -O -  https://get.acme.sh | sh
```

### Use Hurricane Electric

- Export

  ```sh
  export HE_Username="username"
  export HE_Password="password"
  ```

- Issue a cert: `acme.sh --issue --dns dns_he -d wjbzg.com -d *.wjbzg.com`

- Force to renew a cert: `acme.sh --renew -d wjbzg.com -d *.wjbzg.com --force`

  _All the certs will be renewed automatically every 60 days_

### Install the cert to Nginx

```sh
acme.sh --install-cert -d wjbzg.com -d *.wjbzg.com \
--key-file /path/to/keyfile/in/nginx/key.pem \
--fullchain-file /path/to/fullchain/nginx/cert.pem \
--reloadcmd "service nginx force-reload"
```

### Upgrade `acme.sh`

- Update `acme.sh` to the latest code: `acme.sh --upgrade`
- Enable auto upgrade: `acme.sh --upgrade --auto-upgrade`
- Disable auto upgrade: `acme.sh --upgrade --auto-upgrade 0`
