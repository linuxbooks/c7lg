# 阶段测验 2


## 一、判断题

```
1. 在挂装文件系统时可以通过UUID指定文件系统，其UUID的之可以通过blkid命令获取。（  ）

2. 命令 nmcli d sh enp0s3 和 nmcli c sh enp0s3 的输出相同 （  ）

3. 如果一个文件系统处于busy状态，则不能卸装该文件系统。 （  ）

4. 命令 nmcli d d enp0s3 ; nmcli c up enp0s3 用于重新启动设备 enp0s3 的网络连接 （  ）

5. rpm -i abc.rpm 和 yum localinstall abc.rpm 的功能不同。（  ）

6. 在 Linux 环境下，可以使用 iptable 命令来配置 NAT。(  )

7. 为了确保物理安全，应该设置 BIOS 和 GRUB 的修改口令。（  ）

8. let n++ 与 ((n++)) 的功能不同。（  ）

9. 在无状态防火墙中，需要开放1024以上的所有端口来放行应答数据包。（  ）

10. 路由器和命令 ping 及 telnet 均工作于 OSI七层模型的网络层。 （  ） 
```

## 二、单选题

```
1. 在Linux中，哪个文件中包含着IP地址与机器名称的对应关系？（   ）

   A．/etc/lmhosts 
   B．/etc/hosts 
   C．/etc/networks 
   D．/etc/sysconfig/network 
   E. /etc/hostname
   F. /etc/resolv.conf

2. 下列哪个文件包含了各种不同的服务及其端口号的列表？（   ）

   A. /etc/resolv.conf 
   B. /etc/services 
   C. /etc/networks 
   D. /etc/portlist 

3. 在 Linux 环境下，使用什么命令可以关闭网络接口 eth1？ （   ）

   A. service network stop 
   B. service netork stop eth1 
   C. ifdown eth1
   D. ifstop eth1
   E. ps -aux |grep eth1| kill `awk -f {$1}`

4. 在 CentOS 5 下已经安装了一块网卡，下面用于配置第1块虚拟网卡的命令是：（   ）

   A. ifconfig eth0   192.168.0.1 broadcast 192.168.0.255 netmask 255.255.255.0
   B. ifconfig eth1   192.168.0.1 broadcast 192.168.0.255 netmask 255.255.255.0
   C. ifconfig eth1:1 192.168.0.1 broadcast 192.168.0.255 netmask 255.255.255.0
   D. ifconfig eth0:1 192.168.0.1 broadcast 192.168.0.255 netmask 255.255.255.0 

5. 在Linux环境下，使用如下哪个命令可以查看内核路由表? （   ）

   A. netstat --route 
   B. netstat -rn
   C. netstat -an
   D. route show default gw
   E. netstat

6. 在Linux环境下，下面的 crontab 的配置行的含义是什么？（   ）

   10 5 * * * /bin/foo

   A. 一周5天每隔10分钟运行一次/bin/foo
   B. 每天10:05 AM 运行一次/bin/foo  
   C. 每年5月10日运行一次/bin/foo
   D. 每天5:10 AM 运行一次/bin/foo

7. 在如下的crontab文件中，哪个事件每周发生三次：（   ）

   30 4,8,12       *    *    * clean system
   30 6       4,8,12    *    * clean mail
   30 12          14    6    * clean room
   30 12-14        *    *    6 clean car
   30 16           1 6,11    * start myvacation

   A. clean system
   B. clean mail
   C. clean room
   D. clean car
   E. start myvacation

8. 在如下的crontab文件中，哪个事件每天发生三次：（   ）

   30 4,8,12       *    *    * clean system
   30 6       4,8,12    *    * clean mail
   30 12          14    6    * clean room
   30 12-14        *    *    6 clean car
   30 16           1 6,11    * start myvacation

   A. clean system
   B. clean mail
   C. clean room
   D. clean car
   E. start myvacation

9. 在如下的crontab文件中，哪个事件每月发生三次：（   ）

   30 4,8,12       *    *    * clean system
   30 6       4,8,12    *    * clean mail
   30 12          14    6    * clean room
   30 12-14        *    *    6 clean car
   30 16           1 6,11    * start myvacation

   A. clean system
   B. clean mail
   C. clean room
   D. clean car
   E. start myvacation

10. 下面哪个命令用于查看 foo-1.1-1.noarch.rpm 文件要在系统中安装哪些文件：（   ）

    A. rpm –qip foo-1.1-1.noarch.rpm 
    B. rpm –qlp foo-1.1-1.noarch.rpm
    C. rpm –ivh foo-1.1-1.noarch.rpm
    D. rpm –ql foo
    E. rpm –V foo
    F. rpm –q foo
    G. rpm –ivh foo-1.1-1.noarch.rpm

11. 在Linux环境下，使用如下哪个命令可以查看/etc/foo文件是由哪个RPM包安装的? （   ）

    A. rpm -qa |grep foo 
    B. rpm -ql /etc/foo 
    C. rpm -qf /etc/foo
    D. rpm -qc /etc/foo
    E. man foo

12. 在Linux环境下，使用如下哪个命令可以编辑用户自己的 crontab 文件? （   ）

    A. vi ~/.crontab 
    B. cp /etc/crontab . 
    C. crontab -v
    D. crontab -e
    E. cron -edit

13. 下面关于mount的说法错误的是（   ）。

    A. 不能在挂装点目录下实施挂装操作。
    B. 将软盘或光盘放入驱动器后再实施挂装操作。
    C. 可以在没有解除挂装之前从驱动器中将软盘取出。
    D. 不能在已经挂装了文件系统的同一个挂装点上挂装新的文件系统。

14. 一般使用（   ）命令建立分区上的文件系统。

    A. mknod        B. fdisk         C. format        D. mkfs

15. 下面的（   ）情况不会导致 mount 命令出错。

    A. 指定的是一个不正确的设备名            B. 设备不可读
    C. 试图在一个不存在的挂装点挂装设备      D. 文件系统存在碎片

16. 用ftp进行文件传输时，有两种模式： （   ）

    A. Word和binary          B. .txt和Word Document
    C. ASCII和binary         D. ASCII和Rich Text Format

17. 标准光盘的文件系统类型是：（   ）

    A. ext3       B. VFAT/FAT32    C. ISO9660      D. NTFS

18. CentOS 6 系统第一块网卡的网络配置信息存放在哪个文件中？ （   ）

	A. /etc/modules.conf
	B. /etc/sysconfig/network-scripts/ifcfg-eth0
	C. /etc/sysconfig/network-scripts/ifcfg-eth1
	D. /etc/sysconfig/network

19. 关于文件系统的挂装和卸载，下面描述正确的是 。（   ）

    A. 如果光盘未经卸载，光驱是打不开的
    B. 安装文件系统的安装点只能是/mnt下
    C. 不管光驱中是否有光盘，系统都可以挂装CD-ROM设备
    D. mount /dev/sdb /mnt/usb命令中目录/mnt/usb是自动生成的

20. Linux启动时读取哪个配置文件来装载文件系统 （   ）

	A. /etc/mtab     B. /etc/fstab    C. /etc/inittab    D. /etc/xinetd.d

21. 下面的描述错误的是？（   ）

    A. 在CentOS7中，主机名存放在 /etc/hostname 中
    B. 在CentOS 5/6 中，主机名和默认网关存放在 /etc/sysconfig/network 文件中
    C. 在CentOS7中，主机名和默认网关存放在 /etc/sysconfig/network 文件中  
    D. 在CentOS7中，默认网关通过接口配置文件 /etc/sysconfig/network-scripts/ifcfg-* 
	   中的 GATEWAY 指定
	E. 使用 hostname 命令修改主机名，下次启动时将失效
    F. 使用 hostnamectl set-hostname 命令修改主机名，下次启动时仍然有效	

22. 下列提法中，不属于ifconfig命令作用范围的是：（   ）

    A. 配置本地回环地址          B. 配置网卡的IP地址
    C. 激活网络适配器            D. 加载网卡驱动到内核中

23. 若一台计算机的内存为512MB，则交换分区的大小通常设置为：（   ）

    A. 1GB     B. 128MB     C. 256MB     D. 512MB

24. 查看IP地址到以太网MAC地址关系的命令为： （   ）

    A. ping          B. ifconfig          C. arp          D. traceroute

25. 希望重新加载fstab文件中的所有条目，可以以root身份执行什么命令？ （   ）
 
    A. mount -d      B. mount -c        C. mount -a       D. mount -b  

26. 系统交换分区的类型代号为（   ）。 

    A. 82            B. 83            C. 0b            D. 17  

27. 一般情况下，系统启动过程自动加载的文件系统信息是存放在（   ）文件中。

    A. /usr/sbin/cfdisk                 B. /sbin/fdisk  
    C. /etc/mtab                        D. /etc/fstab  

28. 将逻辑分区建立在（   ）分区上。

    A. 从分区      B. 扩展分区      C. 主分区      D. 第二分区  

29. 强制用户或组使用软限额时，可以通过（   ）设置用户超过此数额的宽限时间。 

    A. quotaon     B. quota -u      C. quota -t    D. edquota -t  

30. 为了获取文件系统的配额信息，可以使用（   ）命令。 

    A. quotacheck      B. repquota       C. edquota        D. quota  

31. 一般来说，使用fdisk命令的最后一步是使用（   ）子命令将改动写入硬盘的当前分区表中。 

    A. p         B. r        C. x        D. w  

32. 测试自己的机器与某一主机是否通信正常，使用命令 （   ）

    A. telnet       B. host      C. ping        D. ftp  

33. 为了查看用户没有执行完成的at任务，用户可以执行：（   ） 

    A. atrm       B. atinfo        C. atq        D. at -i  

34. 在 CentOS 7 中，下面哪个命令可以停止 httpd 服务的运行。（   ）

    A. systemctl start httpd
    B. systemctl restart httpd
    C. systemctl status httpd
    D. systemctl stop httpd
	E. systemctl reload httpd

35. 下面哪个命令可以生成一个包含数字、大小写字母的32个字符的随机口令。 （   ）

    A. date +%s
    B. date +%s|md5sum|cut -d' ' -f1
    C. date +%s|sha256sum|head -c 32
    D. date +%s|sha256sum|base64|head -c 32

36. 下面哪个命令不能生成一个包含数字、大小写字母和特殊字符的32个字符的随机口令 （   ）

	A. tr -dc [:alnum:] < /dev/urandom | head -c 32
    B. tr -dc [:graph:] < /dev/urandom | head -c 32
    C. tr -dc [:graph:] < /dev/urandom | fold -w 31 | head -n 1
    D. strings /dev/urandom | grep -o [[:graph:]] | head -n 32 | tr -d '\n'
	E. openssl rand 512 | tr -dc [:graph:] | head -c 32
	F. pwgen -y1 32 或 pwgen -sy1 32

37. 如果想挂载一个 /dev/sdb1 的 DOS 分区到 /mnt/usb 目录，需要运行哪个命令：（   ）

    A.  mount -t exfat /mnt/usb /mnt/sdb1
    B.  mount -t fat32 /dev/sdb1 /mnt/usb
    C.  mount -t vfat /dev/sdb1 /mnt/usb
    D.  mount -t vfat -o loop usb.img /mnt/usb

38. 下面哪条命令不能挂载 U盘（/dev/sdb1）的可读写 NTFS 分区到 /mnt/u 目录。  （   ）

    A. ntfs-3g -o ro/dev/sdb1 /mnt/u
    B. mount -t ntfs-3g -o ro /dev/sdb1 /mnt/u
    C. mount.ntfs-3g -o ro /dev/sdb1 /mnt/u
    D. mount -t ntfs-3g /dev/sdb1 /mnt/u

39. 用 ”useradd john” 命令添加一个用户，这个用户的主目录是什么：（   ）

    A.  /home/john     B.  /bin/john         C.  /var/john        D.  /etc/john

40．CentOS 7 默认使用的 Linux 文件系统类型是（   ）。 

    A. vfat       B. nfs       C. swap       D. ext4        E. xfs 

41. 局域网的网络地址192.168.1.0/24，局域网络连接其它网络的网关地址是192.168.1.1。
    主机 192.168.1.20 访问 172.16.1.0/24 网络时，其路由设置正确的是 （   ）。  

    A. route add –net 192.168.1.0 gw 192.168.1.1 netmask 255.255.255.0 metric 1  
    B. route add –net  172.16.1.0 gw 192.168.1.1 netmask 255.255.255.0 metric 1 
    C. route add –net  172.16.1.0 gw 172.168.1.1 netmask 255.255.255.0 metric 1  
    D. route add default 192.168.1.0 netmask 172.168.1.1 metric 1  

42. 下面哪条命令用于添加到主机的路由。  （   ）

    A. ip route add 192.0.2.0/24 via 10.0.0.1 dev eth0
    B. ip route del 192.0.2.0/24 via 10.0.0.1 dev eth0
    C. ip route add 192.0.2.1 via 10.0.0.1 dev eth0
    D. ip route del 192.0.2.1 via 10.0.0.1 dev eth0
    E. ip route add default via 192.168.1.1 dev eth0
    F. ip route del default via 192.168.1.1 dev eth0

43. 将光盘CD-ROM（hdc）挂装到文件系统的/mnt/cdrom目录下的命令是 （   ） 。  

    A. mount /mnt/cdrom                      B. mount /mnt/cdrom /dev/hdc
	C. mount /dev/hdc     /mnt/cdrom         D. mount /dev/hdc 


44. fsck 对文件系统的检查最先是从文件系统的（   ）开始的。

    A. MBR/GPT       B. 磁盘块       C. 超级块        D. 块链表  

45. 下面哪些口令算“好的口令”？ （   ） 

    A. 12%Wjh            B. abcdefg       C. 111      D. passw0rd  

46. 当一个目录作为一个挂载点被使用后，该目录上的原文件（   ）。

    A. 被永久删除                 B. 被隐藏，待挂载设备卸载后恢复
    C. 被放入回收站               D. 被隐藏，待计算机重新启动后恢复

47. 下面哪条命令可以列出链 POSTROUTING 中所有规则？（   ）

    A. iptables -t nat -A POSTROUTING
    B. iptables -t nat -I POSTROUTING
    C. iptables -t nat -L POSTROUTING
    D. iptables -t nat -D POSTROUTING

48. 在Redhat环境下，下面哪个文件包含了登录root用户允许的终端列表? （   ）

    A. /etc/rooterm.conf 
    B. /etc/terminals 
    C. /etc/secure
    D. /etc/tty.conf
    E. /etc/securetty

49. OpenSSL是一个（   ）

    A. 加密软件   B. 邮件系统   C. 数据库管理系统   D. 嵌入式脚本编程语言

50. 如果没有把一些不常用的功能编译进kernel，最常用的方法是？ （   ）

	A. 当你需要该功能时，把它作为module加载
	B. 重新编译kernel，把该功能添加进来
	C. 重新安装系统
	D. 利用包工具升级内核

51. 网络管理具备以下几大功能：配置管理、（   ）、性能管理、安全管理和计费管理等。

    A. 故障管理      B. 日常备份管理     C. 升级管理      D. 发送提示邮件

52. CentOS 7 系统引导的过程包括如下几步：

    （1）启动引导器GRUB2
	（2）执行本地系统的第一个进程systemd
	（3）Linux内核初始化
	（4）系统固件初始化

    以下正确的引导顺序是 （   ）。 

	A.(4)(2)(3)(1)   B.(4)(1)(3)(2)  C.(2)(4)(3)(1)  D.(1)(4)(3)(2)
 
53. CentOS 7 下日志系统守护进程的主配置文件是（   ）。

    A. /etc/syslog.conf               B. /etc/rsyslog.conf
	C. /etc/rsyslog.d                 D. rsyslogd 
 
54. 为了获得 Shell 命令行参数的个数，可以使用变量（   ）。 

    A. $#           B. $@                C. $0              D. $!  
 
55. shell编程中特殊变量有很多，其中$1-$9描述正确的是 （   ）。

    A. shell脚本执行时接受的9个参数  
    B. shell脚本只能接受9个参数  
    C. shell脚本名为$1,其余表示参数  
    D. shell脚本中使用shift可以实现$1与$9任意位置的互换  

56. 下面哪个 fdisk 的子命令用于列出硬盘分区表。（   ）

    A. l         B. p       C. t        D. m

57. 下面哪个命令用于扩展 LVM 的逻辑卷。（   ）
	
    A. vgextend         B. lvextend       C. vgreduce      D. lvreduce 	
	
58. 下面哪个命令用于重新扫描磁盘上的卷组。 （   ）

    A. vgchange        B. vgdisplay        C. vgs      D. vgscan

59. 下面描述错误的是 （   ）。

    A. lvextend/lvreduce 命令均支持–r|--resizefs 参数用于调整逻辑卷的同时调整文件系统的尺寸
    B. 对ext3/4文件系统可以使用resize2fs命令调整（扩展或缩减）文件系统的尺寸
    C. 对于xfs文件系统可以使用xfs_growfs命令调整（扩展或缩减）文件系统的尺寸
    D. 使用 fsadm 命令可以扩展 ext4/XFS 文件系统的尺寸

60. 下面哪个命令可以显示所有XFS文件系统的用户磁盘限额汇总信息。（   ）

    A. xfs_quota -x -c 'report -a' 
    B. xfs_quota -x -c 'report -u -a' 
    C. xfs_quota -x -c 'report -g -a'
    D. repquota -a

61. CentOS7 下为 enp0s3 接口设备绑定另外IP地址的命令重新启动依然生效的是（   ）。

   A. ifconfig enp0s3 192.168.0.1 broadcast 192.168.0.255 netmask 255.255.255.0
   B. nmcli c m enp0s3 +ipv4.addr "192.168.0.1/24"
   C. ip addr add 192.168.0.1/24 dev enp0s3
   D. ifconfig enp0s3:1 192.168.0.1 broadcast 192.168.0.255 netmask 255.255.255.0
   E. ifconfig eth0:1 192.168.0.1 broadcast 192.168.0.255 netmask 255.255.255.0 

62. 当我们与某远程网络连接不上时，就需要跟踪路由查看，以便了解在网络的什么位置出现了问题，满足该目的的命令是（   ）。
  
    A. ping         B. ifconfig         C. traceroute         D. netstat 

63. 下面有关网络接口配置文件的描述错误的是 （   ）。

    A. 若希望开机时启用此设备，需要指定 ONBOOT=yes
    B. 若希望设置静态IP参数，需要指定 BOOTPROTO=none
    C. 若PREFIX和NETMASK同时存在，PREFIX的配置优先
    D. 通过 GATEWAY 参数指定设备的网关
    E. 当PEERDNS的值为yes时，会使用DHCP服务器分配的DNS值配置 /etc/resolv.conf文件
    F. 当PEERDNS的值为no时，会根据DNS{1,2}的值配置 /etc/resolv.conf 文件
    G. 为当前网络接口绑定多个IP地址可以使用带数字编号的IPADDR和PREFIX指令

64. 下面关于 NetworkManager 的描述错误的是 （   ）。

    A. NetworkManager 是一项管理网络接口和配置网络连接的系统服务
    B. NetworkManager 不仅可以应用在GUI桌面环境，也可应用在未安装图形界面的服务器上
    C. NetworkManager 通过其 ifcfg-rh 插件支持传统的 ifcfg 类型的网络接口配置文件的读写
    D. NetworkManager 支持动态的管理和配置方式来保持网络接口激活和连接的可用性
    E. 在配置网络连接后，需重启 NetworkManager 服务使配置生效
    F. 用户可以使用 NetworkManager 的控制管理工具变更网络状态从而实现网络管理

65. 哪个不是 NetworkManager 的控制管理工具。 （   ）

   A. nm-applet      B. ip      C. nmtui         D. KNetworkManager      E. nmcli

66. 下面哪个命令可以显示网络设备 eno16777736 的状态信息。  （   ）

    A. nmcli dev s
    B. nmcli d s  
    C. nmcli d s eno16777736
    D. nmcli d sh eno16777736

67. 哪条命令用于重新缓存接口 eno16777736 的网络接口配置文件。 （   ）

    A. nmcli connection reload
    B. nmcli dev disconnect eno16777736
    C. nmcli con up ifname eno16777736
    D. nmcli con show eno16777736

68. 下面哪个命令不能激活网络连接。 （   ）

    A. nmcli conn up id eno16777736
    B. nmcli conn s eno16777736
    C. nmcli conn up ifname eno16777736
    D. nmcli c up eno16777736
    E. nmcli cup "My connection" ifname eno16777736

69. 下面哪条命令用于配置 eno16777736 通过 DHCP 获取IP参数。（   ）

   A. nmcli connection eno16777736 ipv4.method manual
   B. nmcli con modify eno16777736 ipv4.method manual 
   C. nmcli c m eno16777736 ipv4.method auto
   D. nmcli d m eno16777736 ipv4.method auto

70. 下面哪个 dig 命令用于查询 192.168.0.252 所对应的域名。 （   ）

    A. dig ls-al.me 
    B. dig @192.168.0.1  ls-al.me 
    C. dig -x 192.168.0.252
    D. dig -t mx ls-al.me 

71. 下面的描述错误的是 （   ）。

    A. 命令 yum makecache 和 yum clean all 的功能相反
    B. 命令 yum provides 和 yum whatprovides 的功能相同
	C. 命令 yum remove 和 yum erase 的功能完全相同
	D. 命令 yum update 和 yum upgrade 的功能完全相同
	E. 命令 yum list updates 和 yum check-update 的功能相同
	F. 命令 yum install 和 yum erase 的功能相反
	G. 若希望实现自动更新，应该安装yum-cron并启动yum-cron服务
	
72. 下面哪条命令可以列出最近被添加到资源仓库中的软件包。 （   ）

    A. yum list available
    B. yum list updates
	C. yum list installed
	D. yum list extras
	E. yum list recent

73. 下面哪个命令可以查询哪些软件包需要 mod_ssl 包。（   ）

    A. rpm -q --whatrequires mod_ssl
    B. rpm -q --requires mod_ssl
    C. rpm -q --scripts mod_ssl
    D. rpm -q --conflicts mod_ssl
    E. rpm -q --obsoletes mod_ssl
    F. rpm -q --changelog mod_ssl

74. CentOS 7 默认没有启用哪个YUM官方仓库。 （   ）

    A. base      B. updates     C. extras      D. centosplus

75. 下面哪个是 CentOS 默认的用于日志滚动的程序。（   ）

    A. logger     B. logresolve     C. logrotate     D. logwatch

76. 下面能正确判断变量 n 的值大于 10 的是 （   ）。

    A. [ $n > 10 ]          B. [ $n>10 ]          C. [$n > 10]
    D. [ $n -gt 10 ]        E. [$n -gt 10]        F. [ $n -lt 10 ]

77. 下面不能正确判断变量 n 的值大于 10 的是 （   ）。

    A. (($n>10))            B. ((n>10))
    C. (( $n>10 ))          D. (( n>10 ))
    E. (( $n > 10 ))        F. (( n > 10 ))
    G. (( $n>10))           H. ((n>10 ))
    I. [ $n -gt 10 ]        J. [ $n -lt 10 ]

78. 若变量 n 的值为 9，则下面哪个命令的输出为 T 。（   ）

    A. [[ $n > 10 ]] && echo T || echo F
    B. [[ $n < 10 ]] && echo T || echo F
    C. [ $n -ge 10 ] && echo T || echo F	
    D. [ $n -gt 10 ] && echo T || echo F	
	
79. 下面的描述错误的是 （   ）。

    A. 可以使用 systemctl reload httpd.service 命令重新加载Apache的配置文件
    B. 可以使用 systemctl restart httpd.service 命令重新启动 Apache 服务
    C. 可以使用 systemctl graceful httpd.service 命令重新启动 Apache 服务
    D. 可以使用 systemctl enable httpd.service 命令设置Apache服务的开机执行

80. 下面的描述错误的是 （   ）。

    A. 使用 systemctl list-units 命令可以显示已加载的单元
    B. 使用 systemctl list-unit-files 命令可以显示已安装的单元
    C. 使用 systemctl --type mount 命令可以显示已加载的mount类型的单元
    D. 使用 systemctl -t target 命令可以显示当前已激活的目标
    E. 使用 systemctl -at target 命令可以显示当前已加载的所有目标
    F. 使用 systemctl list-dependencies 命令显示所有目标的依赖关系
	G. 使用 systemctl get-default 命令可以显示默认的目标

81. 下面哪个命令不能确认当前已经运行了 httpd 服务。（   ）

    A. systemctl is-active httpd
    B. systemctl is-failed httpd
    C. systemctl status httpd
    D. systemctl is-enabled httpd
    E. pstree |grep httpd
    F. ps aux |grep httpd

82. 下面哪个备份工具可以对备份内容实施加密。（   ）

    A. rsync   B. unison   C. rdiff-backup   D. duplicity   E. rsnapshot

83. 下面哪个备份工具可以实现实时同步。 （   ）

    A. rsync   B. lsyncd   C. rdiff-backup   D. duplicity   E. rsnapshot

84. 下面哪个PAM模块可以限制口令中可用的字符类别及数目和口令长度。（   ）

    A. pam_unix      B. pam_pwquality      C. pam_tally2    D. pam_wheel

85. 下面哪个PAM模块可以限制用户在会话过程中对系统资源的使用。 （   ）

    A. pam_limits     B. pam_time      C. pam_listfile     D. pam_access

86. 配置文件 /etc/security/limits.conf 中的哪个配置行
    为 apache 用户同时设置打开文件数的硬限制和软限制。    （   ）

    A. apache		hard		nofile       	65535
    B. apache		soft 		nofile       	65535
    C. apache		-			nofile       	65535
    D. @apache		-			nofile       	65535
    E. *			-			nofile       	65535

87. 下面关于 TCP Wrappers 的描述错误的是 （   ）。

    A. TCP Wrappers 是一个应用层的访问控制程序
    B. CentOS 中内置了libwrap.so 库支持的网络服务程序都能使用TCP Wrappers来实现基于主机的访问控制
    C. TCP wrappers 使用 /etc/hosts.allow 和 /etc/hosts.deny 两个配置文件实现访问控制
    D. 若使用扩展语法，可以仅用 /etc/hosts.allow 一个配置文件实现访问控制
    E. 若服务支持TCP Wrappers，对配置文件/etc/hosts.{allow,deny} 的修改会立即生效，无需重启服务
    F. 由TCP Wrappers提供的访问控制功能，可以被视为防火墙的替代品

88. 下面哪个命令仅进行安全更新，而不更新功能提升的软件。 （   ）

    A. yum check-update
    B. yum -y update
    C. yum -y update-minimal
    D. yum list updates

89. 下面有关 GRUB2 的描述错误的是 （   ）。

    A. 是一种支持多系统启动的系统引导器
    B. 使用模块化的配置文件对启动菜单的设置进行永久性保存
    C. 提供了交互界面和命令行管理工具
    D. 在加载时会读取其配置文件 /boot/grub2/grub.cfg
    E. 可以使用 grub2-mkconfig -o /boot/grub2/grub.cfg 命令生成 GRUB2 的配置文件
    F. 若硬盘引导扇区上的GRUB出现故障，可使用 grub2-install 命令重新安装
    G. 可以使用 grub2-mkpasswd-pbkdf2 命令生成 GRUB 的口令
    H. 可以使用 grub-md5-crypt 命令生成 GRUB 的口令

90. 在 CentOS 7 中，下面哪个命令可以关闭通过 Ctrl+Alt+Delete 热键重启系统的功能。 （   ）

    A. sed -i -e 's/^start/#start/' -e 's/^exec/#exec/' /etc/init/control-alt-delete.conf
    B. sed -i '/ctrlaltdel/ s/^ca/#ca/' /etc/inittab
    C. systemctl mask control-alt-delete.servie && systemctl daemon-reload
    D. systemctl isolate control-alt-delete.servie && systemctl daemon-reload

91. 下列关于包过滤技术防火墙的描述，错误的是（   ）。

    A. 包过滤技术对于用户来说是透明的。
    B. 包过滤技术可以过滤应用层数据
    C. 包过滤技术配置和维护较为复杂
    D. 以上答案都不对

92. 下列关于代理服务技术防火墙的描述，错误的是（   ）。 

    A. 代理服务技术可以实现基于用户级的身份认证和访问控制
    B. 代理服务技术可以过滤应用层数据
    C. 代理服务技术支持第三方的身份认证系统和日志记录系统
    D. 代理服务技术可以阻止已感染病毒的文件传输到内部网络

93. 下面关于入侵检测系统的描述错误的是 （   ）。

    A. 入侵检测系统可以辅助安全管理人员进行安全审计、监视、进攻识别和响应等管理工作
    B. 分为 HIDS（基于主机的入侵检测系统）和NIDS（基于网络的入侵检测系统）两种
    C. Linux 下可用的 HIDS 软件有 Tripwire、AIDE
    D. Linux 下可用的 NIDS 软件有 OSSEC、SNORT、PSAD

94. 对如下命令描述错误的是 （   ）。

    nmcli c m enp0s3 ipv4.method manual ipv4.addresses 10.0.0.30/24 \ 
	  ipv4.gateway 10.0.0.1 ipv4.dns "10.0.0.1 8.8.8.8"

    A. 为网络接口 enp0s3 设置静态 IP 参数
    B. IPv4地址设置为 10.0.0.30，子网掩码为 255.255.255.0，网关地址为 10.0.0.1
    C. 首选DNS为 10.0.0.1，次选DNS为 8.8.8.8
    D. 执行该命令后立即生效
    E. 执行该命令后，还需执行 nmcli d d enp0s3 ; nmcli c up enp0s3 命令后才会生效

95. 下面的用户空间管理工具中，用于对IPV4数据包检查和操作的是 （   ）。

    A. iptables      B. ebtables     C. ip6tables      D. conntrack
	
96. 下面 iptables 命令的作用是 （   ）。

    iptables -N syn-flood            
    iptables -A INPUT -i eth0 -syn -j syn-flood
    iptables -A syn-flood -m limit -limit 5000/s -limit-burst 200 -j RETURN
    iptables -A syn-flood -j DROP

    A. 禁用路由
    B. 阻止 IP 欺骗
    C. 防止 syn-flood 攻击
    D. 防止 DoS 攻击

97. 下面用于清除filter表中所有链中的所有规则的命令是 （   ）。

    A. iptables -F      B. iptables -X      C. iptables -Z      D. iptables -L

98. 下面关于 Netfilter 对表、链、规则的处理描述错误的是 （   ）。

    A. 相同链上不同表的匹配顺序为：raw -> mangle -> nat -> filter -> security
    B. 链内的规则匹配顺序：自上而下按规则的出现顺序依次进行匹配检查
    C. 如果数据包与链中某条规则不匹配，那么它将依次与链中的下一条规则进行比较
    D. 如果数据包与链中的任何规则都不匹配，那么Netfilter将参考该链的策略来决定如何处理该包
    E. 如果数据包与链中的任何规则都不匹配，那么直接丢弃该包

99. 允许 192.168.0.123 访问本机 3306 端口的 iptables 规则是 （   ）。

    A. iptables -I INPUT -p tcp -m tcp --dport 3306 -s 192.168.0.123 -j ACCEPT
    B. iptables -I INPUT -p tcp -m tcp --sport 3306 -d 192.168.0.123 -j ACCEPT
    C. iptables -I INPUT -p tcp -m tcp --dport 3306 -d 192.168.0.123 -j ACCEPT
    D. iptables -I INPUT -p tcp -m tcp --sport 3306 -s 192.168.0.123 -j ACCEPT
    E. iptables -I INPUT -p tcp -m tcp --dport 3306 -j ACCEPT

100. 下面哪个命令用于显示由 Systemd 在开机就运行的服务。（   ）

    A. systemctl -t service --state=active
    B. systemctl list-unit-files -t service --state=enabled
	C. systemctl -t service
	D. systemctl list-unit-files -t service
	E. systemctl

```



