Alpine源配置文件

/ # cat /etc/apk/repositories 

http://dl-cdn.alpinelinux.org/alpine/v3.11/main

http://dl-cdn.alpinelinux.org/alpine/v3.11/community

/ # cat /etc/apk/repositories 

https://mirrors.aliyun.com/alpine/v3.6/main/

https://mirrors.aliyun.com/alpine/v3.6/community/


/ # apk search curl

/ # apk add curl

/ # apk del curl

FROM alpine

RUN echo "https://mirrors.aliyun.com/alpine/v3.6/main/" > /etc/apk/repositories; \

    echo "https://mirrors.aliyun.com/alpine/v3.6/community/" >> /etc/apk/repositories; \
    
    apk add curl