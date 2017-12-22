# 实验指导 1.2 - 初入 Linux

>#### 学习目标
> * 学会本地登录和远程登录
> * 学会使用命令帮助
> * 学会获取系统基本信息
> * 学会关闭和重启系统

## 任务1：本地登录和远程登录

* 在虚拟机中本地登录
  * 以 root 用户登录
  * 用 Alt+F2 切换第二个虚拟控制台，以 student 用户登录 
* 从宿主机远程登录 Linux
  *. 使用 Git Bash
       $ ssh root@192.168.56.71
       # logout                          # 或 exit 或 Ctrl+d
       
	   $ ssh student@192.168.56.71
	   $ logout                          # 或 exit 或 Ctrl+d
  *. 使用 Putty
    * 从 <http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html> 下载 Putty 并安装
    * 创建两个会话，分别用于 root 和 student 登录 192.168.56.71

> **参考**：<http://www.runoob.com/linux/linux-remote-login.html>

## 任务2：获得命令帮助

* 显示所有可用的 Bash 内置命令
      $ help
* 显示指定的 Bash 内置命令的帮助
      $ help pwd
      $ help type
      $ help exit	
* 使用 `--help` 命令参数获取命令帮助
      $ ls
      $ ls --help
      $ ls /
      $ ls -l /
      $ ll /
      $ which ll                             # ll 是命令别名
      $ ls -F /etc 
      $ ls -a
	  
	  $ which clear
	  $ clear                                # 清屏，快捷键为 <Ctrl+l>
	  
	  $ basename --help
	  $ basename /usr/bin/sort
      $ dirname --help
	  $ dirname /usr/bin/sort

	  $ date
	  $ date --help
	  $ date +%F
	  $ date +%Y/%m/%d
	  $ date +"%F %T"
	  $ date +%s

      # 显示UNIX纪元时间为 1476436877 的当前时区时间
	  $ date --date='@1476436877'             
	  $ date -d '@1476436877'             
	  $ date --date='@1476436877' +"%F %T"
	  $ date -d '@1476436877' +"%F %T"
	  $ date -d '+45 days' +%F                # 显示 45 天后的日期
	  $ date -d '-45 days' +%w                # 显示 45 天前是周几
      # 显示下周五洛杉矶早九点 的当前时区时间
	  $ date -d 'TZ="America/Los_Angeles" 09:00 next Fri'  
	
	  $ cal
	  $ cal --help
	  $ cal -3
	  $ cal 2016
	  $ cal 9 2016
	  $ cal 9 1752                    # 新历换旧历，有11天被去除
* 使用 man 手册获得命令帮助（1）

      $ man ls
	  $ man date
	  $ man cal
	  $ man which
	  $ man basename
	  $ man dirname
      $ man bash

	  $ manpath         # 显示 man 命令在何处查找手册
	  $ man man         # 显示 man 命令的手册
      
      # 从 man 的索引数据库中查找有关 passwd 的手册（精确匹配）
	  $ whatis passwd   
	  $ man passwd
	  $ man 5 passwd
	  
      # 从 man 的索引数据库中查找有关 standards 的手册（模糊匹配）
	  $ apropos standards   
	  $ man 7 standards
	  
	  # 比较 whatis 和 apropos
	  $ whatis ls
	  $ apropos ls  或 man -k ls

	  $ man intro
      $ man 4 console
      $ man 4 pts

>**man手册的操作**（与 `less` 命令的操作键兼容）
> 
>* 下箭头：向下滚动一行；上箭头：向上滚动一行
>* 空格键 或 PgDn：向下滚动一屏；PgUp：向上滚动一屏
>* /string ： 向下搜索字符串 string
>* n：继续向下搜索；N：继续向上搜索
>* g：跳转到手册首行；G：跳转到手册末行
>* q：退出手册，返回Shell提示符

## 任务3：使用 `su -` 切切换用户身份

* 普通用户切换为 root 用户
	  [student@localhost ~]$ su -
	  Password:           # 输入 root 用户口令
	  [root@localhost ~]# 
	  
	  ## 执行只有 root 用户才能执行的管理命令
      # 安装最小化安装未安装的 man-pages
	  [root@localhost ~]# yum -y install man-pages       
	  [root@localhost ~]# mandb --help
      # 创建 man 索引数据库文件
	  [root@localhost ~]# mandb -c
	  
	  [root@localhost ~]# exit
	  [student@localhost ~]$ 
