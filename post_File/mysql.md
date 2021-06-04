mysql

---

sudo docker run -p 3306:3306 --name mysql -e MYSQL_ROOT_PASSWORD=xx -d mysql:5.7

mysql -h 127.0.0.1 -uroot -p123456

mysql> use mysql;

mysql> show databases;

sudo docker exec -it mysql bash

mysql -uroot -p123456