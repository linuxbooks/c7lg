# 实验指导 9.1 - Linux 防火墙

>#### 学习目标
> * 使用 `firewall-cmd` 或 `firewall-config` 工具配置基于 firewalld 守护进程的防火墙
> * 使用 `lokkit` 或`system-config-firewall-tui` 工具配置基于 iptables 服务的防火墙
> * 编写基于 `iptabls` 命令的防火墙脚本
> * 编写基于 `iptables-save` 命令输出文件格式的防火墙脚本


## 任务1：firewalld 防火墙 -- 主机防火墙（单网卡）

* 安装并启动 firewalld
* 使用 `firewall-cmd` 命令完成如下操作 
  * 显示当前的默认区域
  * 显示当前已经激活的区域
  * 显示默认区域的所有规则
  * 显示默认区域内允许访问的所有服务
  * 显示默认区域内允许访问的所有端口
  * 显示 firewalld  预定义的服务（名称）
  * 允许访问 http、https 、syslog 服务
  * 允许访问 81 （TCP）端口 
  * 禁止访问 syslog 服务
  * 仅允许 192.168.56.30 的主机访问 syslog 服务
  * 禁止 192.168.56.30 的主机访问 http 服务
  * 使上述配置持久化（下次启动 firewalld 时生效）
* 在适当的客户端进行测试

>**提问** 下面两条命令的作用
>* `firewall-cmd --get-services | grep -wo http`
>* `firewall-cmd --get-services | tr ' ' '\n' | grep  http`


## 任务2：基于 2222 端口的 SSH 服务的 firewalld  防火墙

1. 配置 SSH 服务
  * 设置端口为 2222
  * 重新加载配置
2. 自定义 firewalld 的规则配置文件
  * 复制默认的 SSH 规则文件到 `/etc/firewalld/services/`
  * 修改复制后的 `/etc/firewalld/services/ssh.xml`， 将 22 端口改为 2222
  * 重新加载防火墙配置  
3. 配置 fail2ban
  * 安装 fail2ban
  * 创建本地配置文件 `/etc/fail2ban/jail.local`
          [DEFAULT]
          findtime = 900
          [sshd]
          enabled = true
          bantime = 3600
          maxretry = 5
          port=2222
  * 设置 fail2ban 立即/开机 启动


## 任务3：SSH X11 Forwarding

* 服务器端
  * 安装 `xauth`
  * 配置 SSH 服务器开启 `X11Forwarding`
  * 重新加载 sshd 配置文件
  * 安装 `firewall-config`
* 客户端
  * 安装 Xming
  * 配置 Putty 中的 ssh 会话启用 `X11Forwarding`
  * 连接已配置的 ssh 会话
  * 执行 GUI 工具 `firewall-config` 配置防火墙

