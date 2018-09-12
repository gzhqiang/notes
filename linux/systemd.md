> 查阅 [archwiki](https://wiki.archlinux.org/index.php/Systemd_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)#systemd_.E5.9F.BA.E6.9C.AC.E5.B7.A5.E5.85.B7)
[廖雪峰](http://www.ruanyifeng.com/blog/2016/03/systemd-tutorial-commands.html)
1. 执行单元文件存放位置

```
/usr/lib/systemd/system/(软件包安装的单元) 和 /etc/systemd/system/(系统管理员安装的单元) 目录（后者优先级更高)
```

2. 常用命令

- 显示 系统状态：

```bash
systemctl status
```

- 输出激活的单元

```bash
systemctl 或者 systemctl list-units
```

- 输出运行失败的单元：

```bash
systemctl --failed
```

- 立即激活单元

```bash
systemctl start <单元>
```

- 立即停止单元

```bash
systemctl stop <单元>
```

- 重启单元

```bash
systemctl restart <单元>
```

- 重新加载配置

```bash
systemctl reload <单元>
```

- 输出单元运行状态

```bash
systemctl status <单元>
```

- 检查单元是否配置为自动启动

```bash
systemctl is-enabled <单元>
```

- 开机自动激活单元

```
systemctl enable <单元>
```

- 设置单元为自动启动并立即启动这个单元

```bash
systemctl enable --now unit
```

- 取消开机自动激活单元

```bash
systemctl disable <单元>
```

- 禁用一个单元（禁用后，间接启动也是不可能的）

```bash
systemctl mask <单元>
```

- 取消禁用一个单元

```bash
systemctl unmask <单元>
```

- 显示单元的手册页（必须由单元文件提供）

```bash
systemctl help <单元>
```

- 重新载入 systemd，扫描新的或有变动的单元：

```bash
systemctl daemon-reload
```

3. 电源管理

`参见wiki吧，不是重点!`

4. 编写单元文件

> 参照docker.service

```bash
[Unit]
Description=Docker Application Container Engine
Documentation=https://docs.docker.com
After=network-online.target docker.socket firewalld.service
Wants=network-online.target
Requires=docker.socket

[Service]
Type=notify
# the default is not to use systemd for cgroups because the delegate issues still
# exists and systemd currently does not support the cgroup feature set required
# for containers run by docker
ExecStart=/usr/bin/dockerd -H fd://
ExecReload=/bin/kill -s HUP $MAINPID
LimitNOFILE=1048576
# Having non-zero Limit*s causes performance problems due to accounting overhead
# in the kernel. We recommend using cgroups to do container-local accounting.
LimitNPROC=infinity
LimitCORE=infinity
# Uncomment TasksMax if your systemd version supports it.
# Only systemd 226 and above support this version.
#TasksMax=infinity
TimeoutStartSec=0
# set delegate yes so that systemd does not reset the cgroups of docker containers
Delegate=yes
# kill only the docker process, not all processes in the cgroup
KillMode=process
# restart the docker process if it exits prematurely
Restart=on-failure
StartLimitBurst=3
StartLimitInterval=60s

[Install]
WantedBy=multi-user.target
```

- 单元文件位置

```
可以通过 "systemctl show --property=UnitPath" 查看
```

- service type

```
Type=simple  : （默认值） systemd认为该服务将立即启动。服务进程不会 fork 。如果该服务要启动其他服务，
不要使用此类型启动，除非该服务是socket 激活型。
Type=forking ： systemd认为当该服务进程fork，且父进程退出后服务启动成功。对于常规的守护进程（daemon），
除非你确定此启动方式无法满足需求，使用此类型启动即可。使用此启动类型应同时指定 PIDFile=，以便 systemd 能够跟踪服务的主进程。
Type=oneshot ：这一选项适用于只执行一项任务、随后立即退出的服务。可能需要同时设置 RemainAfterExit=yes 使得 systemd 在服务进程退出之后仍然认为服务处于激活状态。
Type=notify ：与 Type=simple 相同，但约定服务会在就绪后向 systemd 发送一个信号。这一通知的实现由 libsystemd-daemon.so 提供。
Type=dbus ：若以此方式启动，当指定的 BusName 出现在DBus系统总线上时，systemd认为服务就绪。
Type=idle ：systemd会等待所有任务处理完成后，才开始执行 idle 类型的单元。其他行为与 Type=simple 类似。
```
