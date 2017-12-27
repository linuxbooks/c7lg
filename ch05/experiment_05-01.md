# 实验指导 5 - 网络配置与包管理

>#### 学习目标
> * 网络配置
>   * 使用 `ip`/`ifconfig` 命令查看网络参数
>   * 使用 `nmcli/nmtui` 配置基于 NetworkManager 服务的网络连接
>   * 使用 `system-config-network-tui` 配置基于 network 服务的网络连接
>   * 直接修改网络配置文件配置网络连接 
>   * 禁用 一致的网络设备名
> * 网络工具
>   * 网络测试工具 `ping`、`ss`、`ip route`、`traceroute`、`dig`
>   * 网络客户工具 `wget`、`lftp`、`elinks`、`mail`
> * RPM 包管理
>   * 使用 `rpm` 命令 查询软件包
>   * 使用 `rpm` 命令 安装/卸载/升级/校验软件包
> * YUM 系统
>   * YUM 及其组件
>   * 使用 `yum` 命令 安装/卸载/升级/查询 软件包
>   * 使用 `rpm --import` 命令导入 YUM 仓库的 GPG 密钥签名
>   * 修改仓库配置文件配置远程 YUM 仓库（包括非官方仓库）
>   * 使用安装光盘配置本地 YUM 仓库


## 任务1：使用网络基本命令

* 显示所有设备的 IP 地址
* 显示所有连接的流量信息 
* 显示本地主机名
* 显示与本机连接的公网网关上的IP 
  * curl/elinks --dump
  * http://whatismyip.org
* 检测与 114.114.114.114 的连通性
* 检测与 8.8.8.8 的连通性（只发1次ICMP包，且等待1秒的响应时间）
* 显示本机路由表
* 检测 www.baidu.com 的 DNS 解析
* 指定使用 8.8.8.8 检测对 baidu.com 域 的 DNS 解析
* 显示到 www.baidu.com 的路由跟踪信息
* 显示所有网络套接字的连接
* 显示所有 tcp 类型网络套接字的连接
* 显示本机监听的所有 tcp 类型网络套接字的连接
* 给本机上的 tony 用户发送一个测试邮件，主题为 “test”，内容为 “hello”

