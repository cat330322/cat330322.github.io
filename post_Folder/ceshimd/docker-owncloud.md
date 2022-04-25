docker run --name owncloud-mysql -p 3000:3306 -e MYSQL\_ROOT\_PASSWORD=caixianjie -d mysql

docker run --name owncloud -p 80:80 --link owncloud-mysql:db -d  owncloud




docker run --name mysql -p 3000:3306-e MYSQL_ROOT_PASSWORD=root -d mysql:5.7

docker run --name owncloud --link mysql:mysql -d -p 80:80 owncloud


may nonean