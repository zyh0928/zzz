# Nice!!! Linux

## Tip

- Remote Port Forwarding:

  ```sh
  # ssh -R remote_port:localhost:local_port ssh_server_hostname
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
  useradd -m -G wheel <user_name>
  # set password
  passwd <user_name>
  # uncomment %wheel ALL=(ALL) ALL
  vim /etc/sudoers
  ```

- 用户改名:

  ```sh
  pkill -u <old_name>
  pkill -9 -u <old_name>
  usermod -l <new_name> -d /home/<new_name> [-u <new_uid>] -m <old_name>
  groupmod -n <new_name> [-g <new_gid>] <old_name>
  ```

- 删除用户: `userdel -fr <user_name>`
