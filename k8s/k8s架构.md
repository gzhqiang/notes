# Cluster

```
计算，存储和网络资源的集合，k8s利用这些资源运行各种基于容器的应用。
```

# Master

```
Cluster的大脑，负责调度。
```

# Node

```
运行容器应用，Node由Master管理。
```

# Pod

```
Pod是k8s工作的最小单元。每个Pod包含一个或多个容器。

重点:
1. 好管理
把多个容器抽象在一起，封装在一个部署单元中。k8s已Pod为最小单位进行调度、扩展、共享资源、管理生命周期等。
2. 通信和资源共享
Pod中所有容器使用一个网络namespace，即相同的IP和Port。他们可以直接用localhost通信
```

# Controller

```
管理Pod
```

# Service

```
定义外界访问一组特定Pod的方式。
```

# namespace

```

```