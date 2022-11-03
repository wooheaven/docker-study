```bash
$ docker pull mysql

$ docker images | grep mysql
mysql                      latest                      c2c2eba5ae85   7 days ago      535MB

$ docker run --name mysql-container -e MYSQL_ROOT_PASSWORD=12qwas -d -p 3306:3306 mysql:latest
66d6d100a891eee8a22393a03c231eb61bd7616a4275c974809237e509d422a5

$ docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS          PORTS                                                  NAMES
66d6d100a891   mysql:latest   "docker-entrypoint.s…"   23 seconds ago   Up 21 seconds   0.0.0.0:3306->3306/tcp, :::3306->3306/tcp, 33060/tcp   mysql-container

$ docker exec -it mysql-container bash

bash-4.4# mysql -u root -p       
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 9
Server version: 8.0.31 MySQL Community Server - GPL

Copyright (c) 2000, 2022, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show databases ;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
4 rows in set (0.00 sec)
```
