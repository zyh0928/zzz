## Install on Windows

### Install Composer

- 配置环境变量：**PHP_HOME**
- [composer.phar](https://getcomposer.org/download/ "download")：放入 PHP 根目录
- PHP 根目录下创建 **composer.bat**

  ```sh
  @php "%~dp0composer.phar" %*
  ```

- Test

  ```sh
  # 以管理员身份运行
  composer
  ```

- Set Composer proxy

  ```sh
  set http_proxy=http://127.0.0.1:9099 # Windows 或直接设置环境变量
  export http_proxy=http://127.0.0.1:9099 # Linux or Mac OS
  ```

- Change Composer source

  ```sh
  # default source: https://repo.packagist.org
  composer config -g repo.packagist composer https://packagist.phpcomposer.com
  ```

### Modify php.ini

> 注意去除注释「;」

- extension_dir = "./ext"
- date.timezone = Asia/Shanghai
- enable_dl = On
- cgi.force_redirect = 0
- cgi.fix_pathinfo = 1
- fastcgi.impersonate = 1
- cgi.rfc2616_headers = 1
- extension = mysqli
- extension = pdo_mysql
- extension = openssl
- extension = mbstring

### [RunHiddenConsole](http://redmine.lighttpd.net/attachments/660/RunHiddenConsole.zip "download")

- start.bat

  ```sh
  @echo off
  set php_home=./php

  echo Starting PHP FastCGI...
  RunHiddenConsole %php_home%/php-cgi.exe -b 127.0.0.1:9000 -c  %php_home%/php.ini
  ```

- stop.bat

  ```sh
  @echo off

  echo Stopping PHP FastCGI...
  taskkill /F /IM php-cgi.exe > nul
  exit
  ```
