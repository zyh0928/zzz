## Directory Structure

- Root
  > e.g. D:\MyServer
  - [nginx](http://nginx.org/en/download.html "download")
  - [php](https://windows.php.net/download/ "download")
  - [mysql](https://dev.mysql.com/downloads/mysql/ "download")
  - www
  - start.bat
  - stop.bat
  - [RunHiddenConsole.exe](http://redmine.lighttpd.net/attachments/660/RunHiddenConsole.zip "download")

## Nginx-1.14.0

### Start

```sh
start nginx
# or
nginx.exe
```

### Stop

```sh
# 完整有序的停止 nginx，并保存相关信息
nginx.exe -s quit

# 快速停止 nginx，可能并不保存相关信息
nginx.exe -s stop
```

### Reload

```sh
nginx.exe -s reload
```

### Configuration file

> nginx/conf/nginx.conf

- 修改文件路径

  ```nginx
  location / {
      root  ../www;
      index  index.html  index.htm  index.php;
  }
  ```

- /scripts 改为 \$document_root

  > 若 root 无值或错误则报错：No input file specified

  ```nginx
  location ~ \.php$ {
      root  .\..\www;
      fastcgi_pass  127.0.0.1:9000;
      fastcgi_index  index.php;
      fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
      include  fastcgi_params;
  }
  ```

- 添加 index.php

  ```php
  <?php
  echo 'Hello World';
  phpinfo();
  ```

## PHP-7.2.12-NTS

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

## RunHiddenConsole

启动 PHP + Nginx

### start.bat

```sh
@echo off
set php_home=./php
set nginx_home=./nginx

echo Starting PHP FastCGI...
RunHiddenConsole %php_home%/php-cgi.exe -b 127.0.0.1:9000 -c %php_home%/php.ini

echo Starting Nginx...
RunHiddenConsole %nginx_home%/nginx.exe -p %nginx_home%
```

### stop.bat

```sh
@echo off
echo Stopping nginx...
taskkill /F /IM nginx.exe > nul

echo Stopping PHP FastCGI...
taskkill /F /IM php-cgi.exe > nul
exit
```

## MySQL-8.0.11

- 配置环境变量：MYSQL_HOME/bin
- 管理员模式打开命令行，进入 MySQL 根目录下的 bin 文件夹
- 初始化数据库：`‪mysqld --initialize`

  > 带随机密码

- 创建服务：`mysqld --install 服务名`

  > 默认服务名为 MySQL

- 启动 MySQL 服务：`net start mysql`
- 登录 MySQL：`mysql -uroot -p`

  > 随机密码被保存在错误日志里：MySQL 根目录/data/主机名.err

- 修改 root 密码：`ALTER USER 'root'@'localhost' IDENTIFIED BY '123456';`
