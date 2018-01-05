# 实验指导 8 - 服务器安全

>#### 学习目标
> * 系统安全
>   * 设置 GRUB 的修改口令
>   * 禁用 `<Ctrl>`+`<Alt>`+`<Delete>` 重启
>   * 设置超时自动注销
>   * 限制 root 用户 bash 命令历史的记录条目数量
>   * 配置 `sudo` 并禁止 root 用户登录
>   * 使用 `rkhunter` 工具实现 rootkit 检查
>   * 使用 `aide` 工具实现重要文件的完整性检查
>   * 配置 root 用户仅能使用用户密钥而非用户口令登录 SSH 服务
>   * 将 SSH 服务运行于非标准端口 
> * 软件安全
>   * `yum update` 与 `yum upgrade` 的区别 
>   * `yum-cron` 获取每日安全更新通知或直接进行安全更新
> * 口令安全
>   * 使用 `pam_unix.so` 模块限制用户使用旧口令
>   * 使用 `pam_pwquality.so` 模块实现口令复杂性检查
>   * 使用 `pam_tally2.so` 模块实现登录失败的账户锁定  
>   * 口令时效
> * 访问控制
>   * 设置用户或组使用系统资源（文件打开数量） 
>   * 配置仅 wheel 组成员可以使用 su 和 sudo 命令
>   * 使用 `TCP Wrappers` 实现基于 主机/网络 的访问控制
>   * 使用 `fail2ban`/`denyhost` 工具保护 SSH 服务
> * 信息与数据安全
>   * 使用对称加密算法加解密文件
>   * 校验文件的 GPG 数字签名
>   * 创建 SSL/TLS 自签名证书
> * 漏洞检测
>   * 使用 `lynis` 安全审计工具检测系统漏洞
>   * 根据 `lynis` 报告提示加固系统

## 任务1：物理安全

* 设置 GRUB 的修改口令
* 禁用 `<Ctrl>`+`<Alt>`+`<Delete>` 重启

## 任务2：登录安全

* 设置 bash 超时自动注销
* 限制 root 用户 bash 命令历史的记录条目数量为 10
* 配置仅 tony 用户可以使用 sudo 实现完全功能访问
* 禁止 root 用户以口令方式登录（口令锁定）
* 用户 root 的 SSH 登录策略 
  * 禁止 root 用户登录 SSH 服务
  * 配置 root 仅能使用用户密钥而非用户口令登录 SSH 服务

## 任务3：软件安全

* 安装 `yum-cron` 
* 配置 `yum-cron`
  * 获取每日安全更新通知
  * 发送到你自己的邮箱

## 任务4： 服务安全

* 关闭无必要 `vfstpd` 服务 
* 关闭无必要 `nfs` 服务 
* 关闭 `NetworkManager` 服务
* 关闭无必要 `ntpd` 和 `chronyd` 服务
  * 使用 `ntpdate` 命令安排每日周期任务进行时间同步

>**将不同的 服务/应用 分散部署在不同的 服务器/虚拟机/容器**

## 任务5：口令安全

* 记住最近使用的5个口令，在设置新口令时不能使用
* 口令质量检查 （/etc/security/pwquality.conf）
  * 口令必须大于12个字符
  * 必须至少包含四类字符中的一个
* 口令时效
  * 对新创建用户设置 90 天后必须重新修改口令
  * 对现存的 tony 用户设置 90 天后必须重新修改口令
* 账户锁定
  * 5 次登录失败进行登录锁定
  * 20 分钟后自动解锁  

## 任务6：访问控制

* 为 apache 用户设置打开文件数的限制为 65535
* 配置仅 wheel 组成员可以使用 su 和 sudo 命令
* 安装 `denyhosts` 工具基于 `TCP Wrappers` 实现对 SSH 服务的主机访问控住保护

## 任务7：文件加密与解密

* 显示 openssl 支持的所有兑成加密算法
* 使用 aes128 加密算法对 /root/anaconda-ks.cfg 文件加密
  * 加密后的文件为  /root/anaconda-ks.cfg.mi
* 对 /root/anaconda-ks.cfg.mi 文件进行解密 
  * 加密后的文件为  /root/anaconda-ks.cfg.new