## 三、多选题

```
1. 在Linux环境下，可以测试DNS服务器的命令是：（     ）

   A. nslookup 
   B. dig
   C. host
   D. hostname

2. 下面哪些命令可以生成一个包含数字、大小写字母的32个字符的随机口令。 （     ）

    A. tr -dc [:alnum:] < /dev/urandom | head -c 32
    B. tr -dc [:alnum:] < /dev/urandom | fold -w 32 | head -n 1
    C. strings /dev/urandom | grep -o [[:alnum:]] | head -n 32 | tr -d '\n'
    D. date +%s | sha256sum | base64 | head -c 32
	E. dd if=/dev/urandom count=1 2>/dev/null | base64 | head -c 32
	F. openssl rand -base64 64 | head -c 32
	G. pwgen -1 32 或 pwgen -s1 32
	H. openssl rand -base64 32

3. 下面哪些命令可以生成10个包含数字、大小写字母和特殊字符的32个字符的随机口令。（     ）

	A. tr -dc [:alnum:] < /dev/urandom | head -c 320 |fold -w 32
    B. tr -dc [:graph:] < /dev/urandom | head -c 320 |fold -w 32
    C. tr -dc [:graph:] < /dev/urandom | fold -w 32 | head -n 10
    D. strings /dev/urandom | grep -o [[:graph:]] | head -n 32 | tr -d '\n'
	E. openssl rand 1024 | tr -dc [:graph:] | fold -w 32 | head -n 10
	F. pwgen -y1 32 10 或 pwgen -sy1 32 10

4. 在 Linux系统中，下列哪些文件与名称解析有关？（     ）

   A. /etc/host.conf
   B. /etc/resolv.conf
   C. /etc/hosts
   D. /etc/nsswitch.conf

5. 在 Linux 环境下，使用如下哪些命令可以查看内核路由表? （     ）

   A. netstat -Route 
   B. netstat -rn
   C. netstat -an
   D. route show default 
   E. route
   F. ip route show

6. 下面的（）情况可能导致mount命令出错。（     ）

   A. 指定的是一个不正确的设备名          B. 设备不可读
   C. 试图在一个不存在的挂装点挂装设备    D. 文件系统存在碎片

7．CentOS 7 支持的 Linux文件系统类型：（     ）。 

    A. ntfs                     B. xfs             C. swap    
	D. ext 2/3/4                E. nfs             F. btrfs

8. 下面哪些命令可以创建 Linux 的文件系统。 （      ）

    A. mkfs.ext4           B. mkfs.btrfs           C. mkfs.xfs
    D. mkfs.vfat           E. mkswap               F. mke2fs
    G. mkfs -t ext3        H. mkfs.ntfs-3g         I. mkbootdisk

9. 关于限制磁盘限额，描述正确的是（     ）。

   A. 使用edquota可以监控系统所有用户使用的磁盘空间，并在接近极限时提示用户
   B. 用户组的磁盘限额是用户组内所有用户予设磁盘空间总和
   C. 单个用户的磁盘限额就是该用户所在用户组内所有磁盘限额的总合
   D. 在Linux系统下限制用户使用的磁盘空间可以使用edquota
   E. 用户组的磁盘限额就是该用户组内拥有最大磁盘限额值的用户的磁盘限额

10. 下列关于/etc/fstab文件描述，正确的是（     ）。

    A. fstab文件只能描述属于linux的文件系统
    B. CD_ROM和软盘必须是自动加载的
    C. fstab文件中描述的文件系统不能被卸载
    D. fstab文件中描述的根文件系统不能被卸载
    E. 启动时按fstab文件描述内容装载文件系统

11. 为了观察正在不断增长的日志文件 /var/log/messages ，可以使用哪些命令。 （     ）
 
       A. tail -f  /var/log/messages       B. tac   /var/log/messages      
	   C. watch /var/log/messages          D. watch tail /var/log/messages 

12. 下面关于 NAT 的叙述错误的是？（     ）

    A. NAT英文全称是Network Address Translation，称为网络地址转换，它是一个IETF标准，
    B. NAT可以应用到防火墙技术里，把个别IP地址隐藏起来不被外界发现，使外界无法直接访问内部网络主机/设备。
    C. NAT是通过改写数据包的源IP地址、目的IP地址、源端口、目的端口来实现的。
    D. NAT分为源NAT（Source NAT，SNAT）和目的NAT（Destination NAT，DNAT）两种不同的类型。
    E. Linux世界里的IP伪装（IP Masquerading）非常出名，它是DNAT的一种特殊形式。
    F. 端口转发、负载均衡和透明代理都属于SNAT。

13. 用于在当前Shell中执行当前目录下名为 myscript 的可执行脚本的命令是（      ）。

    A. myscript                B. ./myscript            C. . ./myscript
    D. sh myscript             E. . myscript            F. source myscript
	G. source ./myscript       H. sh ./myscript

14. 下面关于 OpenSSH 的描述正确的是（      ）。

    A. 开放源代码的安全加密程序 
    B. OpenSSH常用于为http协议加密
    C. OpenSSH用于提高远程登录访问的安全性 
    D. SSH和telnet使用同样的端口号
    E. OpenSSH 既支持用户口令认证又支持用户密钥认证

15. 当root密码丢失后，应该：（      ）

    A. 使用 Linux LiveCD 启动，挂载磁盘上的 / 文件系统后可以修改 root 密码
    B. 对于 CentOS 5/6 ，通过GRUB进入单用户模式后修改 root 密码
    C. 对于 CentOS 7 ，进入 rescue.target 或 emergency.target 目标后可以修改 root 密码
    D. 重新安装系统
	E. 对于 CentOS 7 ，通过GRUB为内核传递 rd.break 参数在内核初始化后中断系统 systemd 的执行，
	   并提供一个无需root口令登录的调试Shell。进入该Shell后，挂载磁盘上的 / 文件系统后可以修改root密码

16. 下面哪些是Linux下的磁盘分区工具。（     ）

   A. fdisk          B.  mkfs         C. gdisk           D. parted

17. 下面哪些命令可以扩展文件系统的大小。 （     ）

    A. xfs_repair           B. xfs_admin           C. xfs_growfs 
    D. tune2fs              E. resize2fs           F. fsadm

18. 下面描述正确的是 （      ）。

    A. 当文件系统上面有打开的文件时，文件系统处于busy状态
    B. 当某个进程的工作目录在文件系统时，文件系统处于busy状态
    C. 当文件系统上的缓存文件正在被使用时，文件系统处于busy状态
    D. 使用 fuser命令可以查找使用文件系统的进程，同时也提供了杀死这些进程的方法 

19. 下面关于一致的网络设备名的描述正确的是 （      ）。

    A. enp0s3 表示 PCI接口的以太网设备（PCI总线地址0，插槽编号为3）
    B. eno16777736 表示板载的以太网设备（板载设备索引编号为16777736）
    C. 系统启动过程中由 systemd 的 systemd-udev 将内核识别的网络设备名重命名为一致的网络设备名
    D. 使用 grubby --update-kernel=ALL --args=net.ifnames=0 命令
       可以禁用一致的网络设备名而使用传统的网络设备名
    E. 使用 ln -s  /dev/null  /etc/udev/rules.d/80-net-name-slot.rules 命令
       通过禁用systemd-udev的规则文件也可以禁用一致的网络设备名

20. 如下的哪些配置在重启系统后依然生效。 （      ）

   A. ifconfig enp0s3 192.168.0.1 netmask 255.255.255.0
   B. ip addr add 192.168.0.1/24 dev enp0s3
   C. nmcli c m enp0s3 ipv4.method manual ipv4.addresses 168.0.1/24 
   D. echo -e 'BOOTPROTO=none\nONBOOT=yes\nIPADDR=10.0.0.30\nPREFIX=24\nDEVICE=enp0s3' \
      > /etc/sysconfig/network-scripts/ifcfg-enp0s3

21. 下面哪些命令可以显示网络设备 enp0s3 的传输统计信息。（      ）

    A. ip addr show enp0s3
    B. ip link show enp0s3
    C. ip -s link show enp0s3
    D. ifconfig enp0s3

22. CentOS7 下为 enp0s3 接口设备绑定另外IP地址的命令能立即生效的是（      ）。

   A. ifconfig enp0s3 192.168.0.1 broadcast 192.168.0.255 netmask 255.255.255.0
   B. nmcli c m enp0s3 +ipv4.addr "192.168.0.1/24"
   C. ip addr add 192.168.0.1/24 dev enp0s3
   D. ifconfig enp0s3:1 192.168.0.1 broadcast 192.168.0.255 netmask 255.255.255.0
   E. ifconfig eth0:1 192.168.0.1 broadcast 192.168.0.255 netmask 255.255.255.0 

23. 下面的四条命令：  （     ）

    （1）scp id_rsa.pub osmond@192.168.0.100:.ssh/authorized_keys
    （2）cat id_rsa.pub | ssh osmond@192.168.0.100 "cat - > ./ssh/authorized_keys"
    （3）cat id_rsa.pub | ssh osmond@192.168.0.100 "cat - >> ./ssh/authorized_keys"
    （4）ssh-copy-id -i osmond@192.168.0.100

    A. (1)和(2)的功能相同               B. (1)和(3)的功能相同
    C. (2)和(4)的功能相同               D. (3)和(4)的功能相同

24. 下面哪些不是以数值进行比较判断的。（     ）

    A. [ $n > 10 ]                      B. [[ $n > 10 ]]
    C. [ $n -gt 10 ]                    D. [[ $n -ge 10 ]]
    E. [ $n -le 10 ]                    F. [[ $n -lt 10 ]]
    G. ((n>10))                         H. ((n<10))
    I. test $num -gt 10                 J. test $num -le 10 

25. 下面的描述正确的是 （       ）。

    A. 使用 yum-utils 包提供的 yum-config-manager 命令可以启用和禁用仓库
    B. 使用 yum repolist 命令可以显示已启用的仓库
    C. 使用 rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-* 命令可以导入仓库的 GPG 公钥
    D. 使用 rpm -q gpg-pubkey 命令可以查询所有已安装的GPG公钥信息 

26. 下面哪个命令可以查询 mod_ssl 的包信息。（     ）

    A. rpm -ql mod_ssl
    B. rpm -qc mod_ssl
    C. rpm -qd mod_ssl
    D. rpm -qi mod_ssl
    E. rpm -q mod_ssl
    F. rpm -qf /etc/httpd/conf.d/ssl.conf
	G. yum info mod_ssl

27. 下面哪个命令可以查询 mod_ssl 包的依赖关系。（     ）

    A. rpm -q --whatrequires mod_ssl
    B. rpm -q --requires mod_ssl
    C. rpm -q --scripts mod_ssl
    D. yum provides mod_ssl
    E. yum deplist mod_ssl 

28. 通过查看 top 命令的输出，如下描述正确的选项是 （        ）。

  top - 02:38:35 up 15 days,  2 user,  load average: 0.04, 0.03, 0.02
  Tasks: 157 total,   2 running, 155 sleeping,   0 stopped,   0 zombie
  %Cpu(s):  5.8 us,  8.6 sy,  0.0 ni, 95.2 id,  0.4 wa,  0.0 hi,  0.0 si,  0.0 st
  KiB Mem :  1016860 total,   748112 free,    96708 used,   172040 buff/cache
  KiB Swap:  2097148 total,  2097148 free,        0 used.   767412 avail Mem

    A. 服务器已经运行了 15 天
	B. 过去1、5、15分钟的平均负载分别是 0.04, 0.03, 0.02
	C. 共有157个进程，2个处于运行态，155个处于睡眠态
	D. 用户进程占用5.8%CPU时间，系统进程占用8.6%CPU时间，等待IO占用0.4%CPU时间，空闲95.2%CPU时间
	E. 系统当前有 2 个登录用户
	F. 系统有 1G 物理内存，已使用 96M，块设备的读写缓冲区和文件系统的页面缓存使用了172M
	G. 系统有 2G 交换空间，当前未使用
	H. 系统运行良好，无资源瓶颈

29. 通过 vmstat 命令的输出可知，下面选项描述正确的是 （      ）。

  $ vmstat 2 5
  procs -----------memory---------- ---swap-- -----io----  -system--  ------cpu-----
   r  b   swpd   free   buff  cache   si   so    bi    bo    in   cs  us sy id wa st
   45 0      0 533932   1860 384092    0    0   108    35  1531  986  61 30  9  1  0
   58 0      0 533932   1860 384124    0    0    22     6  1413 1027  69 31  0  0  0
   55 0      0 533932   1860 384124    0    0    35     4  1441  989  69 31  0  0  0
   57 0      0 533932   1860 384124    0    0    17     4  1606 1160  69 31  0  0  0
   60 0      0 533932   1860 384124    0    0    26     7  2329 1086  68 32  0  0  0

    A. 等待运行的进程长期大于1，说明cpu繁忙，需要增加cpu
	B. US列的值长期大于60%，说明用户进程消耗的cpu时间较多，应考虑优化用户的程序
	C. US+SY的值几乎接近 100%（id的值接近0），说明 cpu不足，需要增加cpu
	D. 磁盘IO等待时间过长，需要更换 SSD 硬盘
	E. 需要增加物理内存

30. Systemd的核心组件包括 （      ）。

    A. 守护进程systemd负责Linux的系统和服务。命令行工具systectl用于控制 systemd 管理的系统和服务状态。
    B. Systemd 使用内核的 Cgroup 子系统跟踪系统中的进程，并提供了systemd-{cgls,cgtop} 用于显示Cgroup资源信息。
    C. 命令行工具systemd-analyze用于分析系统启动性能并检索其他状态和跟踪信息。
    D. 由systemd启动的systemd-logind守护进程负责管理用户登录。
    E. 由systemd启动的systemd-journal守护进程负责记录事件的二进制日志。
    F. 由systemd启动的systemd-udevd守护进程负责监听内核的udev事件并根据相应的 udev 规则执行匹配的指令。

31. Systemd 使用哪些激活机制以提高系统启动的并行性。（      ）

    A. 基于Socket激活      B. 基于D-Bus激活      C. 基于Device激活      D. 基于Path激活

32. 下面哪些命令可以显示指定单元的顺序依赖关系。（      ）

    A. systemctl show --property "Wants" boot.mount
    B. systemctl show --property "Before" crond.service
    C. systemctl show --property "After" crond.service | fmt -10 | sed 's/After=//g' | sort
    D. systemctl show --property "Requires" boot.mount
    E. systemctl show --property "Conflicts" postfix.service

33. 三种备份策略是 （      ）。

   A. 完全（Full）备份        B. 差分（Differential）备份       C. 系统备份
   D. 应用程序备份            E. 增量（Incremental）备份        F. 用户数据备份

34. 下面用于加密文件的命令是 （      ）。

    A. openssl enc -des3 -k mypasswd -e -in file11 -out file12
    B. openssl enc -des3 -k mypasswd -d -in file13 -out file14
    C. openssl enc -aes256 -k mypasswd -e -in file21 -out file22
    D. openssl enc -aes256 -k mypasswd -d -in file23 -out file24
    E. sha256sum my.iso
    F. openssl dgst -sha256 my.iso

35. 对于下面的 openssl 命令，描述正确的是 （      ）。

   openssl req -new -x509 -days 365 -sha256 -nodes \
    -newkey rsa:2048 -keyout private/ftp.olabs.lan.key -out certs/ftp.olabs.lan.crt \
    -subj '/O=olabs/L=Beijing/C=CN/emailAddress=osmond@olabs.lan/CN=ftp.olabs.lan'

    A. 用于生成自签名的X509证书文件和与之对应的私钥文件
    B. 证书文件为 ftp.olabs.lan.key；私钥文件为 ftp.olabs.lan.crt
    C. 私钥使用2048位密钥长度的RSA算法；证书签名使用sha256哈希算法
    D. 使用名为 nodes 的对称加密算法对私钥进行加密
    E. 证书的有效期为 365 天
    F. 证书的 Common Name 为 ftp.olabs.lan

36. 下面哪些软件可以实现具有高速缓存的代理服务。（      ）

    A. Dnsmasq                 B. Polipo                 C. Squid
    D. LibreSwan               E. OpenVpn                F. Varnish

37. 下面哪些命令可以显示正在运行系统的启动日志。 （      ）

    A. journalctl
    B. journalctl --since yesterday
    C. journalctl -p err
    D. journalctl -k
    E. journalctl -b
    F. journalctl -b-1 -p err
    G. journalctl -u boot.service
    H. dmesg

38. 下面的命令，可以输出 a00～a09 序列的是（      ）。

    A. echo a0$(seq 0 9)
    B. echo a$(seq 9)
    C. echo {a00..a09}
    D. echo a{0..9}0
    E. echo a0{0..9}
    F. echo a{00..09}

39. 下面能输出序列 20 17 14 11 的命令或表达式是（      ）。

    A. seq 10 -3 20               E. {10..20..3}
    B. seq 10 20 3                F. {10..3..20}
    C. seq 20 -3 10               G. {20..10..3}
    D. seq 20 3 10                H. {20..3..10}

40. 下面哪些命令可以提升普通用户的权限。 （       ）

    A. sudo      B. su      C. su -     D. sudo -s

41．在shell 编程中关于$2 的描述正确的是（      ）。

    A. 程序后携带了两个位置参数
    B. 宏替换
    C. 程序后面携带的第二个位置参数
    D. 携带位置参数的个数
    E. 用$2 引用第二个位置参数

42. 当前主机的网卡eth0 的IP为192.168.16.1,将本地 80 端口的请求转发到 8080 端口的命令是（      ）。

    A. iptables -t nat -A PREROUTING -d 10.0.0.1 -p tcp --dport 80 -j DNAT --to-destination 10.0.0.1:8080
    B. iptables -t nat -A PREROUTING -d 10.0.0.1 -p tcp --dport 80 -j DNAT --to 10.0.0.1:8080
    C. iptables -t nat -A POSTROUTING -d 10.0.0.1 -p tcp --dport 80 -j DNAT --to 10.0.0.1:8080
    E. iptables -t nat -A PREROUTING -i eth0 -d 10.0.0.1 -p tcp --dport 80 -j REDIRECT --to-ports 8080
    E. iptables -t nat -A PREROUTING -i eth0 -d 10.0.0.1 -p tcp --dport 8080 -j REDIRECT --to-ports 80
    F. iptables -t nat -A POSTROUTING -i eth0 -d 10.0.0.1 -p tcp --dport 80 -j REDIRECT --to-ports 8080

43. 服务器有两块网卡，网卡 eth0 的IP为 1.2.3.4，网卡 eth1 的IP为10.0.0.1，下面用于局域网共享上网的命令是（     ）。

    A. iptables -t nat -A POSTROUTING -s 10.0.0.0/24 -o eth0 -j SNAT --to-source 1.2.3.4
    B. iptables -t nat -A POSTROUTING -s 10.0.0.0/24 -j MASQUERADE 
    C. iptables -t nat -A PREROUTING -s 10.0.0.0/24 -j MASQUERADE 
    D. iptables -t nat -A PREROUTING -s 10.0.0.0/24 -o eth0 -j SNAT --to-source 1.2.3.4

44. 下面关于连接跟踪的描述正确的是 （          ）。

    A. 可以使用连接跟踪信息实现状态防火墙
    B. NAT依赖连接跟踪信息转换所有相关的数据包
    C. 基于 Netfilter 的 nf_conntrack.ko 及其相关的模块 nf_conntrack_*.ko 实现连接跟踪功能
    D. 连接跟踪不仅可以跟踪有状态的连接协议（如TCP），还可以跟踪无状态的传输协议（如UDP）
    E. 连接跟踪的状态更新会在两个位置被触发，一个是PREROUTING链，另外一个是OUTPUT链
    F. 连接跟踪加快了已建立连接的后续数据包的放行
    G. 连接跟踪可以使用一条规则跟踪所有连接的回应包
    H. 连接跟踪可以只开放那些有应答数据的端口，无需打开1024以上的所有端口来放行应答数据包
    I. 连接跟踪的缺点是需要使用更多的物理内存
    J. 鉴于连接跟踪的诸多优点，应该尽量使用
    K. 在使用连接跟踪的同时，为避免连接跟踪表满丢弃数据包的情况，通常只对防火墙的部分流量实施非连接跟踪

45. 若在 Web 服务器的 /var/log/messages 日志里出现如下信息，则选项中描述正确的是（      ）。

    kernel: nf_conntrack: table full, dropping packet. 

    A. 防火墙的规则设置启用了连接跟踪，例如：
	   iptables -A INPUT -m conntrack --ctstate INVALID -j DROP
       iptables -A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
       iptables -A INPUT -m conntrack --ctstate NEW -p tcp -m multiport --dport 22,80,443 -j ACCEPT
       iptables -A INPUT -m conntrack --ctstate NEW -j DROP
    B. 由于Web服务器访问量较大，使连接跟踪表满，从而导致了上述错误
    C. 对于物理内存较大的服务器，可以通过加大 conntrack_max 的值和缩短已建立连接的timeout时间来解决，例如：
       sysctl -w net.nf_conntrack_max=655360 
       sysctl -w net.netfilter.nf_conntrack_max=655360 
       sysctl -w net.netfilter.nf_conntrack_tcp_timeout_established=28800 
       sysctl -p
    D. 对于物理内存较小的服务器，可以通过使用 raw 表，使对Web服务的访问绕过连接跟踪，例如：
       iptables -t raw -A PREROUTING -p tcp -m multiport --dport 80,443 -j CT --notrack
	   iptables -A INPUT -m conntrack --ctstate INVALID -j DROP
       iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED,UNTRACKED -j ACCEPT
       iptables -A INPUT -m conntrack --ctstate NEW -p tcp -m tcp --dport 22 -j ACCEPT
       iptables -A INPUT -m conntrack --ctstate NEW -j DROP

46. 下面关于 CentOS 7 的防火墙描述正确的是 （        ）。

    A. CentOS 7 引入了动态防火墙配置系统，为了兼容低版本，仍旧支持静态防火墙配置系统
    B. CentOS7 中的 firewalld 守护进程和 iptables 服务可以共存
    C. 可以使用图形工具firewall-config和命令行工具firewall-cmd配置基于 firewalld 的防火墙
    D. 可以使用图形工具firewall-config和命令行工具lokkit配置基于 iptables 服务的防火墙
    E. 仅当 firewalld 运行的情况下，才可以使用 firewall-cmd 命令配置和管理防火墙
    F. firewalld 将所有网络流量分为多个区域从而简化防火墙管理，默认的区是 private 
	G. 默认情况下，firewalld 只对 external 区开启了IP伪装功能

47. 若已执行了 firewall-cmd --set-default-zone internal 命令，则可以同时为默认区域配置运行时规则
    和持久性规则的 firewall-cmd 命令是 （        ）。

    A. firewall-cmd --add-service=https
       firewall-cmd --add-service=https --permanent
    B. firewall-cmd --zone=public --add-service=https
       firewall-cmd --zone=public --add-service=https --permanent
    C. firewall-cmd --add-service=https --permanent 
       firewall-cmd --reload
    D. firewall-cmd --add-service=https
       firewall-cmd --runtime-to-permanent
    E. firewall-cmd --zone=internal --add-service=https
       firewall-cmd --zone=internal --add-service=https --permanent

48. 下面用于判断变量name的之不为空的是 （      ）。

    A. [ "$name" = "" ]                 B. [ "$name" != "" ]
    C. [ -z "$name" ]                   D. [ -n "$name" ]
    E. [ ! "$name" ]                    F. [ "$name" ]
    G. [ "X${name}" = "X" ]             H. [ "X${name}" != "X" ]
	I. [ ! -s "$name" ]                 J. [ -s "$name" ]

49. 下面能计算出 1～100 之和的是 （        ）。

    A. s=0 ; for ((i=1;i<=100;i++)) ; do ((s+=i)) ; done
    B. s=0 ; for ((i=1;i<=100;)) ; do ((s+=i;i++)) ; done
    C. s=0 ; i=1; for ((;i<=100;)) ; do ((s+=i,i++)) ; done
    D. i=0 ; s=0; while ((i<100)) ; do ((i++,s+=i)) ; done
    E. i=0 ; s=0; until ((i==100)) ; do  ((i++,s+=i)) ; done
    F. for ((s=0,i=1;i<=100;i++)) ; do ((s+=i)) ; done
    G. for ((s=0,i=1;i<=100;s+=i,i++)) ; do : ; done
    H. for ((s=0,i=1;i<=100;i++,s+=i)) ; do : ; done

50. 为了确保WB服务器的安全，下面哪些内核参数设置是合理的。 （       ）

    A. 启用 TCP SYN Cookie 保护（防止常见的SYN泛洪攻击）
       net.ipv4.tcp_syncookies = 1
    B. 对服务器禁用地址重定向
       net.ipv4.conf.all.accept_redirects = 0
       net.ipv4.conf.all.secure_redirects = 0
       net.ipv4.conf.all.send_redirects = 0
       net.ipv4.conf.default.accept_redirects = 0
       net.ipv4.conf.default.secure_redirects = 0
       net.ipv4.conf.default.send_redirects = 0
    C. 禁用 IP 源路由
       net.ipv4.conf.all.accept_source_route = 0
       net.ipv4.conf.default.accept_source_route = 0
    D. 开启反相路径源验证，IP欺骗保护（RFC1812）
       net.ipv4.conf.all.rp_filter = 1
       net.ipv4.conf.default.rp_filter = 1
    E. 对服务器禁用包转发
       net.ipv4.ip_forward = 0
       net.ipv4.conf.all.forwarding = 0
       net.ipv4.conf.default.forwarding = 0
    F. 接受直接 ping 请求响应，拒绝响应 ping 的广播请求
       net.ipv4.icmp_echo_ignore_all = 0
       net.ipv4.icmp_echo_ignore_broadcasts = 1

```

