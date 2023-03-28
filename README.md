### Redis实战 示例源码

#### Redis服务器安装

- Ubuntu20.04 安装redis-server

    ```
    $ sudo apt-get install redis-server
    ```

- 查看redis-server进程

    ```
    $ ps aux | grep redis
    或者
    $ ps -eaf | grep redis
    ```

- 查看Redis服务器状态

    ```
    $ systemctl status redis.service
    或者
    $ sudo /etc/init.d/redis-server status
    ```

#### Redis服务器基本配置 

配置文件为/etc/redis/redis.conf 

- 开启Redis的远程连接

    ```
    $ vim /etc/redis/redis.conf 
    注释掉绑定地址#bind 127.0.0.1
    ```

- 修改Redis的默认端口

    ```
    $ vim /etc/redis/redis.conf 
    port 6379
    ```

    数据文件存储路径为/var/lib/redis

    配置完成后重新启动服务器

    ```
    $ sudo /etc/init.d/redis-server restart or
    $ sudo service redis-server restart or
    $ sudo redis-server /etc/redis/redis.conf
    ```
    或者
    ```
    $ sudo systemctl restart redis.service
    ```

#### 启动客户端

安装Redis服务器，会自动地一起安装Redis命令行客户端程序。命令行输入 redis-cli 

    ```
    $ redis-cli -h host -p port -a password
    ```

#### Docker安装Redis

- 取最新版的 Redis 镜像

    拉取官方的最新版本的镜像：
    ```
    $ docker pull redis:latest
    latest: Pulling from library/redis
    f1f26f570256: Pull complete
    8a1809b0503d: Pull complete
    d792b14d05f9: Pull complete
    ad29eaf93bf6: Pull complete
    7cda84ccdb33: Pull complete
    95f837a5984d: Pull complete
    Digest: sha256:7b83a0167532d4320a87246a815a134e19e31504d85e8e55f0bb5bb9edf70448
    Status: Downloaded newer image for redis:latest
    docker.io/library/redis:latest
    ```

- 查看本地镜像 

    使用以下命令来查看是否已安装了 redis：
    ```
    $ docker images
    REPOSITORY                    TAG                   IMAGE ID       CREATED         SIZE
    redis                         latest                31f08b90668e   5 days ago      117MB
    ```

- 运行容器

    安装完成后，我们可以使用以下命令来运行 redis 容器：
    ```
    $ docker run -itd --name redis-test -p 6379:6379 redis
    # -p 6379:6379：映射容器服务的 6379 端口到宿主机的 6379 端口。外部可以直接通过宿主机ip:6379 访问到 Redis 的服务。
    ```

- 安装成功

    我们可以通过 docker ps 命令查看容器的运行信息：
    ```
    $ docker ps
    CONTAINER ID   IMAGE               COMMAND                  CREATED              STATUS              PORTS                                       NAMES
    52453bec297e   redis               "docker-entrypoint.s…"   About a minute ago   Up About a minute   0.0.0.0:6379->6379/tcp, :::6379->6379/tcp   redis-test
    ```

    接着我们通过 redis-cli 连接测试使用 redis 服务。
    ```
    $ docker exec -it redis-test /bin/bash
    root@52453bec297e:/data# redis-cli
    127.0.0.1:6379> set test 1
    OK
    127.0.0.1:6379>
    root@52453bec297e:/data#
    exit
    ```

#### 参考资料

- Redis菜鸟教程 <https://www.runoob.com/redis/redis-tutorial.html>
- Docker 安装 Redis <https://www.runoob.com/docker/docker-install-redis.html>

![封面](cover.jpg)