* root 用户切换为普通用户
	  [root@localhost ~]# su - student
	  [student@localhost ~]$
	  
	  [student@localhost ~]$ exit
	  [root@localhost ~]# 

## 任务4：安装必要的软件并更新系统

* 安装必要的软件
	  # yum -y install  lshw pciutils usbutils 
	  # yum -y install  gdisk system-storage-manager
	  # yum -y install  bash-completion 
	  # yum -y install  zip unzip bzip2 tree tmpwatch pinfo man-pages
	  # yum -y install  nano vim-enhanced tmux screen
	  # yum -y install  net-tools psmisc lsof sysstat
	  # yum -y install  yum-plugin-security yum-utils createrepo
	  # yum -y install  git wget curl elinks lynx lftp mailx mutt rsync
* 更新系统
  * 检查是否有可用的软件包更新
        # yum check-update 或 yum list updates
  * 执行更新
        # yum -y update

> **提示**：
>
> * 更新系统时会使用 CentOS 镜像站点中的 update 仓库，因此需要主机连接公网
> * 在安装 Linux 虚拟机时配置了一块自动获得IP的NAT类型的网卡，因此只要安装此虚拟机的宿主机能连接公网则 Linux 虚拟机就能连接公网

## 任务5： 重启系统

* 执行如下命令之一重启系统
      # systemctl reboot
      # reboot
      # shutdown -r now

## 任务6：  获取系统基本信息

* 显示硬件信息
      # lshw                    # 显示所有硬件信息
      # lshw -c processor       # 显示 CPU 的制造厂商及型号
      # lshw -c memory          # 显示物理内存的大小
      # lshw -c disk            # 显示磁盘的实际尺寸
      # lshw -c display         # 显示显卡的制造厂商及型号
      # lshw -c network         # 显示网卡的制造厂商及型号
      
	  # lscpu
	  # lspci
	  # lsusb
* 显示系统信息
      # cat /etc/system-release    # 查看系统发行版本
      # uname -r                   # 查看系统内核版本
      # dmesg                      # 查看系统启动信息
      
      # free -h                    # 查看物理内存和交换空间大小
      # swapon -s                  # 查看所有交换空间
      
      # lsblk                      # 查看系统中的块设备
      # df -Ph                     # 查看磁盘剩余空间
      
      # localectl                  # 查看语言支持与键盘设置
      # timedatectl                # 查看日期和时间（或 date）
      
      # hostnamectl                # 显示主机名（或 hostname）
      # ip addr show               # 显示网络接口参数（或 ifconfig）
      # ip route show              # 显示路由信息（或 route）

## 任务7：  系统基本设置

* 设置语言支持
      # 查看系统支持的语言
	  # localectl list-locales
       
      # 更改为英文，下次登录时生效
      # localectl set-locale LANG="en_US.UTF-8"
	  # 更改为中文，下次登录时生效
	  # localectl set-locale LANG="zh_CN.UTF-8"
* 设置系统时区
      # 查看系统支持的时区
	  # timedatectl list-timezones
	  
	  # 更改时区为欧洲巴黎，立即生效
	  # timedatectl set-timezone Europe/Paris
	  # 更改时区为中国上海，立即生效
      # timedatectl set-timezone Asia/Shanghai	
* 设置日期 和/或 时间
      # timedatectl set-time 23:06:00
      # timedatectl set-time 2016-10-15
      # timedatectl set-time '2016-10-15 23:06:00'
        
      ## CentOS6 及早期版本中使用的命令，CentOS7 仍兼容
      # date -s '20161015'
      # date -s '23:06'
      # date -s '20161015 2306'
      
      # date 101523052016.00     # [MMDDhhmm[[CC]YY][.ss]]
* 设置主机名
      # hostnamectl set-hostname cent7h1.olabs.lan
* 配置SELinux
      # 将配置文件 /etc/selinux/config 中的 `SELINUX=enforcing` 行改为 `SELINUX=disabled`
      # sed -i 's/SELINUX=.*/SELINUX=disabled/' /etc/selinux/config

## 任务8： 关闭系统

* 执行如下命令之一关闭系统
      # systemctl poweroff
      # poweroff
      # shutdown -h now
