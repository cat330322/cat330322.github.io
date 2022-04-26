# Registry

## 启动

docker run -d -p 5000:5000 --restart=always --name registry registry:2

关闭并删除容器

docker stop registry

docker rm registry

## 查看registry当前仓库的镜像

curl http://10.10.1.45:5000/v2/_catalog

## 添加tag

docker tag nginx:1.19.4 localhost:5000/my-nginx

## 推送到本地仓库

docker push localhost:5000/my-nginx

## 删除本地缓存

docker image remove nginx:1.19.4
docker image remove localhost:5000/my-nginx

## 本地仓库拉取

docker pull localhost:5000/my-nginx