>**参考**
>
>* https://www.linuxtrainingacademy.com/linux-ip-command-networking-cheat-sheet/
>* https://www.linuxtrainingacademy.com/determine-public-ip-address-command-line-curl/
>* [Common administrative commands in Red Hat Enterprise Linux 5, 6, and 7](https://access.redhat.com/articles/1189123)

## 任务2：配置网络连接

* 从宿主机（Windows/Mac/Linux）远程登录 CentOS 7 的虚拟机
  * 使用 VirtualBox 中配置的 Host-Only 网卡的配置连接
  * 如： `ssh root@192.168.56.71`
* 修改 VirtualBox 中配置的 NAT 网卡上配置的网络连接  
  * 这相当于你在机房的局域网里配置服务器的能与公网连通的 IP 地址
  * 查看 NAT 网卡对应的网络参数
  * 将当前 IP 地址值加10，其他参数均不变，使用 `nmcli` 为此连接重新设置静态网络参数
  * 重新激活，并检测修改
  * 检测与公网的连通性，并检测域名解析是否正常
  * 重新配置为动态获得网络参数

## 任务3：YUM 仓库管理

* 配置国内镜像（方法一）
  * 为官方仓库配置使用 163 的镜像
  * 参考 http://mirrors.163.com/.help/centos.html
* 安装配置 EPEL 仓库
  * 查询本机是否安装了 epel 仓库发行包
  * 搜索 epel 仓库发行包的包名称
  * 安装 EPEL 仓库
  * 导入 YUM 仓库的 GPG 密钥签名的公钥
        rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-7
* 配置国内镜像（方法二）
  * 用 `sed` 命令修改 epel 仓库配置文件配置使用清华大学的镜像地址
  * 清华大学开源镜像网址：http://mirrors.tuna.tsinghua.edu.cn
* 显示当前可用的仓库
* 为每个仓库在本地创建仓库元数据缓存

>**提示** 使用 `yum-utils` 包中提供的 `yum-config-manager` 命令可以管理 yum 的配置选项和仓库配置文件（如：启用/禁用指定的仓库、从一个URL配置仓库配置文件等）

## 任务4：安装 LXC 

>* LXC 相关的 RPM 包在 EPEL 仓库中，请先配置 EPEL 仓库

```
yum -y install debootstrap perl libvirt
systemctl is-enabled libvirtd
systemctl is-active libvirtd
systemctl start libvirtd
ip a # 显示 libvirt 创建的网桥设备


yum search lxc
yum -y install lxc lxc-templates
systemctl start lxc.service
lxc-checkconfig

yum -y install lxc-extra
echo "alias lxc-ls='lxc-ls --fancy'" >> ~/.bashrc
. ~/.bashrc
lxc-ls
```

## 任务5：创建和使用 LXC 容器

1、 通过不同发行模版创建容器

```
ll /usr/share/lxc/templates/

lxc-create -n c7-v1 -t centos
lxc-ls

## 在容器启动前，以 chroot 方式修改口令 
chroot /var/lib/lxc/c7-v1/rootfs passwd

## 启动指定的容器，-d 表示后台
lxc-start -d -n c7-v1 
## 在制定容器中直接执行命令
lxc-attach -n c7-v1 -- passwd  # 在容器启动后设置口令
lxc-attach -n c7-v1 -- yum install openssh-server
lxc-attach -n c7-v1 -- systemctl start sshd
lxc-ls
ssh [<User>@]<IP>

## 关闭指定容器
lxc-stop -n c7-v1

## 创建最新版的 debian 容器
#lxc-create -n d9-v1 -t debian
## 删除容器
#lxc-destroy -n d9-v1
```

2、 下载模版并创建容器

```
## 0. 显示可用的镜像模版
/usr/share/lxc/templates/lxc-download -l

## 1. 从下载的镜像文件创建 CentOS6 容器
lxc-create -n c6-v1 -t download -- -d centos -r 6 -a amd64

## 后台启动容器  c6-v1
lxc-start -d -n c6-v1 
## 在容器启动后，以 lxc-attach 方式修改口令
lxc-attach -n c6-v1 -- passwd
## 如果创建容器时配置了 tty，可通过如下命令连接到 tty 
## 还可以加 -t <n> 表示指定使用 ttyn 终端，默认为 tty1
lxc-console -n c6-v1 
## 登录后在容器中执行命令
yum install openssh-server
service sshd start
exit
#### 提示： <Ctrl-a> q 退出，返回到容器的宿主机

lxc-ls
ssh ...

## 2. 从下载的镜像文件创建 Debian 9 容器
lxc-create -n d9-v1 -t download -- -d debian -r stretch -a amd64
#lxc-create -n d8-v1 -t download -- -d debian -r jessie -a amd64

## 为 d9-v1 容器修改 PATH 环境变量
chroot /var/lib/lxc/d9-v1/rootfs
/bin/sed -i '$ i\export PATH=/bin:/sbin:$PATH' /root/.profile
source /root/.profile &> /dev/null
echo $PATH
exit

## 后台启动容器  d9-v1
lxc-start -d -n d9-v1

lxc-attach -n d9-v1 -- passwd
lxc-attach -n d9-v1 -- apt install openssh-server vim
lxc-attach -n d9-v1 -- vi ~/.bashrc
lxc-attach -n d9-v1 -- systemctl is-enabled sshd
lxc-attach -n d9-v1 -- systemctl is-active sshd
lxc-attach -n d9-v1 -- systemctl start sshd
lxc-ls
ssh ...

## 关闭指定容器
lxc-stop -n d9-v1
```

>**参考**
>
>* https://www.tecmint.com/install-create-run-lxc-linux-containers-on-centos/
>* http://wiki.libvirt.org/page/VirtualNetworking

## 任务6：rpm 命令

* 查询系统中安装的所有RPM软件包
* 查询系统中是否安装了名为 lxc 包
* 若安装了名为 `lxc` 包，在屏幕上显示 yes，否则显示 no
* 查找 /etc/shadow 文件是由哪个包安装的
* 查询 `libvirt` 包的发行信息 
* 查询 `libvirt-daemon` 包内置的安装前/后配置脚本
* 查询 `lxc` 包安装的所有文件
* 查询 `lxc` 包的依赖要求
* 校验 `lxc` 软件包


## 任务7：yum 命令

* 安装 zsh 软件包
* 使用 wget 下载最新的  usermin
  * http://www.webmin.com/download/rpm/usermin-current.rpm
* 安装下载到本地的 `usermin-current`.rpm
* 查询 `lxc` 包的发行信息
* 查询 `lxc` 包的依赖要求
* 当 EPEL 仓库未启用时，查询 lxc 包的依赖要求
* 查询什么软件包里提供了 `ifconfig` 和 `pstree`
* 查询所有的包名包含 httpd 的包
* 查询所有包组信息
* 删除 `usermin` 软件包
* 通过 YUM 事务历史删除已安装的 `zsh`

## 任务8：debian 包管理

* 请在 debian 9 的容器中学习
  * 与 rpm 功能对应的 `dpkg` 的使用
  * 与 yum 功能对应的 `apt`/`apt-get`  
  * 与 `rpm --import` 功能对应的 `apt-key add`


## 任务9：配置 CentOS 6 的网络连接

>### 关于网络服务
>* 静态
>  * network - CentOS 系列
>  * networking - Debian 系列
>* 动态
>  * NetworkManager 

---

>**提示** 
>* 网络服务： `network` 
>* 网络接口配置文件 `/etc/sysconfig/network-scripts/ifcfg-eth0` 
>* 主机名设置在 `/etc/sysconfig/network` 文件中
>* DNS 解析配置文件 `/etc/resolv.conf`
>* 配置的静态 IP 地址的网段应与 libvirt 创建的虚拟网桥一致

1、通过 lxc-console 或 ssh 登录 c6-v1 容器

    [root@c6-v1 ~]#

2、修改接口位置文件  `/etc/sysconfig/network-scripts/ifcfg-eth0` 

    DEVICE=eth0
    #BOOTPROTO=dhcp
    BOOTPROTO=none
    ONBOOT=yes
    HOSTNAME=c6-v1
    NM_CONTROLLED=no
    TYPE=Ethernet
    MTU=
    #DHCP_HOSTNAME=`hostname`
    IPADDR=192.168.122.161
    NETMASK=255.255.255.0
    GATEWAY=192.168.122.1

3、修改 DNS 解析文件 `/etc/resolv.conf`

    [root@c6-v1 ~]# echo "nameserver 192.168.122.1" > /etc/resolv.conf

4、确保 network 网络服务在开机时启动

    [root@c6-v1 ~]# chkconfig network on

5、退出容器登录

    [root@c6-v1 ~]# exit

   若使用 lxc-console 登入容器，则按 `<Ctrl-a> <q>` 返回宿主机的 shell

6、重新启动 c6-v1 容器的网络服务

    [root@host ~]# lxc-attach -n c6-v1 -- /sbin/service network restart

7、重新显示容器信息

    [root@host ~]# lxc-ls


>**参考**
>* [Common administrative commands in Red Hat Enterprise Linux 5, 6, and 7](https://access.redhat.com/articles/1189123)


## 任务10：配置 Debian 9 的网络连接

>**提示** 
>* 网络服务：`networking`
>* 网络接口配置文件 `/etc/network/interfaces` 
>* 主机名设置在 `/etc/hostname` 文件中
>* DNS 解析配置文件 `/etc/resolv.conf`
>* 设置的静态 IP 地址的网段应与 libvirt 创建的虚拟网桥一致


1、使用 chroot 命令切换到 d9-v1 容器的 root 文件系统

    [root@host ~]# chroot /var/lib/lxc/d9-v1/rootfs
    [root@host /]#

2、修改接口位置文件  `/etc/network/interfaces` 

```
[root@host /]# /bin/cat > /etc/network/interfaces <<_END
auto lo
  iface lo inet loopback

auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
  address 192.168.122.191
  netmask 255.255.255.0
  gateway 192.168.122.1
_END

```

3、修改 DNS 解析文件 `/etc/resolv.conf`

    [root@host /]# echo "nameserver 192.168.122.1" > /etc/resolv.conf

4、确保 networking 网络服务在开机时启动

    [root@host /]# /bin/systemctl enable networking

5、退出容器 chroot

    [root@host /]# exit

6、启动容器 d9-v1

    [root@host ~]# lxc-start -d -n d9-v1

7、重新显示容器信息

    [root@host ~]# lxc-ls


>**参考**
>* https://www.debian.org/doc/
>  * https://www.debian.org/doc/manuals/debian-reference/ch05.zh-cn.html