## 四、搭配题

```
１、将常用的系统信息显示命令与其功能联系起来。

(  ) 01. lsof                 A. 显示 Linux 内核等信息
(  ) 02. lsblk                B. 显示系统在线信息
(  ) 03. dirname/basename     C. 显示系统启动相关信息
(  ) 04. df -h                D. 显示系统分区表
(  ) 05. lspci/lsusb          E. 显示物理卷/卷组/逻辑卷信息
(  ) 06. mountpoint           F. 显示磁盘限额报告
(  ) 07. uname                G. 显示系统块设备信息
(  ) 08. fdisk -l             H. 显示系统已经挂载的文件系统
(  ) 09. dmesg                I. 显示指定目录是否是挂装点
(  ) 10. chkconfig --list     J. 显示系统启动运行的 SysV 类型的守护进程
(  ) 11. free                 K. 显示正在运行中的进程打开了哪些文件、目录和套接字
(  ) 12. w/who                L. 显示系统内存的使用信息
(  ) 13. uptime               M. 显示文件系统剩余空间
(  ) 14. {pv,vg,lv}display    N. 显示在线用户
(  ) 15. findmnt              O. 截取出文件路径字符串中的目录名/文件名
(  ) 16. requota              P. 显示与PCI/USB总线连接的设备

2、 将 iptables 每种表与其可操作的链联系起来

(     ) 1. 用于包过滤的 filter 表                       A. PREROUTING 链
(     ) 2. 用于网络地址转换的 nat 表                    B. INPUT 链
(     ) 3. 用于改写包头的 mangle 表                     C. FORWARD 链
(     ) 4. 用于连接跟踪处理的 raw 表                    D. OUTPUT 链
(     ) 5. 用于配置强制访问控制的 security 表           E. POSTROUTING 链 	  

3、将 firewalld 各区与其默认开启的服务端口联系起来

(     ) 1. block                   A. ssh
(     ) 2. dmz                     B. dhcpv6-client
(     ) 3. drop                    C. ipp-client
(     ) 4. external             
(     ) 5. home                    D. mdns
(     ) 6. internal                 
(     ) 7. public                  E. samba-client
(     ) 8. trusted
(     ) 9. work                    F. 无

4、将下面的 firewall-cmd 命令与其功能联系起来

(  ) 01. firewall-cmd --zone=internal --remove-service=mysql
(  ) 02. firewall-cmd --zone=internal --list-ports
(  ) 03. firewall-cmd --add-forward-port=port=80:proto=tcp:toport=3128
(  ) 04. firewall-cmd --get-default-zone
(  ) 05. firewall-cmd --zone=internal --change-interface=enp0s3
(  ) 06. firewall-cmd --add-service=http
(  ) 07. firewall-cmd --list-services
(  ) 08. firewall-cmd --add-port=8080/tcp
(  ) 09. firewall-cmd --list-all
(  ) 10. firewall-cmd --add-forward-port=port=21:proto=tcp:toaddr=192.0.2.155
(  ) 11. firewall-cmd --list-forward-ports
(  ) 12. firewall-cmd --panic-on
(  ) 13. firewall-cmd --add-forward-port=port=22155:proto=tcp:toport=22:toaddr=192.0.2.155
(  ) 14. firewall-cmd --list-all-zones
(  ) 15. firewall-cmd --add-masquerade
(  ) 16. firewall-cmd --get-zones
(  ) 17. firewall-cmd --query-masquerade
(  ) 18. firewall-cmd --get-services
(  ) 19. firewall-cmd --get-zone-of-interface=enp0s3
(  ) 20. firewall-cmd --zone=internal --add-service=mysql

    A. 显示预定义的区
    B. 显示预定义的服务
    C. 显示默认区域
    D. 显示默认区域的所有规则
    E. 显示网络接口 enp0s3 对应的区域
    F. 将网络接口 enp0s3 对应的区域更改为 internal
    G. 允许访问默认区域的WWW服务
    H. 允许访问默认区域的 8080/tcp 端口号
    I. 允许访问 internal区域的 Mysql 服务
    J. 拒绝访问 internal区域的 Mysql 服务
    K. 显示默认区域允许访问的所有服务
    L. 显示 internal 区域允许访问的所有端口号
    M. 为默认区域开启IP伪装
    N. 显示默认区域是否开启了IP伪装
    O. 对默认区域的80端口的访问重定向到3128端口
    P. 对默认区域的21端口的访问重定向到192.0.2.155的21端口
    Q. 对默认区域的22155端口的访问重定向到 192.0.2.155 的22端口
    R. 显示默认区域设置的转发端口
    S. 丢弃所有的入站和出站流量并丢弃已建立的连接包
    T. 显示所有的区域及其规则信息
```

