# Nice!!! Arch

## Installation

### [Download](https://archlinux.org/download)

- [USB Tool](https://rufus.akeo.ie)

### [Installation](https://wiki.archlinux.org/title/Installation_guide)

- [完整流程](https://zhuanlan.zhihu.com/p/596227524) _# 注意启动模式是否为 UEFI_

- 选择 _Arch Linux install medium_ 进入安装环境

  - 进入后可以使用 `passwd` 设置密码后用局域网 SSH 连接 `ssh root@ip.address`

- 连接 WIFI: `iwctl`

  - `station wlan0 show`
  - `station wlan0 connect SSID`

- 检查是否支持 UEFI: `efibootmgr`

#### After Chroot

- 添加新用户（见 Linux.md）

- 授权 sudo:

  ```sh
  # uncomment %wheel ALL=(ALL) ALL
  vim /etc/sudoers
  ```

- 语言:

  ```sh
  cat << EOF > /etc/locale.gen
  en_US.UTF-8 UTF-8
  zh_CN.UTF-8 UTF-8
  EOF
  locale-gen
  echo 'LANG=en_US.UTF-8' > /etc/locale.conf
  ```

- pacman 配置: `vim /etc/pacman.conf` _# uncomment Color and ParallelDownloads = 5_

- yay 安装:

  ```sh
  # 预先安装 base-devel
  git clone https://aur.archlinux.org/yay.git
  cd yay
  makepkg -si
  ```

#### 常用软件包

- chromium

  ```sh
  # /etc/environment, or ~/.xprofile add export
  GOOGLE_API_KEY=API 密钥的「键」
  GOOGLE_DEFAULT_CLIENT_ID=客户端 ID
  GOOGLE_DEFAULT_CLIENT_SECRET=客户端密钥
  ```

- dhcpcd: 分配 ip 地址
- [fcitx5](https://wiki.archlinux.org/title/Fcitx5) _# /etc/environment，配置快捷键时禁用 Settings > Keyboard > Typing_

  ```sh
  # /etc/environment, or ~/.xprofile add export
  GTK_IM_MODULE=fcitx
  QT_IM_MODULE=fcitx
  XMODIFIERS=@im=fcitx
  SDL_IM_MODULE=fcitx
  INPUT_METHOD=fcitx
  GLFW_IM_MODULE=ibus
  ```

- man-db man-pages: 软件包文档
- [nano](https://wiki.archlinux.org/title/nano)
- [shadowsocks-rust](https://wiki.archlinux.org/title/Shadowsocks)

```sh
pacman -S chromium dhcpcd fcitx5-chinese-addons fcitx5-im fcitx5-rime gedit git man-db man-pages nano noto-fonts noto-fonts-cjk noto-fonts-emoji openssh shadowsocks-rust tilix ttf-fira-code ttf-roboto ttf-roboto-mono ttf-sarasa-gothic ttf-ubuntu-font-family zip
```

```sh
# open in tilix

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

#### Gnome

- bae:

  - `pacman -S gnome gnome-tweaks`
  - `systemctl enable gdm.service`

- extensions

  - Arch Linux Updates Indicator: `pacman-contrib`
  - Blur my Shell
  - Caffeine
  - Clipboard Indicator
  - Launch new instance
  - Places Status Indicator

#### Theme

- icon: `numix-circle-icon-theme-git`
- cursor: `bibata-cursor-theme`

## [PAM](https://wiki.archlinux.org/title/PAM)

### [Fingerprint](https://wiki.archlinux.org/title/Fprint)

```sh
# /etc/pam.d/system-local-login
auth sufficient pam_fprintd.so

# /etc/pam.d/gdm-*
auth include system-local-login
```

### [Howdy](https://wiki.archlinux.org/title/Howdy)
