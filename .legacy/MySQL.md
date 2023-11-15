## Install on Linux

## Install on Windows

- 配置环境变量：MYSQL_HOME/bin
- 管理员模式打开命令行，进入 MySQL 根目录下的 bin 文件夹
- 初始化数据库：`mysqld --initialize`

  > 带随机密码

- 创建服务：`mysqld --install 服务名`

  > 默认服务名为 MySQL

- 启动 MySQL 服务：`net start mysql`
- 登录 MySQL：`mysql -uroot -p`

  > 随机密码被保存在错误日志里：MySQL 根目录/data/主机名.err

- 修改 root 密码：`ALTER USER 'root'@'localhost' IDENTIFIED BY '123456';`

## Encode

- set character_set_client = utf8mb4;
- set character_set_connection = utf8mb4;
- set character_set_database = utf8mb4;
- set character_set_results = utf8mb4;
- set character_set_server = utf8mb4;

```sh
mysql> show variables like '%char%';
+--------------------------+----------------------------------+
| Variable_name            | Value                            |
+--------------------------+----------------------------------+
| character_set_client     | utf8mb4                          |
| character_set_connection | utf8mb4                          |
| character_set_database   | utf8mb4                          |
| character_set_filesystem | binary                           |
| character_set_results    | utf8mb4                          |
| character_set_server     | utf8mb4                          |
| character_set_system     | utf8                             |
| character_sets_dir       | user\local\mysql\share\charsets\ |
+--------------------------+----------------------------------+
```

## Link

- [**MySQL**](https://www.mysql.com/)
- [**Download**](https://dev.mysql.com/downloads/mysql/)
