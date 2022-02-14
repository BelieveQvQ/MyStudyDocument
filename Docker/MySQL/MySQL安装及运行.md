# Docker MySQL 安装及运行



## 第一步,从Docker Hub 中拉取MySQL

```
docker pull mysql:latest
```

## 第二步,创建MySQL配置文件目录

## 运行

```shell
docker run -d -p 3306:3306 --name gwsql \
--network my-net \
-v /home/t1gerhead/gwsql/data:/var/lib/mysql \
-e MYSQL_ROOT_PASSWORD=2223246086 \
mysql
```

