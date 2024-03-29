## Command

```sh
# create user, host use % to create a user connected from any computer
CREATE USER username@host IDENTIFIED BY password;

# update user password
ALTER USER username@host IDENTIFIED BY password;

# refresh the MySQL system permission table
FLUSH PRIVILEGES;

# grant permissions to the MySQL user account
GRANT ALL PRIVILEGES ON database.* TO username@host;
GRANT permission1, permission2 ON database_name.table_name TO username@host;
```

## Install on Ubuntu

- add mysql apt repository

  ```sh
  # downloading the repository package
  wget https://repo.mysql.com//mysql-apt-config_0.8.13-1_all.deb

  # install the MySQL repository package
  sudo dpkg -i mysql-apt-config_0.8.13-1_all.deb
  ```

- install mysql server

  ```sh
  # update package database
  sudo apt update

  # install packages for the MySQL community server
  sudo apt install mysql-server
  ```

- enter a password for the root
- authentication plugin >> 2
- secure mysql server installation

  ```sh
  sudo mysql_secure_installation
  ```

- managing mysql server via systemd

  ```sh
  # check MySQL server
  systemctl status mysql
  # auto started
  sudo systemctl enable mysql
  ```

- install extra mysql products and components(Optional, GUI)

  ```sh
  sudo apt update
  sudo apt install mysql-workbench-community libmysqlclient18
  ```
