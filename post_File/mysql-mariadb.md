docker pull mysql
docker run \
    -p 3306:3306 \
    -e MYSQL_ROOT_PASSWORD=localDocker@mysql \
    -v /home/docker/mysql/data:/var/lib/mysql:rw \
    -v /home/docker/mysql/log:/var/log/mysql:rw \
    -v /home/docker/mysql/conf/my.cnf:/etc/mysql/my.cnf:rw \
    -v /home/docker/mysql/mysql-files:/var/lib/mysql-files/ \
    --name mysql \
    --restart=always \
    -d mysql


docker run -p 3306:3306 --name mysql02 -e MYSQL_ROOT_PASSWORD=123456 -d mysql：8.0

docker exec -it c4bf367b7155  bash 

mysql -uroot -p{密码}

mysql> ALTER USER 'root'@'%' IDENTIFIED WITH mysql_native_password BY 'root';

mysql> alter user 'root'@'%' identified by '123456';

mysql> flush privileges;

# 修改用户对应的密码

ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '123456';

# 刷新权限

flush privileges;


# 修改用户对应的密码

ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '123456';

# 刷新权限

flush privileges;

grant all privileges on *.* to 'root'@'%' with grant option;

flush privileges;