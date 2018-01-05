# CH09 Linux 防火墙

本章讲解 Linux 防火墙的相关概念及其配置方法。

* 防火墙
  * 防火墙的概念及分类
  * 包过滤防火墙
  * NAT 的概念及分类
* Linux 防火墙
  * Linux 防火墙组成
    * 内核空间：Netfilter
      * 链：`PREROUTING`、`INPUT`、`FORWARD`、`OUTPUT`、`POSTROUTING`
      * 表：**`filter`**、**`nat`**、`mangle`、`raw`、`security`
        * `filter` 表中的**自主访问控制（DAC）**过滤
        * `security` 表用以配合 SELinux 实现**强制访问控制（MAC）**过滤
    * 用户空间配置工具：`iptables`，... 
  * 连接跟踪与状态防火墙
    * 内核模块：`nf_conntrack.ko`, `nf_conntrack_*.ko`
    * 表： `/proc/net/nf_conntrack` (内核自动维护，一般无需认为干预)
    * 用户空间状态：**NEW**，**ESTABLISHED**，**RELATED** 、**INVALID**、**UNTRACKED**
  * 数据包在 Netfilter 多表/链中的穿越流程
    * 入站包（目标地址为防火墙）：`PREROUTING` -> `INPUT`
    * 出站包（源地址为防火墙）：OUTPUT -> POSTROUTING
    * 转发包（目标地址和源地址均不是防火墙）：`PREROUTING` -> `FORWARD` -> `POSTROUTING`
* firewalld 守护进程
  * 使用 firewall-cmd 工具配置基于 firewalld 的防火墙
  * `/etc/firewalld/firewalld.conf`
  * `/etc/firewalld/`
  * `/usr/lib/firewalld/`
* iptables 服务
  * 使用 lokkit 工具配置基于 iptables 服务的防火墙
  * `iptables-restore` 和 `iptables-save` 
  * `/etc/sysconfig/iptables-config`
  * `/etc/sysconfig/iptables`
* iptables 命令
  * iptables 命令语法
  * 编写基于 iptables 命令的防火墙脚本
  * 编写基于 iptables 规则集文件（`iptables-save`输出格式）的防火墙脚本


>* [CH09 - 教学指导](guidelines.md)
>* [CH09 - 实验指导 9.1](experiment_09-01.md)
>* [CH09 - 实验指导 9.2](experiment_09-02.md)
>* [CH09 - 家庭作业](assignments.md)