>* [Xming](https://xming.en.softonic.com/)
>* [PuTTY+Xming 实现 X11 的 ssh 转发](http://blog.csdn.net/smstong/article/details/46328247)

## 任务4：firewalld 防火墙 -- 网关防火墙（多网卡）

>**配置环境**
>* 防火墙主机（CentOS 7 VirtualBox 虚拟机）有 2 块物理网卡
>  * NAT 类型网卡 （自动获得网络参数）
>  * host-only 网卡 （192.168.56.71/24） 
>  * libVirtd 虚拟网桥 （192.168.122.1/24）
>    * c7-v1 容器 （192.168.122.71/24）
>* 服务器主机（CentOS 7 VirtualBox 虚拟机）有 1 块网卡
>  * host-only 网卡 （192.168.56.30/24） 
>* Window 宿主机 
>  * host-only 虚拟网桥 （192.168.56.1/24） 
>  * 能连接公网 （有线/无线）

* 配置防火墙主机 
  * 显示 firewalld 预定义的区域
  * 显示 firewalld 预定义的区域的所有规则
  * 仅显示 `work` 区域的所有规则
  * 显示当前已经激活的区域
  * 显示默认区域的所有规则
  * 将默认区域设置为 `work`
  * 将 VirtualBox 虚拟机中设置为 NAT 的网卡对应的设备设置为 `external` 区域
  * 绑定源地址 192.168.122.0/24 到 `public` 区域
  * 显示 `public` 区域的所有规则
  * 重新显示当前已经激活的区域
  * 允许访问  `external` 区域的 http、https 服务
  * 允许访问  `external` 区域的81 （TCP）端口 
  * 仅允许 192.168.56.30 的主机访问 `work` 区域（默认）的 syslog 服务
  * 删除 `external` 区域上默认设置的 IP 伪装功能
  * 显示 `external` 区域的所有规则
  * 添加 `work` 区域上对 `192.168.56.0/24` 的 IP 伪装功能
  * 在 `work` 区域（默认）上，将对 192.168.56.71:22/tcp 的访问重定向到新克隆的系统 192.168.56.30 的 22 端口
  * 在 `work` 区域（默认）上，将对 192.168.56.71:2022/tcp 的访问重定向到 c7-v1 容器的 22 端口
  * 显示 `work` 区域的所有规则
  * 显示 `public` 区域的所有规则
  * ......
  * 使上述配置持久化（下次启动 firewalld 时生效）
* 测试
  * 在防火墙主机上测试
        ping 192.168.56.1 
        ping 192.168.56.30
        ping 192.168.122.71

        ssh  192.168.122.71
        ssh -p 2222 192.168.122.71

        ssh 192.168.56.30
  * 在 Windows （192.168.56.1）上测试
        ssh -p 22     root@192.168.56.71
        ssh -p 2222   root@192.168.56.71
        ssh -p 2022   root@192.168.56.71
  * 在服务器主机（新克隆的虚拟机）上，测试 IP 伪装 
        elinks --dump http://whatismyip.org

>**提问**  下面命令的帮助输出中只有 **[Z]** 而没有 **[P]** 说明了什么？如何持久化地将一个网络接口绑定到一个 firewlld 的区域？
>```
># firewall-cmd --help |grep -A1 '\--change-interface='
>  --change-interface=<interface>
>                       Change zone the <interface> is bound to [Z]
>```
>**参考**
>* https://fedoraproject.org/wiki/Firewalld?rd=FirewallD
>* http://firewalld.org/

## 任务5：iptables 防火墙

1. 关闭 firewalld 并切换使用基于 iptables 服务的防火墙
   * 关闭并禁用 `firewalld`
   * 安装 `iptables-services` 和 `system-config-firewall-tui`
   * 启动并设置开机启动 `iptables` 服务
2. 配置  `iptables` 防火墙
   * 直接修改规则集文件 `/etc/sysconfig/iptables` 配置 
   * 使用  `system-config-firewall-tui` 或 `lokkit` 配置
3. 重新加载防火墙配置

>**提示** 你也可以在  c6-v1 容器上练习配置 iptables 主机防火墙


## 任务6：iptables 脚本

* 基于 `iptables-save` 命令输出文件格式的防火墙脚本
  * **参考** https://github.com/fcaviggia/hardened-centos7-kickstart/blob/master/config/hardening/iptables.sh
* 基于 `iptabls` 命令的防火墙脚本
  * **参考** http://easyfwgen.morizot.net/gen/index.php 
  * **参考** http://www.malibyte.net/iptables/scripts/fwscripts.html


## 任务7：Debian 防火墙

* 配置 Debian 系列服务器的防火墙
  * [Debian Firewall](https://wiki.debian.org/DebianFirewall)

>**参考**
>* [Debian VPS 系统 iptables 防火墙使用教程](https://yq.aliyun.com/ziliao/70072)
>* [Debian/Ubuntu系统中安装和配置 UFW](http://blog.csdn.net/jb19900111/article/details/18552913)
>* [ubuntu server guide -- firewall](https://help.ubuntu.com/lts/serverguide/firewall.html)
>* [Ufw 使用指南](http://wiki.ubuntu.org.cn/Ufw使用指南)




