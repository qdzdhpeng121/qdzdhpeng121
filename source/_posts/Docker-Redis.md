---
title:  Docker-Redis
date: 2021-06-14 14:25:00
tags:
---

## Docker安装redis
docker pull redis  
mkdir -p redis-mount/{conf,data}
wget http://download.redis.io/redis-stable/redis.conf
### 修改配置文件
bind 将这个注释掉，保证redis可以远程访问  
requirepass 设置密码  
daemonize 这个要注释掉，不然docker容器起不来  
appendonly 用于开启AOF（Append-only file）默认是no，如果想开启，改成yes即可
### 启动redis
docker run -d -p 6379:6379 \
-v $PWD/conf/redis.conf:/etc/redis/redis.conf \
-v $PWD/data:/data --name redis-server-master \
--restart=always \
--privileged=true \
redis redis-server /etc/redis/redis.conf
### 测试连接
docker exec -it redis-server-master redis-cli -a {密码}