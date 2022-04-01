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


- Redis菜鸟教程 <https://www.runoob.com/redis/redis-tutorial.html>

![封面](cover.jpg)

