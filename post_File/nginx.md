nginx

---

临时生效

ulimit  -n 10240

echo 10240 > /proc/sys/net/core/somaxconn

echo 0 > /proc/sys/net/ipv4/tcp_syncookies

echo 1 > /proc/sys/net/ipv4/tcp_tw_reuse

永久生效

vi /etc/security/limits.conf

root soft nofile 10240

root hard nofile 10240

vi /etc/sysctl.conf

net.core.somaxconn=10240

net.ipv4.tcp_syncookies=0

net.ipv4.tcp_tw_reuse=1

二、nginx配置优化

worker_processes  4;

worker_connections  10240;

三、测试

ab -c 10000 -n 10000 http://www.you-nginx-ip.com

四、http和https的性能区别

HTTP耗时 = TCP握手(需要１个RTT)

HTTPs耗时 = TCP握手 + SSL握手(需要多个RTT，下面例子是７个).

再加上https有加密解密环节，所以，访问https站点的实际的tps要比http站点少很多。比较来说如果http站点的tps有4000的话，可能https站点的tps就只有800左右。