## 五、编程题


1、创建一个添加和删除组和用户的脚本，要求脚本调用格式为:

```
   # adusers <-a|-d>  <gname>  <num>

   例如：
   # adusers -a student 30
   将创建一个名为 student 的组，然后创建30个属于 student 组的用户，
   用户名为 student01～student30
   # adusers -d student 30
   将删除30个属于 student 组的用户，用户名为 student01～student30
   若 student 组中无其他成员，则同时删除组 student
```

2、某系统管理员需要做一些重复工作，编制一个解决方案：

```
(1) 每隔1小时从 /var/log/a.log 文件中找出包含"WARNING"或"FATAL",同时不包含"IGNOR"的行，
    然后，提取以":"分割的第1和第5个字段。
(2) 在每周日凌晨0：20 备份并压缩/etc 目录下的所有内容，存放在/backup 目录里，
    且文件名为如下形式 yyyymmdd_etc.tar.gz，其中 yyyy 为年，mm为月，dd 为日。
(3) 每天凌晨1：11 将/data 目录下的所有目录和文件 同步到 /backup/snapshots，
    然后将同步后的内容归档并压缩，存放在/backup 目录里，
    且文件名为如下形式 yyyymmdd_data.tar.xz，其中 yyyy 为年，mm为月，dd 为日。
	并检查是否存在两周前的 /backup/*_data.tar.xz 文件，若找到则删除之。
    shell 程序 databack.sh 存放在 /root/bin 目录下。	
(4) 每隔4小时检查一次当前系统文件系统空间使用情况，如果使用百分比达到90％，
    则给管理员发一封警告提示邮件。要求邮件内容同时包含主机名和IP地址信息。
	shell 程序 checkdisk.sh 存放在 /root/bin 目录下。
```

