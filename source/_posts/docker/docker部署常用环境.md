---
title: docker部署常用环境
categories: docker
tags:
- Docker
toc: true
---

# docker安装Redis服务
```
docker run -d --restart=always --name redis -p 6379:6379
--requirepass "9db86db568f66753a9e1497a5e668ae7"
```

# docker安装Mysql服务
```
docker run -d --restart=always --name mysql 
-p 3306:3306 
-v /home/data/mysql/data:/var/lib/mysql 
-v /home/data/mysql/conf.d:/etc/mysql/conf.d 
-e MYSQL_ROOT_PASSWORD=Cdf1234~ mysql:latest
```

# docker安装minio
```
docker run 
--name minio 
-p 9000:9000 
-p 9999:9999 
-d --restart=always 
-e "MINIO_ROOT_USER=wetry" -e "MINIO_ROOT_PASSWORD=8f9efb0510324b258d566c091d5d6e57"
 -v /home/data/minio/data:/data 
 -v  /home/data/minio/config:/root/.minio 
 minio/minio:RELEASE.2023-05-18T00-05-36Z 
 server /data 
 --console-address ":9000" 
 -address ":9999"
```

# docker安装mongodb
```
docker run -d \
--name mongodb  \
-p 27017:27017 \
-v /home/data/mongo/data:/data/db \
-v /home/data/mongo/conf:/data/conf \
-v /home/data/mongo/log:/data/log \
-e MONGO_INITDB_ROOT_USERNAME=admin \
-e MONGO_INITDB_ROOT_PASSWORD=Cdf1234~ \
--privileged=true \
--restart always \
mongo:latest
```