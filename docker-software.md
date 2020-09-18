
# docker software

docker 作为独立的虚拟机, 可以承载各类系统软件, 安装提供服务的软件使用docker目前是最高效的方式

docker 把每一个非运行时的虚拟机封装为一个个独立的镜像, 每一个镜像启动后, 变为容器.

同一个镜像创建的容器之间相互独立, 不存在冲突.

可以简单的认为 镜像 <==> 类;容器 <==> 对象

## docker安装

### ubuntu-docker最新版

https://docs.docker.com/install/linux/docker-ce/ubuntu/

### docker国内源设置

https://www.docker-cn.com/registry-mirror

```
sudo gedit /etc/docker/daemon.json
```
```
{
  "registry-mirrors": ["https://registry.docker-cn.com"]
}
```
```
service docker restart
```

## docker 命令
```
# 搜索docker
docker search <镜像名>
# 下载docker
docker pull <镜像名>
# 查看镜像
docker images
# 第一次启动镜像
docker run [参数] <镜像名>
# 关闭
docker stop <容器id/容器名>
# 启动（已经存在容器）
docker start <容器id/容器名>
# 查看运行容器
docker ps
# 查看所有容器
docker ps -a
# 进入docker
sudo docker exec -it <name> /bin/bash
```
**docker run参数**

- -p 端口映射 本地端口:容器端口
- -v 路径映射 本地路径:容器路径
- -e 创建时各个镜像需要独立配置的参数
- -d 设置为守护进程, 在退出docker 后仍然在后台运行
- --name docker容器名字

## 使用 docker 安装 服务软件

### mysql
```
docker run -p 3306:3306 -e MYSQL_ROOT_PASSWORD=passwd --name mysql -d mysql
```
**开启远程**
https://blog.csdn.net/xinpengfei521/article/details/80403965

### redis

```
docker run -p 6379:6379 --name redis  -d redis redis-server --appendonly yes
```
- redis-server --appendonly yes : 在容器执行redis-server启动命令，并打开redis持久化配置

### mongodb
```
docker run -p 27017:27017 --name mongo -d mongo
```

### elasticsearch 以及 kibana
必须先开elasticsearch再开kibana
```
docker run -p 9200:9200 -p 9300:9300 --name elasticsearch -d elasticsearch

docker run --link elasticsearch:elasticsearch -p 5601:5601 -d kibana --name kibana
```

### rabbitmq
```
docker run -d --name rabbitmq --publish 5671:5671 \
 --publish 5672:5672 \
 --publish 4369:4369 \
 --publish 25672:25672 \
 --publish 15671:15671 \
 --publish 15672:15672 \
 --hostname myRabbit \
 -e RABBITMQ_DEFAULT_VHOST=my_vhost \
 -e RABBITMQ_DEFAULT_USER=root \
 -e RABBITMQ_DEFAULT_PASS=arron1024 \
rabbitmq:management
```

### zookeeper
```
docker run --privileged=true -d --name zookeeper -p 2181:2181  -d zookeeper
```
### minio
```
docker run -d --name minio -p 9000:9000 minio/minio server /data
```