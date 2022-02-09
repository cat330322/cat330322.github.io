docker-compose      # 拉取镜像

docker-compose up -d nginx     # 运行nginx容器

docker-compose up -d     # 运行所有容器

docker-compose ps     # 查看容器运行状态

docker-compose down     # 停止容器和容器网络

docker-compose rm nginx     # 删除nginx容器

version: '3.1'
services:

    nginx:

        image: nginx     # 镜像名称

        container_name: nginx     # 容器名字

        restart: always     # 开机自动重启

        ports:     # 端口号绑定（宿主机:容器内）

            - '80:80'

            - '443:443'

        volumes:      # 目录映射（宿主机:容器内）

            - ./conf/nginx.conf:/etc/nginx/nginx.conf

            - ./conf.d:/etc/nginx/conf.d

            - ./html:/usr/share/nginx/html


docker-compose -f docker-compose-portainer.yml -p portainer up -d

-p：项目名称

-f：指定docker-compose.yml文件路径

-d：后台启动

MySQL

5.7

docker-compose -f docker-compose-mysql5.7.yml -p mysql5.7 up -d

8.0

docker-compose -f docker-compose-mysql8.0.yml -p mysql8.0 up -d