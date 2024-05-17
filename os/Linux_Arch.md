# Nice!!! Arch

## Installation

### [Download](https://archlinux.org/download)

- [USB Tool](https://rufus.akeo.ie)

### [Installation](https://wiki.archlinux.org/title/Installation_guide)

- [完整流程](https://zhuanlan.zhihu.com/p/596227524) _# 引导加载程序 GRUB_

- 选择 _Arch Linux install medium_ 进入安装环境

  - 进入后可以 `passwd` 设置密码后用局域网 SSH 连接 `ssh root@ip.address`

- 连接 WIFI: `iwctl`

  - `station wlan0 show`
  - `station wlan0 connect SSID`

- fdisk

  - `fdisk -l`
  - `fdisk /dev/<name>`

    ```sh
    p # 分区列表
    d # 删除分区
    n # 新建分区
    w # 保存退出
    ```

  _# 如果硬盘是 nvme0n1，name 就要写为 nvme0n1，清空分区后新建两个分区，后面的 p1 就要写成 nvme0n1p1_

- btrfs

  - p1: `mkfs.fat -F 32 /dev/nvme0n1p1` _# EFI System_
  - p2: `mkfs.btrfs /dev/nvme0n1p2` _# Linux filesystem_

    ```sh
    mount /dev/nvme0n1p2 /mnt &&
    btrfs subvolume create /mnt/@ &&
    btrfs subvolume create /mnt/@home &&
    btrfs subvolume create /mnt/@logs &&
    btrfs subvolume create /mnt/@pkgs &&
    umount /mnt

    ROOT=nvme0n1p2 &&
    mount -o compress=zstd:3,subvol=@ /dev/$ROOT /mnt &&
    mkdir -p /mnt/{boot,home,var/log,var/cache/pacman/pkg}  &&
    mount -o compress=zstd:3,subvol=@home /dev/$ROOT /mnt/home &&
    mount -o compress=zstd:3,subvol=@logs /dev/$ROOT /mnt/var/log &&
    mount -o compress=zstd:3,subvol=@pkgs /dev/$ROOT /mnt/var/cache/pacman/pkg

    mount /dev/nvme0n1p1 /mnt/boot
    ```

- ```sh
  # 获取pacman镜像源
  reflector -p https -c China --delay 3 --completion-percent 95 --sort rate --save /etc/pacman.d/mirrorlist
  # 查看是否有edu.cn的链接信息
  cat /etc/pacman.d/mirrorlist
  ```

- `pacstrap -K /mnt base linux linux-firmware sof-firmware`

- fstab: `genfstab -U /mnt >> /mnt/etc/fstab` _# cat /mnt/etc/fstab_

- 切换到新系统: `arch-chroot /mnt`

- 时区:

  ```sh
  # 输入 /usr/share/zoneinfo/ 之后按下Tab键查看可选的时区
  ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
  # 硬件时间
  hwclock --systohc
  ```

- pacman 配置: `vim /etc/pacman.conf` _# uncomment Color and ParallelDownloads = 5_

- 语言:

  ```sh
  cat << EOF > /etc/locale.gen
  en_US.UTF-8 UTF-8
  zh_CN.UTF-8 UTF-8
  EOF
  locale-gen
  echo 'LANG=en_US.UTF-8' > /etc/locale.conf
  ```

- **之后参考教程**

### 常用软件包

- chromium

  ```sh
  # /etc/environment
  GOOGLE_API_KEY=API 密钥的「键」
  GOOGLE_DEFAULT_CLIENT_ID=客户端 ID
  GOOGLE_DEFAULT_CLIENT_SECRET=客户端密钥
  ```

- dhcpcd: 分配 ip 地址
- [fcitx5](https://wiki.archlinux.org/title/Fcitx5)

  ```sh
  # /etc/environment
  GTK_IM_MODULE=fcitx
  QT_IM_MODULE=fcitx
  XMODIFIERS=@im=fcitx
  INPUT_METHOD=fcitx
  SDL_IM_MODULE=fcitx
  GLFW_IM_MODULE=ibus
  ```

- man-db man-pages: 软件包文档
- [nano](https://wiki.archlinux.org/title/nano)
- [shadowsocks-rust](https://wiki.archlinux.org/title/Shadowsocks)

  ```txt
  chromium dhcpcd fcitx5-chinese-addons fcitx5-im fcitx5-rime gedit git man-db man-pages nano noto-fonts noto-fonts-cjk noto-fonts-emoji openssh shadowsocks-rust tilix ttf-fira-code ttf-roboto ttf-roboto-mono ttf-sarasa-gothic ttf-ubuntu-font-family zip
  ```

- open in tilix

  ```sh
  pacman -S python-nautilus

  # ~/.local/share/applications/open-pantheon-terminal-here.desktop
  [Desktop Entry]
  Name=Terminal
  TryExec=tilix
  Exec=tilix -w %u
  Icon=utilities-terminal
  Type=Application
  StartupNotify=true
  X-GNOME-Gettext-Domain=tilix
  NoDisplay=true
  MimeType=inode/directory;
  Name[en_US]=Terminal
  X-GNOME-FullName[en_US]=Terminal
  Comment[en_US]=
  Path=
  Terminal=false
  X-GNOME-UsesNotifications=false
  Categories=Other;
  ```

### Gnome

- bae:

  - `gnome gnome-extra`
  - `systemctl enable gdm.service`

- extensions

  - Arch Linux Updates Indicator - `pacman-contrib`
  - Blur my Shell
  - Caffeine
  - Clipboard Indicator
  - Dash to Dock
  - Launch new instance
  - Places Status Indicator
  - Screenshot Tool
  - Top Bar Organizer
  - Unite
  - User Themes
  - Workspace Indicator

### Theme

- icon: `numix-circle-icon-theme-git`
- cursor: `bibata-cursor-theme`
- gtk: `numix-gtk-theme`

## [PAM](https://wiki.archlinux.org/title/PAM)

### [Fingerprint](https://wiki.archlinux.org/title/Fprint)

```sh
# /etc/pam.d/system-local-login
auth sufficient pam_fprintd.so

# /etc/pam.d/gdm-*
auth include system-local-login
```

### [Howdy](https://wiki.archlinux.org/title/Howdy)