3、编写个 shell 脚本将 /data 目录下大于 1GB 的文件转移到 /tmp/gt1g 目录下

4、请尽量用一行命令完成如下的文本处理

4.1 根据 netstart 或 ss 的输出完成如下任务 

```
# netstat -tn
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address               Foreign Address             State
tcp        0      0 111.222.88.131:3306         182.16.22.178:1655          TIME_WAIT
tcp        0      0 111.222.88.131:3306         182.16.22.178:4593          TIME_WAIT
tcp        0      0 111.222.88.131:3306         182.16.22.178:1803          TIME_WAIT
tcp        0 416400 111.222.88.131:22           71.245.117.83:35556         ESTABLISHED
tcp        0      0 111.222.88.131:3306         182.16.22.178:2998          TIME_WAIT
tcp        0      0 111.222.88.131:3306         182.16.22.178:1804          TIME_WAIT
tcp        0      0 111.222.88.131:3306         182.16.22.178:2270          TIME_WAIT
tcp        0      0 127.0.0.1:3306              127.0.0.1:57756             ESTABLISHED
tcp        0      0 127.0.0.1:3306              127.0.0.1:57757             ESTABLISHED
tcp        0      0 111.222.88.131:3306         182.16.22.178:4917          TIME_WAIT
tcp        0      0 111.222.88.131:3306         182.16.22.178:1450          TIME_WAIT
tcp        0      0 111.222.88.131:3306         182.16.22.178:2141          TIME_WAIT
tcp        0      0 111.222.88.131:3306         182.16.22.178:4969          TIME_WAIT
tcp        0      0 111.222.88.131:3306         182.16.22.178:1270          TIME_WAIT
tcp        0    432 111.222.88.131:22           123.120.176.232:50095       ESTABLISHED
tcp        0      0 111.222.88.131:3306         182.16.22.178:4476          TIME_WAIT
tcp        1      0 ::1:47427                   ::1:8009                    CLOSE_WAIT
tcp        1      0 ::1:47200                   ::1:8009                    CLOSE_WAIT
tcp        1      0 ::1:47237                   ::1:8009                    CLOSE_WAIT
tcp        1      0 ::1:46765                   ::1:8009                    CLOSE_WAIT
tcp        1      0 ::1:47482                   ::1:8009                    CLOSE_WAIT
tcp        1      0 ::1:47472                   ::1:8009                    CLOSE_WAIT
tcp        1      0 ::1:47239                   ::1:8009                    CLOSE_WAIT
tcp        0      0 ::ffff:127.0.0.1:57757      ::ffff:127.0.0.1:3306       ESTABLISHED
tcp        1      0 ::1:46954                   ::1:8009                    CLOSE_WAIT
tcp        1      0 ::1:47473                   ::1:8009                    CLOSE_WAIT
tcp        1      0 ::1:47124                   ::1:8009                    CLOSE_WAIT
tcp        1      0 ::1:47230                   ::1:8009                    CLOSE_WAIT
tcp        0      0 ::ffff:127.0.0.1:57756      ::ffff:127.0.0.1:3306       ESTABLISHED
tcp        1      0 ::1:47202                   ::1:8009                    CLOSE_WAIT
tcp        1      0 ::1:47231                   ::1:8009                    CLOSE_WAIT
tcp        1      0 ::1:47273                   ::1:8009                    CLOSE_WAIT
tcp        1      0 ::1:47324                   ::1:8009                    CLOSE_WAIT

# ss -nt
State       Recv-Q Send-Q                   Local Address:Port                     Peer Address:Port
CLOSE-WAIT  1      0                                  ::1:47427                             ::1:8009
CLOSE-WAIT  1      0                                  ::1:47200                             ::1:8009
CLOSE-WAIT  1      0                                  ::1:47237                             ::1:8009
SYN-SENT    0      1                       111.222.88.131:59981                   93.184.216.34:25
CLOSE-WAIT  1      0                                  ::1:46765                             ::1:8009
CLOSE-WAIT  1      0                                  ::1:47482                             ::1:8009
CLOSE-WAIT  1      0                                  ::1:47472                             ::1:8009
CLOSE-WAIT  1      0                                  ::1:47239                             ::1:8009
ESTAB       0      0                     ::ffff:127.0.0.1:57757                ::ffff:127.0.0.1:3306
ESTAB       0      407592                  111.222.88.131:22                      71.245.117.83:35556
SYN-SENT    0      1                       111.222.88.131:59980                   93.184.216.34:25
CLOSE-WAIT  1      0                                  ::1:46954                             ::1:8009
CLOSE-WAIT  1      0                                  ::1:47473                             ::1:8009
SYN-SENT    0      1                       111.222.88.131:59978                   93.184.216.34:25
ESTAB       0      0                            127.0.0.1:3306                        127.0.0.1:57756
ESTAB       0      0                            127.0.0.1:3306                        127.0.0.1:57757
CLOSE-WAIT  1      0                                  ::1:47124                             ::1:8009
CLOSE-WAIT  1      0                                  ::1:47230                             ::1:8009
ESTAB       0      0                     ::ffff:127.0.0.1:57756                ::ffff:127.0.0.1:3306
CLOSE-WAIT  1      0                                  ::1:47202                             ::1:8009
SYN-SENT    0      1                       111.222.88.131:59982                   93.184.216.34:25
SYN-SENT    0      1                       111.222.88.131:59979                   93.184.216.34:25
CLOSE-WAIT  1      0                                  ::1:47231                             ::1:8009
ESTAB       0      0                       111.222.88.131:22                    123.120.176.232:50095
CLOSE-WAIT  1      0                                  ::1:47273                             ::1:8009
CLOSE-WAIT  1      0                                  ::1:47324                             ::1:8009
```