* 使用 `diff` 命令比对解密文件与源文件

## 任务8：校验 RPM 包的数字签名

* 查询已导入 RPM 数据库的所有 GPG 公钥信息
  * 要求显示 summary，version 和 release 信息 
* 使用 wget 下载最新的  usermin RPM包，以及其 GPG 签名的公钥
  * http://www.webmin.com/download/rpm/usermin-current.rpm
  * http://www.webmin.com/jcameron-key.asc
* 将此 GPG 签名的公钥文件 `jcameron-key.asc` 导入 RPM 数据库
* 再次查询已导入 RPM 数据库的所有 GPG 公钥信息
* 验证 usermin-current.rpm 文件的 GPG 签名


## 任务9：校验文件的数字签名

* 校验 sha256sum.txt.asc 文件的 GPG 签名从而确认此文件确实是 CentOS 发布的
      wget http://mirrors.163.com/centos/7/isos/x86_64/sha256sum.txt.asc
* 下载 CentOS 的 GPG 公钥文件
      wget http://mirror.centos.org/centos/RPM-GPG-KEY-CentOS-7
* 显示 GPG 公钥文件的密钥指纹
      gpg --quiet --with-fingerprint ./RPM-GPG-KEY-CentOS-7
* 将 GPG 公钥导入本机的 GPG 公钥链
      gpg --import ./RPM-GPG-KEY-CentOS-7 
* 校验 sha256sum.txt.asc 的 GPG 签名 
      gpg --verify ./sha256sum.txt.asc

* 校验你下载的 CentOS/LinuxMint 发行版的 ISO 文件及其 GPG 数字签名
>   * CentOS - 参考 https://wiki.centos.org/Download/Verify
>   * LinuxMint - 参考 ttp://linuxmint-installation-guide.readthedocs.io/en/latest/verify.html

> **提示** 若 ISO 文件下载在 Windows 上，可以使用 git-for-windows 中集成的 gpg 工具完成

## 任务10：自签名 SSL/TLS 证书

* 创建单域名自签名证书文件及其私钥
  * 证书文件 ftp.olabs.lan.crt
  * 私钥文件 ftp.olabs.lan.key
* 创建多域名自签名证书文件及其私钥文件
  * 证书文件 myservers.crt
  * 私钥文件 myservers.key
  * 多域名 
    * olabs.lan www.olabs.lan wiki.olabs.lan 
    * olabs.net www.olabs.net wiki.olabs.net 
    * olabs.org www.olabs.org wiki.olabs.org 

## 任务11*：由本地 CA 签署证书模拟证书签署过程

* 在 Windows 上创建本地 CA
  * 安装基于 OpenSSL 的前端开源 GUI 工具 [xca](https://sourceforge.net/projects/xca/) 
  * 创建 CA 的证书和私钥
* 在 Linux 上生成证书签名请求文件
  * ftp.olabs.lan.csr
  * myservers.csr 
* 在 Windows 上使用本地 CA 签署证书
  * 将 Linux 上生成的 CSR 文件共享给 Windows （如 scp） 
  * 使用本地 CA 签署 CSR 文件并生成 CRT 证书文件
  * 将生成的 CRT 证书文件共享给 Linux （如 scp） 


## 任务12*：RKHunter ： Check Rootkit

* 安装 RKHunter
* 配置文件：`/etc/rkhunter.conf`
* 检查系统上的 Rootkit

>**参考** [RKHunter : Detect Rootkit](https://www.server-world.info/en/note?os=CentOS_7&p=rkhunter)

## 任务13*： AIDE ： Host based IDS

* 安装 AIDE
* 配置文件：`/etc/aide.conf`
* 生成检测数据库
* 检查系统上的重要文件变化，实现基于主机的入侵检测
* 确认更改安全后重新生成检测数据库

>**参考** [AIDE: Host based IDS](https://www.server-world.info/en/note?os=CentOS_7&p=aide)

## 任务14： 漏洞检测

* 安装 `lynis` 
* 首次执行 `lynis audit system`
* 使用 `lynis -c` 扫描整个系统
* 根据 `lynis` 报告提示加固系统

>**参考**
>* https://cisofy.com/documentation/lynis/get-started/
>* `man lynis`