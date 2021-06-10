redis
---

docker run -itd --name redis1 -p 6379:6379 redis

/etc/init.d/redis-server restart

redis-cli -a abc

redis-cli -h 127.0.0.1 -p 6379
