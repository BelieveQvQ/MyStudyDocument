# Docker Redis 安装及启动



## 第一步,从Docker Hub拉取Reids

```shell
# pull 从仓库中拉取
# latest 最新版本
docker pull redis:latest
```

## 第二步,在Linux上创建conf

关于Linux的文件或目录指令,可在该[链接](https://www.runoob.com/linux/linux-file-content-manage.html)中查询.

```shell
# 创建目录 -p 使用递归创建
mkdir /home/tigerhead/docker/redis/data -p
# 进入目录创建配置文件文件
cd /home/tigerhead/docker/redis/
touch redis.conf
# 删除目录及文件 -r 递归删除
rm /home/t1gerhead/redis -r
```

## 第三步,配置Redis.conf

关于Linux的vim的指令,可以在该[链接](https://www.runoob.com/linux/linux-vim.html)中查询.

```shell
# 使用vim打开Redis.conf文件
vim /home/tigerhead/docker/redis/redis.conf
# 使用键盘中的 i 进入文本编辑模式,进入编辑模式后左下角会出现 –INSERT- 

# 绑定IP,如果外网访问时,把他注释掉
bind 127.0.0.1
# 保护模式,当把bind(绑定的IP)注释掉后,需要把保护模式关闭
protected-mode no
# 开启数据持久化
appendonly yes
# 访问密码
requirepass 123456

# 使用键盘中的 : 进入vim的 ex命令模式
# 输入 wq 保存并退出 redis.conf ; w:保存 q:退出 q!:退出但不保存
```

## 第四步,启动Redis

```shell
# 运行一个镜像,新建一个容器
docker run 
# 容器的名称及端口映射 ; 服务器端口:Docker端口
--name myredis -p 6379:6379 
# 容器持久化数据目录映射 ; 自定义目录:容器中目录
-v /home/tigerhead/docker/redis/data:/data 
# Redis配置项文件映射 ; 自定义文件;容器中文件
-v /home/tigerhead/docker/redis/conf/redis.conf:/etc/redis/redis.conf 
# 使用配置文件启动Redis
-d redis redis-server /etc/redis/redis.conf

# 在每行代码后面加上 \ 即可美观的运行
docker run \
--name myredis -p 6379:6379 \
-v /home/tigerhead/docker/redis/data:/data \
-v /home/tigerhead/docker/redis/conf/redis.conf:/etc/redis/redis.conf \
-d redis redis-server /etc/redis/redis.conf
```

## 第五步,查看Redis运行状态

```shell
# 查看活跃的容器状态
docker ps
# 如果没有 myredis 说明启动失败 查看错误日志
docker logs myredis
# 查看 myredis 的 ip 挂载 端口映射等信息
docker inspect myredis
# 查看 myredis 的端口映射
docker port myredis
```

## 第六步,访问Redis

```shell
# 使用容器内部连接,随后输入设置的密码
docker exec -it myredis redis-cli
```

也可以使用外部的Redis管理工具:**Redis Desktop Manager**

## 附录

```bash
# 搜索镜像
docker search <image name>
# 拉取镜像
docker pull <image name>
# 查看本地镜像
docker images
# 查看已经创建的容器
docker ps -a
# 查看已经启动的容器
docker ps -s
# 运行一个容器实例
docker run <container name>
# 停止指定容器
docker stop <container tag>
# 删除指定容器
docker rm <container tag>
```