## Install on Windows

- [下载 Ruby](https://rubyinstaller.org/downloads/)
  > mac 下自带 Ruby
- 安装过程中请注意勾选 **Add Ruby executables to your PATH** 添加到系统环境变量
- 安装完成后需测试安装有没有成功,运行 CMD 输入以下命令：

  ```sh
  ruby -v

  # 如安装成功会打印
  # ruby 2.5.1p57 (2018-03-29 revision 63029) [x64-mingw32]
  ```

- 更换 gem 源

  ```sh
  # 删除原 gem 源
  gem sources --remove https://rubygems.org/

  # 添加国内淘宝源
  gem sources -a https://ruby.taobao.org/

  # 打印是否替换成功
  gem sources -l

  # 更换成功后打印如下
  # *** CURRENT SOURCES ***
  # https://ruby.taobao.org/
  ```

## RubyGems

Ruby 自带一个叫做 RubyGems 的系统，用来安装基于 Ruby 的软件

### Command

- 安装：`gem install <module-name>`

  ```sh
  # 若 mac 安装遇到权限问题需加 sudo gem install sass
  gem install sass
  gem install compass
  gem install haml
  ```

- 更新：`gem update <module-name>`

  ```sh
  # 更新 sass
  gem update sass
  ```

- 查看版本：`<module-name> -v`

  ```sh
  # 查看 sass 版本
  sass -v
  ```

- 查处帮助：`<module-name> -h`

  ```sh
  # 查看 sass 帮助
  sass -h
  ```

## Link

- [**Ruby**](https://rubyinstaller.org/)
