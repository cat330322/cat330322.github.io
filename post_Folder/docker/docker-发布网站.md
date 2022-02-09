npm安装包

npm config set registry https://registry.npm.taobao.org

npm install yarn

yarn config set registry https://registry.npm.taobao.org/


yarn buid 打包

dist 替换服务器

docker build -t 20211202 .

FROM nginx

将dist文件中的内容复制到 /usr/share/nginx/html/ 这个目录下面

COPY dist/  /usr/share/nginx/html/ 

docker run --name=dockervue -d -p 8088:80 20211202