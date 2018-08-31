# Nginx配置文件

1. user nginx(user) nginx(group)

```
定义用户和用户组, 用户组可以省略, 如果省略, 则用户组和用户想同。
```

2. worker_processes number

```
定义工作进程数, 最好等于cpu核数, 也可以配置auto(从1.3.8 and 1.2.5开始支持)。
```

3. error_log file [level]

```
配置log的文件路径, 第一个参数是文件路径, 第二个是级别, 默认是error
```

4. pip file

```
存储nginx进程号的文件。
```

5. events {...}

```
看官方解释这个
```

6. worker_connections number

```
设置一个进程能打开的最大连接数(并发数)
```