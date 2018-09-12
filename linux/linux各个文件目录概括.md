1. / 

```
根目录, 整个文件树的开始。
```

2. /bin

```
可执行的程序, 单用户模式下也可以操作的命令。常用的比如ls, rm
```

3. /boot

```
包含系统启动的文件, Linux核心文件以及开机菜单所需配置文件。
```

4. /dev

```
设备文件, 通过df -h可以看出其不占硬盘空间, 说明其放在内存。
```

5. /etc

```
存放配置文件, 比如账号密码, 一般来说只可以看的哦, 只有root用户才可以修改的。 /etc/opt放置的事是第三方协力软件/opt的配置文件。
```

5. /home

```
用户主目录
```

6. /lib

```
包含一些必要的库(引入系统, 和根文件系统运行命令所需要的库), 开机用到的库, 以及在/bin或者/sbin下的适龄会调用的函数库。
```

7. /mnt

```
临时挂载点
```

8. /opt

```
第三方协力软件放置的目录。
```

9. /proc

```
提供正在运行进程和内核的消息(也可以查询内存, linux版本, CPU的信息)
```

10. /root

```
root用户
```

11. /sbin

```
跟/bin差不多, 但是这一般需要sudo才能运行, 普通用户不行。里面有很多指令是可以修复系统环境的, 但是只有root用户才能执行, 其它用户最多可以查询。
```

12. /sys

```
存放一些特有站点的数据.
```

13. /sys

```
This is a mount point for the sysfs filesystem, which provides information about the kernel like /proc, but better structured, following the formalism of kobject infrastructure.
```

14. /tmp

```
临时文件
```

15. /usr

```
This directory is usually mounted from a separate partition.  It should hold only shareable, read-only data, so that it can be mounted by various machines running Linux.
```

16. /media

```
放置的是可移除的设备。比如光盘, U盘等。
```

17. /run

```
系统开机产生的各项信息放置在这。早期是放置在/var/run目录下。
```

18. /srv

```
可以视为service的缩写, 跟网络服务有关。
```

19. /usr/bin

```
所有一般用户都能使用的命令 usr=unix software resource
```