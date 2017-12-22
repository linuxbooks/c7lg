# CH01U03 —— 初入 Linux

## Linux 工作界面

* 字符界面（**CLI**：Command Line Interface）
  * **bash**
  *	zsh
  *	sh
* 图形界面（**GUI**：Graphic User Interface）
  * [Gnome 桌面环境](http://www.gnome.org/)
    * [Unity 桌面环境](http://unity.ubuntu.com/)
    * [MATE 桌面环境](http://www.mate-desktop.org/)
    * [Cinnamon 桌面环境](http://cinnamon.linuxmint.com/)
  * [KDE 桌面环境](http://www.kde.org/)
    * [Trinity 桌面环境](http://www.trinitydesktop.org/)
  * [Xfce 桌面环境](http://www.xfce.org/)
  * [LXDE 桌面环境](http://www.lxde.org/)
  * ……

> 可以在 http://www.freedesktop.org/wiki/Desktops/ 了解其他开源桌面系统。

## 为什么使用字符工作方式

* 在字符操作方式下可以高效地完成所有的任务，尤其是系统管理任务。
* 系统管理任务通常在远程进行，而远程登录后进入的是字符工作方式。
* 由于使用字符界面不用启动图形工作环境，大大地节省了系统资源开销。

## 进入字符工作界面的方法

* 在图形环境下开启终端窗口进入字符工作方式。
* 在系统启动后直接进入字符工作方式。
* 使用远程登录方式（SSH）进入字符工作方式。

## 终端类型
* 物理终端：直接接入本机的显示器和键盘设备 （控制台） /dev/console
* 虚拟终端：附加在物理终端之上的以软件方式虚拟实现的终端 /dev/ttyN 
* 模拟终端(伪终端)：图形界面下打开的命令行接口设备；基于 ssh 或 telnet 协议等远程打开的设备  /dev/pts/N
* 串行终端: /dev/ttySN

## 字符界面登录与注销

* 虚拟控制台（Virtual Console）
  * 系统默认提供了6个虚拟控制台。每个虚拟控制台可以独立的使用，互不影响。
  * 使用Alt+F1～Alt+F6进行多个虚拟控制台之间的切换 
* 使用登录名和口令登录
  * 超级用户登录后的操作提示符是“#”
  * 普通用户登录后的操作提示符是“$” 
* 每个用户都有一个存放个人文件的主目录
* 注销
  * logout/exit 命令 
  * Ctrl+d 热键

## ssh 登录远程

* ssh 是英文 Secure Shell 的缩写。 
* 用户在通过ssh连接到远程系统时在网络上传输的口令和数据都是经过加密的，因此更加安全。 
* Linux
      ssh osmond@192.168.1.100
      ssh osmond@192.168.1.100 date
* Windows
  * 使用 [git for windows](git-for-windows.github.io) 中集成的 OpenSSH 客户端
    * Windows 下的 gcc 编译环境 [mingw64](http://mingw-w64.org/) 或 [mingw](http://mingw.org/)
  * 使用 GUI 工具
    * **putty** - http://www.chiark.greenend.org.uk/~sgtatham/putty/
    * SecureCRT - http://www.vandyke.com/products/securecrt/
    * Xshell - http://www.netsarang.com/products/xsh_overview.html

## 当前工作目录

* 每个 shell 和系统进程都有一个当前工作目录（current working directory，cwd）
* shell 初始的当前工作目录
  * 超级用户：/root
  * 普通用户：/home/<useranme>
* 随着用户使用 cd 命令在文件系统中切换目录，可以使用
  * pwd -- 显示 shell 当前工作目录的绝对路径

## 超级用户

* 超级用户（root）：特殊的管理帐号
  * root 具有对系统全部地控制能力 
  * 另一方面也具有对系统破坏的无限能力
* 除非必要，尽量不要登录为 root 账户
  * 普通（无特权，unprivileged）用户的系统破坏能力有限

## 成为超级用户

* $ `su -` ： 新建一个 root 身份执行的 shell
* $ `sudo COMMAND`：以 root 用户身份运行命令
  * 需要被系统管理员事先配置
  * 默认地，wheel 组中的用户皆可使用 sudo

## 命令类型

* 内置命令
  * 由 Shell 自身解析执行的命令
* 外置命令
  * 存执在文件系统路径下的可执行文件
  * 执行时 在 `PATH` 环境变量指定的路径中**依次**搜寻
  * 显示命令的存储路径
    * `which COMMAND`
    * `whereis COMMAND`

> 显示命令类型 `type COMMAND`

## 命令格式

      COMMAND [OPTIONS...] [ARGUMENTS...]

* 选项：指定使用命令的某个或某些功能
  * 短选项（单字符选项）前使用 `-`， 如： `-l` `-h`
    * 多个短选项前可使用一个 `-` ， 如： `-lh`
  * 长选项（单词选项）前使用 --
    * 如： `--help` ， `--human-readable`
* 参数：指定命令的操作对象
    
> 命令名、多个选项、以及多个操作对象之间都用空格间隔

# 几个简单命令

* date
* cal
* cat
* echo
* passwd
* pwd
* type

## 命令帮助

* 使用 --help 命令选项
  * `COMMAND` **--help**
* 内置命令
  * `help`
  * `help COMMAND`
* 外部命令
  * `man [1-8] COMMAND`
  * `info COMMAND`

## man 手册中的常见段落

* NAME
* SYNOPSIS
  * **[]**: 可选内容
  * **<>**: 必选内容
  * **a|b**: 二选一
  * **...**: 同一内容可出现多次
* DESCRIPTION
* OPTIONS
* EXAMPLES
* ENVIRONMENT
* AUTHOR
* REPORTING BUGS
* SEE ALSO

## man 的章节

  * man1: 用户命令
  * man2: 系统调用
  * man3: C库调用
  * man4: 设备文件及特殊文件
  * man5: 配置文件格式
  * man6: 游戏
  * man7: 杂项
  * man8: 管理类的命令

## man 的操作

* `空格键` 或 `PgDn`：向下滚动一屏；`PgUp`：向上滚动一屏
* `下箭头`：向下滚动一行；`上箭头`：向上滚动一行
* `/string` ： 向下搜索字符串 string
  * n：继续向下搜索；N：继续向上搜索
* `?string` ： 向上搜索字符串 string
  * n：继续向上搜索；N：继续向下搜索
* `g`：跳转到手册首行；`G`：跳转到手册末行
* `q`：退出手册，返回Shell提示符

>**man手册的操作** 与 `less` 命令的操作键兼容

## man 搜索

* 显示 man 命令在何处查找手册
  * `manpath`
* 安装最小化安装未安装的 man-pages
  * `yum -y install man-pages`
* 创建 man 索引数据库文件
  * `mandb -c`
  * `mandb` 的配置文件：/etc/man_db.conf
* 从 man 的索引数据库中查找信息（精确匹配）
  * `whatis KEYWORD` 
* 从 man 的索引数据库中查找信息（模糊匹配）
  * `apropos KEYWORD`  或 `man -k KEYWORD`

>**比较 whatis 和 apropos**
>*	`whatis ls`
>*	`apropos ls`  或 `man -k ls`


## info 命令

* 和 man 命令相似，但它提供的信息更加深入
* 不带任何参数运行 info 会列举所有项目
* info 信息页的结构和网页相似
  * 每页都被分成“节点”
  * 到节点的链接又一个前缀“*”
  * `info [命令]`

## 浏览信息（info）页

* 在查看 info 信息页时：
  * 使用箭头键、PgUp、 PgDn　来浏览
  * Tab 会转移到下一个链接
  * Enter　会转移到选中的链接
  * n/p  /u 会转到下一个/前一个/ 　上一级节点
  * s 文本　搜索文本（默认为前一个搜索项目）
  * q 会退出 info 程序


## 安装必要的软件并更新系统

* 安装软件 `yum -y install`
* 检查更新 `yum check-update`
* 更新系统 `yum -y update`

```
# yum -y install  lshw pciutils usbutils bash-completion vim-enhanced tree psmisc net-tools
```

## 获取系统基本信息

* 显示硬件信息
  * lshw
  * lscpu
  * lspci/lsusb
* 显示系统信息
  * cat /etc/system-release
  * uname -r
  * dmesg
  * lsblk
  * df -hP
  * free -m
  * swapon -s
  * localectl
  * timedatectl
  * hostnamectl
  * ip addr show
  * ip route show  

## 系统基本设置

* 设置语言支持
  * `localectl set-locale LANG="zh_CN.UTF-8"`
* 设置系统时区
  * `timedatectl set-timezone Asia/Shanghai`
* 设置日期 和/或 时间
  * `timedatectl set-time 2017-08-15`
  * `timedatectl set-time 20:08:08`
  * `timedatectl set-time '2017-08-15 20:08:08'`
* 设置主机名
  * `hostnamectl set-hostname cl7h1.olabs.lan`
* 配置 防火墙 的 启用/禁用
  * `systemctl stop firewalld.service`
  * `systemctl disable firewalld.service`
* 配置 SELinux 的 启用/禁用
  * `sed -i 's/SELINUX=.*/SELINUX=disabled/' /etc/selinux/config`

## 关机 和 重启

* sync
  * 将文件系统的缓存内容强制写入硬盘中
* 关机
  * systemctl poweroff
  * poweroff
  * shutdown -h now
* 重启
  * systemctl reboot
  * reboot
  * shutdown -r now
  
##  shutdown 命令

* 语法
      shutdown [选项] time [警告信息]
  * time
    * hh:mm
	* +m
	* now(+0)
  * -t sec: 表示给进程发送警告和杀死信号之间的秒数
  * -r/-h：重启/关机
  * -k：仅发出信息给所有用户，但并不会真正关机
  * -c：取消前一个后台运行的 shutdown 命令
  * -F/-f：重新启动时**强制/禁止**运行 fsck
* 举例
      # shutdown  –h  +5  “System will be down in 5 minites, Please save your work.”
