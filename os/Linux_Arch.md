## Installation

### [Download](https://archlinux.org/download/)

- [USB Tool](https://rufus.akeo.ie/)

### [Installation](https://wiki.archlinux.org/title/Installation_guide)

- [完整流程](https://zhuanlan.zhihu.com/p/596227524) _#引导加载程序 GRUB_

- 选择 _Arch Linux install medium_ 进入安装环境

  - 进入后可以 `passwd` 设置密码后用局域网 SSH 连接 `ssh root@ip.address`

- 连接 WIFI

  - 查看网络接口: `ip link`
  - 进入交互式提示符，配置并连接到互联网: `iwctl`
  - （可选）取消禁用 wifi 设备: `rfkill unblock wifi`
  - （可选）开启设备: `ip link set <dev name>`

    ```sh
    station wlan0 show
    # station wlan0 scan
    # station wlan0 get-networks
    station wlan0 connect <network name>
    exit
    ```

- btrfs

  - p1: `mkfs.fat -F 32 /dev/p1` _# EFI System_
  - p2: `mkfs.btrfs /dev/p2` _# Linux filesystem_

    ```sh
    mount /dev/p2 /mnt &&
    btrfs subvolume create /mnt/@ &&
    btrfs subvolume create /mnt/@home &&
    btrfs subvolume create /mnt/@logs &&
    btrfs subvolume create /mnt/@pkgs &&
    umount /mnt

    ROOT_PART=p2 &&
    mount -o compress=zstd:3,subvol=@ /dev/$ROOT_PART /mnt &&
    mkdir -p /mnt/{boot,home,var/log,var/cache/pacman/pkg}  &&
    mount -o compress=zstd:3,subvol=@home /dev/$ROOT_PART /mnt/home &&
    mount -o compress=zstd:3,subvol=@logs /dev/$ROOT_PART /mnt/var/log &&
    mount -o compress=zstd:3,subvol=@pkgs /dev/$ROOT_PART /mnt/var/cache/pacman/pkg

    mount /dev/p1 /mnt/boot
    ```

- `pacstrap /mnt base base-devel linux linux-firmware linux-headers sof-firmware`

- ```sh
  pacman -S vim nano reflector

  ## 获取pacman镜像源
  reflector -c China -a 10 --sort rate --save /etc/pacman.d/mirrorlist
  ## 查看是否有edu.cn的链接信息
  cat /etc/pacman.d/mirrorlist
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

## Get Started

```sh
# install yay
# /etc/pacman.conf  end
[archlinuxcn]
Server = https://mirrors.tuna.tsinghua.edu.cn/archlinuxcn/$arch

sudo pacman -Syu
sudo pacman -S archlinuxcn-keyring

sudo pacman -S yay

sudo pacman -Rs archlinuxcn-keyring
# remove pacman.conf end
```

### 常用软件包

- chromium

  ```sh
  # ~/.xprofile

  export GOOGLE_API_KEY=API 密钥的「键」
  export GOOGLE_DEFAULT_CLIENT_ID=客户端 ID
  export GOOGLE_DEFAULT_CLIENT_SECRET=客户端密钥
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
- [shadowsocks-libev](https://wiki.archlinux.org/title/Shadowsocks)

```txt
chromium dhcpcd gedit git fcitx5-im fcitx5-chinese-addons fcitx5-rime man-db man-pages nano noto-fonts noto-fonts-cjk noto-fonts-emoji openssh shadowsocks-libev tilix ttf-fira-code ttf-roboto ttf-roboto-mono ttf-sarasa-gothic ttf-ubuntu-font-family zip
```

### Gnome

- bae:

  - `yay -S gnome gnome-tweaks gnome-tweak-tool`
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
  - Workspace Indicator`

### Theme

- icon: `numix-circle-icon-theme-git`
- cursor: `bibata-cursor-theme`
- gtk: `numix-gtk-theme`

## [PAM](https://wiki.archlinux.org/title/PAM)

### [Fingerprint](https://wiki.archlinux.org/title/Fprint)

### [Howdy](https://wiki.archlinux.org/title/Howdy)
