## Tip

- Port forwarding: `ssh -R [listening_host:]listening_port:host:hostport user@host`

  ```sh
  ssh -R 12345:localhost:22 root@192.168.X.X
  ```

## Install Arch

### [Download](https://archlinux.org/download/)

### [Installation](https://wiki.archlinux.org/title/Installation_guide)

- 选择 _Arch Linux install medium_ 进入安装环境

  - 进入后可以 `passwd` 设置密码后用局域网 SSH 连接 `ssh root@ip.address`

- 创建分区表和分区: `fdisk /dev/sda`

  - `n`: Partition number: default, First sector: default, Last sector: +1G
  - `n`: All: default
  - `w`

## Install Ubuntu

## Command

```sh
# Remove the user
userdel -fr <username>
```
