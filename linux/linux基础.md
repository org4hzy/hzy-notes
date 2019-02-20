# linux运维基础

* 计算机信息
```s
uname -a
watch -n 1 uptime
```

* 账号管理
```s
账号配置  /etc/passwd  /etc/group /etc/shadow
在 tty1登录，root用户需要设置密码，更新密码命令 passwd。
新增用户:	useradd user_a;	设置密码 passwd user_a
```

* 防火墙 增加远程端口访问权限
```s
systemctl start/stop/enable/disable firewall 检测防火墙状态
firewall-cmd --permanent --add-port=22/tcp
firewall-cmd --reload
firewall-cmd --state
```

* 系统服务 [ daemons 守护进程]
```s
systemd 进程
systemctl 命令控制服务
服务脚本的文档 
/etc/systemd/system
```

* 日报服务 journalctl
```s
journalctl -u ngnix.service -f 查看ngnix服务日报.
journalctl -h 帮助
```

********************************* 

* linux 安装sshd服务
```text
ubuntu  : apt install openssh-server

* 查看sshd 服务状态 service sshd status .
用MobaXterm root登录，需要修改sshd的配置.

vim  etc/ssh/sshd_config
PermitRootLogin yes 允许root远程登录
PermitEmptyPasswords yes 允许无密码登录

* 重启服务 service sshd reload  / restart
```


