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
  * 导入 YUM 仓库的 GPG 密钥签名
        rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-7
* 配置国内镜像（方法二）
  * 用 `sed` 命令修改 epel 仓库配置文件配置使用清华大学的镜像地址
  * 清华大学开源镜像网址：http://mirrors.tuna.tsinghua.edu.cn
* 显示当前可用的仓库
* 为每个仓库在本地创建仓库元数据缓存

## 任务4：安装 LXC 

>* LXC 相关的 RPM 包在 EPEL 仓库中，请先配置 EPEL 仓库

```
yum install debootstrap perl libvirt
ip  # 显示 libvirt 创建的网桥设备


yum search lxc
yum -y install lxc lxc-templates
systemctl start lxc.service libvirtd
lxc-checkconfig

yum -y lxc-extra
echo "alias lxc-ls='lxc-ls --fancy'" >> ~/.bashrc
. ~/.bashrc
lxc-ls
```

## 任务5：创建和使用 LXC 容器

```
ll /usr/share/lxc/templates/
lxc-create -n c7-v1 -t centos
lxc-ls

lxc-start -d -n c7-h1 
lxc-attach -n c7-h1 -- passwd
lxc-attach -n c7-h1 -- yum install openssh-server
lxc-attach -n c7-h1 -- ip a

/usr/share/lxc/templates/lxc-download -l
lxc-create -n c6-v1 -t download -- -d centos -r 6 -a amd64
lxc-create -n d9-v1 -t download -- -d debian 

```

>**参考**
>
>* https://www.tecmint.com/install-create-run-lxc-linux-containers-on-centos/

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


## 任务9：配置网络连接（续）

* 为 centos 6 容器 配置网络连接 
* 为 debian 9 容器 配置网络连接

>* **要求** 均配置为 静态 IP 地址 （网段与 libvirt 创建的虚拟网桥一致）
>* **参考** [Common administrative commands in Red Hat Enterprise Linux 5, 6, and 7](https://access.redhat.com/articles/1189123)