(4.1.1) 统计处于各状态的所有TCP连接连接数

(4.1.2) 统计出与本机Web服务已建立的连接数目

(4.1.3) 统计出与当前服务器已建立连接的远程IP及并发连接数并按降序输出

4.2 根据 access_log 的内容完成如下任务 

    192.168.33.1 - - [17/Sep/2016:08:40:44 +0800] "GET / HTTP/1.1" 200 10 "-" "curl/7.29.0"
    192.168.33.9 - - [17/Sep/2016:08:40:44 +0800] "GET / HTTP/1.1" 200 10 "-" "curl/7.29.0"
    192.168.33.9 - - [17/Sep/2016:08:40:45 +0800] "GET / HTTP/1.1" 200 10 "-" "curl/7.29.0"

(4.2.1) 找出 access_log 中请求最多的前十位 IP 地址

(4.2.2) 找出 access_log 中最后的1万行中请求最多的前十位 IP 地址

(4.2.3) 找出 access_log 中最近5分钟内请求最多的前十位 IP 地址


## 六、简答题


1、系统管理员的职责包括那些？管理的对象是什么？

2、简述 /etc/fstab 文件各个字段的含义?

3、什么是静态路由，其特点是什么？什么是动态路由，其特点是什么？

4、简述 /proc 文件系统以及 sysctl 的作用。

5、简述TCP三次握手的过程。

6、简述VPN，常见有哪几种？
