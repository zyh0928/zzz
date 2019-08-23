## Command

```sh
# Update package database with apt
sudo apt update

# Upgrade installed packages with apt
sudo apt upgrade
sudo apt full-upgrade

# Clean system with apt
sudo apt autoremove

# Remove installed packages with apt
# just removes the binaries of a package. It leaves residue configuration files
sudo apt remove <package_name>
# removes everything related to a package including the configuration files
sudo apt purge <package_name>
```

## [acme.sh](https://github.com/Neilpang/acme.sh)

### Install online

```sh
curl https://get.acme.sh | sh
# or
wget -O - https://get.acme.sh | sh
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
acme.sh --installcert -d wjbzg.com -d *.wjbzg.com \
--key-file /www/picoll/ssl/wjbzg.com.key \
--fullchain-file /www/picoll/ssl/fullchain.cer \
--reloadcmd "nginx -s reload"
```

### Upgrade `acme.sh`

- Update `acme.sh` to the latest code: `acme.sh --upgrade`
- Enable auto upgrade: `acme.sh --upgrade --auto-upgrade`
- Disable auto upgrade: `acme.sh --upgrade --auto-upgrade 0`

## [Node.js](https://github.com/nodesource/distributions)

```sh
curl -sL https://deb.nodesource.com/setup_11.x | sudo -E bash -
sudo apt-get install -y nodejs
```

## [Yarn](https://yarnpkg.com/lang/en/docs/install/#debian-stable)

```sh
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
sudo apt-get update && sudo apt-get install yarn
```

## Shadowsocks

- install tool

  ```sh
  # pip
  sudo apt install python3-pip

  # shadowsocks
  pip3 install https://github.com/shadowsocks/shadowsocks/archive/master.zip
  ```

- configuration shadowsocks

  ```sh
  sudo mkdir /etc/shadowsocks

  sudo vim /etc/shadowsocks/config.json
  ```

  ```json
  {
    "server_port": 9099,
    "password": "password",
    "method": "aes-256-cfb",
    "fast_open": false
  }
  ```

- systemd service

  ```sh
  sudo vim /etc/systemd/system/shadowsocks-server.service

  sudo systemctl start shadowsocks-server

  sudo systemctl enable shadowsocks-server
  ```

  ```bat
  [Unit]
  Description=Shadowsocks Server
  After=network.target

  [Service]
  ExecStart=/usr/local/bin/ssserver -c /etc/shadowsocks/config.json
  Restart=on-abort

  [Install]
  WantedBy=multi-user.target
  ```

- open tcp fastopen & bbr

  ```sh
  # append options
  echo -e "\nnet.ipv4.tcp_fastopen = 3\n\nnet.core.default_qdisc=fq\nnet.ipv4.tcp_congestion_control=bbr" >> /etc/sysctl.conf

  # save
  sysctl -p

  # checking
  lsmod | grep bbr
  ```
