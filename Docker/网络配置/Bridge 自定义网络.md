docker run 默认会链接 docker0网络(容器之间互相隔离)

如果想要容器互相连接,就需要自己新建一个Bridge 在run是连接了.



```
# 查看所有网络类型 默认会有3个 Bridge/host/nono
docker network ls

# 创建一个 name:my-net state:bridge的网络
docker network create my-net

# 在容器run添加 使容器连接该网络
--network my-net

```

