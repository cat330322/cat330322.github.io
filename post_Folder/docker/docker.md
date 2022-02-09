利用docker commit新构镜像

1、停止docker容器

docker stop container01

2、commit该docker容器

docker commit container01 new_image:tag

3、用前一步新生成的镜像重新起一个容器

docker run --name container02 -p 80:80 new_image:tag