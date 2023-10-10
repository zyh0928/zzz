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

  ```sh
  # add user
  useradd -m <user_name> -G wheel
  # set password
  passwd <user_name>
  # uncomment %wheel ALL=(ALL) ALL
  visudo
  ```

- 用户改名:

  ```sh
  pkill -u <old_name>

  pkill -9 -u <old_name>

  usermod -l <new_name> -d /home/<new_name> [-u <new_uid_9999>] -m <old_name>

  groupmod -n <new_name> [-g <new_gid_9999>] <old_name>
  ```

- 删除用户: `userdel -fr <user_name>`
