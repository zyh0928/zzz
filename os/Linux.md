## Tip

- Port forwarding: `ssh -R [listening_host:]listening_port:host:hostport user@host`

  ```sh
  ssh -R 12345:localhost:22 root@192.168.X.X
  ```

## Install Arch

- 转发端口
- Erase SSD
- 创建分区表和分区
- 格式化并挂载根分区
- 安装 `filesystem`
- 格式化并挂载/boot
- 安装 `linux`
- 格式化并挂载 efi 分区
- 安装 `linux`

## Install Ubuntu

## Command

```sh
# Remove the user
userdel -fr <username>
```
