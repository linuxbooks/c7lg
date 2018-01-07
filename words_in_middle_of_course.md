# 写在配置网络服务之前

## 本课程与其他理论课程的关系

* 计算机网络技术
  * TCP/IP 网络
  * 应用层协议
* 网络与信息安全
  * PKI
  * TLS/SSL
* 操作系统原理
* 关系数据库原理

>###国外经典教材
>* 计算机网络
>  * [计算机网络：自顶向下方法（原书第6版）](https://item.jd.com/11556873.html)
>  * [计算机网络（第5版）](https://item.jd.com/10927233.html)
>* 网络与安全
>  * [密码编码学与网络安全：原理与实践（第六版）](https://item.jd.com/11670334.html)
>  * [计算机安全：原理与实践（原书第3版) ](https://item.jd.com/11888616.html)
>* 操作系统
>  * [现代操作系统（原书第4版）](https://item.jd.com/12139635.html)
>  * [操作系统――精髓与设计原理（第八版）](https://item.jd.com/12140626.html)
* 数据库
>  * [数据库系统概念（原书第6版](https://item.jd.com/10954261.html)
>  * [数据库系统：设计、实现与管理（基础篇）（原书第6版）](https://item.jd.com/11928293.html)

## 本课程与各个专业的关系

* 网络相关专业
  * 虚拟化与云平台技术
  * DevOps 与大规模应用部署
  * Python 语言编程
* 软件相关专业
  * DevOps 与软件工程
  * Web/APP 应用开发
* 硬件相关专业
  * 嵌入式开发
    * 基于微控制器 
      * [Arduino](https://www.arduino.cc/)
    * 基于 ARM 平台的 Linux 操作系统
      * [LEDE Project](https://lede-project.org/start)
      * [Alpine Linux](https://alpinelinux.org/)
      * Debian
  * 物联网 


>###参考
>* **Python 教材**
>  * [Python编程快速上手 让繁琐工作自动化](https://item.jd.com/11943853.html)
>  * [数据结构 Python语言描述](https://item.jd.com/12273412.html)
>  * [Python算法教程](https://item.jd.com/11841674.html)
>  * [Python极客项目编程](https://item.jd.com/12063813.html)
>* **Arduino 与物联网**
>  * [Arduino程序设计基础（第2版）](https://item.jd.com/11661917.html)
>  * [图解物联网](https://item.jd.com/12177484.html)
>  * [完美图解物联网IoT实操：使用JavaScript，Node.JS，Arduino，Raspberry Pi](https://item.jd.com/12160187.html)
>  * [从芯片到云端：Python物联网全栈开发实践](https://item.jd.com/12253128.html)  
>* **云平台**
>  * https://vinfrastructure.it/2013/07/iaas-vs-paas-vs-saas/
>  * https://en.wikipedia.org/wiki/DevOps
>  * https://en.wikipedia.org/wiki/DevOps_toolchain

## 如何学习网络服务

* 理解与某项服务相关的协议
  * 通用互联网协议
    * DHCP、DNS、NTP、SNMP
    * HTTP(s)、FTP(s)、SMTP(s)、POP3(s)、IMAP(s) 
  * 与操作系统相关的网络协议
    * RDP、SMB
    * SSH、NFS  
* 安装服务软件包
  * 查看服务软件包安装的执行文件和配置文件
  * 查看服务软件包安装的与 Linux 发布版本相关的 `README` 文件
  * 查看服务软件包安装的手册
* 查找某项服务的配置文档 
  * 发行版本的官方文档
    * https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/
    * https://help.ubuntu.com/
  * 知名 VPS 服务商提供的相关服务配置文档
    * https://www.linode.com/docs/
    * https://www.vultr.com/docs/
  * 服务软件的官方配置文档 