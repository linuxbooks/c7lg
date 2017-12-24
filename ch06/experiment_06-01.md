# 实验指导 6 - 服务管理与基础服务

>#### 学习目标
> * 服务管理
>   * 使用 `systemctl` 显示、启动和停止服务
>   * 使用 `systemctl` 实现服务的持久化管理
>   * 使用 `service` 和 `chkconfig/update-rc.d` 管理服务
> * cron 服务
>   * 修改配置文件安排 cron 任务
>   * 使用 `crontab` 命令安排 cron 任务
>   * 控制使用 cron 的人员
> * rsyslogd 和 systemd-journal 服务
>   * 显示系统日志
>   * 配置中央日志服务器
>   * 查看 `LogWatch` 的日志统计信息
> * sshd 服务
>   * 配置仅支持用户密钥登录的 SSH 服务器
>   * 配置支持 sftp+chroot 的 SFTP 服务器
>   * 使用 `ssh-keyscan` 命令搜集可信任主机公钥
>   * 用户密钥管理
>   * 使用 SSH 隧道（Tunnel）实现端口转发（Port forward）


## 任务1：守护进程（服务）管理

* 显示当前已运行的所有服务
* 查看所有服务是否在启动系统时启用
* 显示 cron 服务是否正在运行
* 显示 cron 服务是否在启动时运行
* 显示 cron 服务的运行状态
* 关闭正在运行的 cron 服务
* 显示 cron 服务的运行状态
* 启动 cron 服务
* 禁止 cron 服务在启动时运行
* 启用 cron 服务在启动时运行

## 任务2：修改配置文件安排 cron 任务

>* 请在 /etc/cron.d/test 文件中完成下列任务
>* **提问** 此文件修改后需要重新 restart/reload cron 服务吗？

* 每小时第1分钟将系统平均负载信息以追加方式写入 /root/load 文件
* 每阁3小时的30分时将磁盘剩余信息以追加方式写入 /root/du 文件
* 每周1-5晚10点将 /data/work 目录中的内容向 /backup/data/work 同步一次
* 每月1日和15日凌晨1:30重新启动一次 httpd 服务
* 每天凌晨 0:30 找出 /backup 目录下 90 天以前修改过的文件并将其删除

## 任务3：使用 `crontab` 命令安排 cron 任务

* 切换 student 用户身份，完成如下任务
  * 每天 7：00 找出 ~/student 目录下尺寸最大的 10 个文件列表写入 ~/student/maxsize 文件  
  * 每隔 5 天凌晨的 2 点删除 ~/student/temp 目录下的所有文件
  * 每周日凌晨的 2 点将 ~/student/data 同步到 ~/student/bak/data
* 配置仅允许 student 和 tony 用户安排 cron 任务

## 任务4：显示日志信息

* 浏览 /var/log
  * 使用文本工具查看 /var/log/{secure,message} 文件
  * 检查用户上次登录的时间
* 使用 logwatch
  * 在屏幕上打印昨天的日志信息简要，如用户登录失败信息、SSH 登录信息、磁盘空间使用等。
  * 在屏幕上打印今天的 SSH 登录信息。
* 使用 journalctl
  * 显示journal记录的所有日志
  * 显示自昨天以来记录的日志（类似地可以使用today表示今天）
  * 动态跟踪显示最新日志信息
  * 显示日志级别为err的日志
  * 显示内核日志
  * 显示最近一次的启动日志
  * 显示上次启动时的错误日志
  * 显示systemd指定单元的日志
  * 显示进程名为sshd的相关日志
  * 显示指定时间之内的进程名sudo的日志

>**提问** 如何配置 systemd-journal 服务实现持久化存储（即将其存入磁盘而非 tmpfs） 

## 任务5：配置日志服务器

  * 配置将容器 c7-v1 上的所有 rsyslog 日志记入 宿主服务器 
  * 配置将容器 c6-v1 上的所有 rsyslog 日志记入 宿主服务器
  * 配置将容器 d9-v1 上的所有 rsyslog 日志记入 宿主服务器

## 任务6：SSH 密钥管理

* 在容器的宿主服务器上完成如下操作
  * 收集 c7-v1、c6-v1、d9-v1 的主机公钥
  * 以 root 身份创建密钥对（无私钥口令）
  * 将此公钥分发给容器 c7-v1、c6-v1、d9-v1
  * 分别 ssh 登录容器 c7-v1、c6-v1、d9-v1 进行连接测试
  * 为私钥设置保护口令
  * 使用 ssh-agent、ssh-add 导入私钥
  * 分别 ssh 登录 c7-v1、c6-v1、d9-v1 进行连接测试
* 在安装 VirualBox 的 Windows 宿主机上使用 Putty 携带的工具完成
  * 使用 PuTTYgen 生成密钥对（设置私钥口令）
  * 将私钥保存到 \User\YourName\ 的任意子目录下
  * 打开 Putty 的会话窗口，载入连接 CentOS 7 VirtualBox 虚拟机的回话，设置私钥文件位置
  * 运行 Pageant 导入以创建的私钥
  * 使用 Putty 通过密钥登录 CentOS 7 VirtualBox

>**提示** 若你偏爱命令行工具，不喜欢图形工具（如：Putty），安装 Git for Windows 即可，她集成了 openssh-client。

## 任务7：跨主机的文件复制

* 使用 scp/sftp
  * 使用 scp/sftp 在 CentOS 7 VirtualBox 虚拟机和容器 c7-v1、c6-v1、d9-v1 之间互传文件 
* 使用 Windows 下的 GUI 工具在 WIndows 和 CentOS 7 VirtualBox 虚拟机之间互传文件
  * 使用 [WinSCP](https://winscp.net/) 实现 sftp
  * 使用 [FreeFileSync](https://www.freefilesync.org/) 实现基于 sftp 的目录同步

## 任务8：配置 chroot 的 SFTP 服务

* 配置 sftp-grp 组的成员登录 SFTP 服务器后被监禁在 /home 目录下


## 任务9：配置 SSH 服务

* 设置所有用户必须以密钥方式登录
* 执行 .ssh 目录及文件的严格权限检查
* 设置 ssh 空闲回话时间为5分钟，超过时自动注销
* 关闭 DNS 反向解析功能
* 除了 root 只有 student 和 tony 才能使用 ssh/scp/sftp
* 重新启动 sshd 服务

# 任务10：配置 SSH 隧道

* 配置安装并启动 webmin 
  * 安装：参考 http://www.webmin.com/rpm.html 
  * 启动：`/etc/init.d/webmin start`
* 在 Windows 上配置 SSH 隧道
  * 对本机上的 9000 端口和 CentOS 7 VirtualBox 虚拟机上的 9000 建立 ssh 隧道 
    * 若您已配置了基于 openssh-client 的密钥登录，请使用 ssh 命令
    * 若您已配置了基于 Putty 的密钥登录，请在 Putty 的回话配置界面中设置，也可以使用 plink 命令行工具进行
* 在 Windows 上的浏览器中使用 URL https://localhost:9000 访问 Webmin

## 任务11：服务管理 （续）

* 在 c6-v1 容器上使用 `service` 和 `chkconfig` 管理服务
