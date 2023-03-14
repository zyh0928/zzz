## Tip

- Port forwarding: `ssh -R [listening_host:]listening_port:host:hostport user@host`

  ```sh
  ssh -R 12345:localhost:22 root@192.168.X.X
  ```

- 电脑固件更新管理

  ```sh
  # 安装固件管理软件包
  pacman -S fwupd
  # 查看电脑相关硬件设备
  fwupdmgr get-devices
  # 刷新设备版本状态
  fwupdmgr refresh --force
  # 获取更新
  fwupdmgr get-updates
  # 安装更新
  fwupdmgr update
  ```

## Command

### User

- 创建用户:

  - `useradd -m <user_name> -G wheel`
  - `passwd <user_name>`
  - `visudo` _取消注释 %wheel ALL=(ALL) NOPASSWD: ALL_

- 用户改名:

- 删除用户: `userdel -fr <user_name>`
