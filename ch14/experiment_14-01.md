# 实验指导 14 - Apache 静态站点

>#### 学习目标
>* Apache 的基本配置与安全设置
>* 配置每个系统用户的 Web 站点
>* 使用别名机制配置“虚拟目录”
>* 配置主机访问控制和用户访问控制
>* 配置基于 IP 和 Port 的虚拟主机
>* 配置基于 域名 的虚拟主机
>* 配置基于 SSL/TLS 的虚拟主机
>* 配置 URL/URI 重定向

## 任务1：基本配置与安全设置

### 要求

* 设置服务器名和管理员Email
* 开启 HTTP 的 `KeepAlive` 功能
* 禁用 `/etc/httpd/conf.d/welcome.conf` 配置文件
* 避免服务器信息外泄，控制服务器回应给客户端的应答头
* 控制服务器不显示生成页面的页脚的信息
* 安装配置 mod_evasive 模块防止 DoS 攻击

### 步骤

* 安装 Apache2.4
* 设置服务器名和管理员Email（请根据实际修改）
  * 假定服务器名为 `www.olabs.lan`
* 开启 HTTP 的 `KeepAlive` 功能
* 避免显示测试页面而暴露系统信息
  * 禁用 `/etc/httpd/conf.d/welcome.conf` 配置
  * 生成默认站点主页文件，其内容为 `<H1>It Works!</H1>`
* 避免服务器信息外泄，创建 `/etc/httpd/conf.d/security.conf`
  * 控制服务器回应给客户端的 `Server:` 应答头仅显示 `Apache`
  * 控制服务器不显示生成页面的页脚的信息
* 安装配置 mod_evasive 模块防止 DoS 攻击
  * 安装 EPEL 仓库提供的 mod_evasive
  * 配置 `/etc/httpd/conf.d/mod_evasive.conf`   
* 配置防火墙开启对 http 服务的访问
* 检查配置文件语法的正确性
* 配置 httpd 的开机启动和立即启动
* 使用支持 HTTP 协议的客户端进行测试
  * 本机：`curl --head http://localhost` 
  * 本机：`curl -vsI http://localhost | egrep '^(>|<)'`
  * 本机：`elinks http://localhost`
  * 本机：`elinks http://192.168.56.71`
  * 本机：`elinks http://www.olabs.lan`
  * Windows : http://IPorFQDN
* 查看 Apche 默认的错误日志和访问日志文件
* 使用 `ab` 命令进行压力测试
      ab -n 10000 -c 100 http://localhost/

>**参考**
>* curl 的常用选项
>  * `curl --help|egrep ' \-(I|L|s|S|v)'`
>* [Configure mod_evasive](https://www.server-world.info/en/note?os=CentOS_7&p=httpd2&f=4)

## 任务2：配置每个系统用户的 Web 站点

### 要求

配置每个系统用户的 Web 站点，并以 tony 用户为例进行测试

### 步骤

* 修改 `/etc/httpd/conf.d/userdir.conf` 文件
  * 为每个系统用户指定 Web 站点的文档根目录 `public_html`
* 检查语法正确性并重新启动Apache 
* 为 tony 用户准备 Web 站点 
      # useradd tony
      # mkdir -m 700 ~tony/public_html
      # echo "Test for tony." > ~tony/public_html/index.html
      # chown -R tony.tony ~tony/public_html
      # ls -ld  ~tony  ~tony/public_html
      # setfacl -m u:apache:x ~tony
      # setfacl -m u:apache:x ~tony/public_html
* 在客户端进行浏览测试
  *  http://IPorFQDN/~tony

## 任务3：主机访问控制、别名机制和目录列表

### 要求

* 假设 Apache 主机的 IP 为 192.168.56.71
* 配置 仅允许本地回环网络或 192.168.56.0/24 访问别名 /yum
* 对别名 /yum 所映射的文件系统目录开启目录列表功能

### 步骤

* 创建 `/etc/httpd/conf.d/pxe.conf` 文件
 * 将对 `/yum` 的别名访问映射到文件系统 `/var/ftp/yum`
 * 对目录 `/var/ftp/yum` 设置访问控制
   * 开启目录列表功能
   * 使用 CentOS 中 Apache 默认的目录列表选项配置 （`conf.d/autoindex.conf`）
   * 仅允许本地回环网络或 192.168.56.0/24 访问
* 检查语法正确性并重新启动Apache 
* 在客户端进行浏览测试
  * 本地：http://localhost/yum
  * 远程：http://192.168.56.71/yum
  * 远程：http://www.olabs.lan/yum

>**提示**
>* 在 192.168.56.0/24 之外的主机上测试，例如在 c6-v1 容器里测试 

## 任务4：主机访问控制与用户访问控制

### 要求

* 假设 Apache 主机的 IP 为 192.168.56.71
* 配置仅在 localhost 上可以直接访问 http://127.0.0.1/server-status
* 配置在 localhost 之外对 http://192.168.56.71/server-status 的访问启用 HTTP 基本认证
* 配置仅在 192.168.56.0/24 的网络上可以使用 HTTP 摘要用户认证访问 http://192.168.56.71/sec/

### 步骤
* 为 mod_status 模块设置基本认证的用户访问控制
  * 创建 `/etc/httpd/conf.d/server-status.conf` 文件
    * 配置 Location 容器 /server-status 设置访问控制
    * 开启 mod_status 模块生成服务器状态信息
    * 在 127.0.0.1 上可以直接访问
    * 在 127.0.0.1 之外的网络上使用用户认证访问
      * 使用 HTTP 的基本认证
      * jason 用户可以使用口令 JaP455 访问
  * 使用 `htpasswd` 命令设置基本认证口令文件 `/etc/httpd/.bpasswd` 
* 为 `/var/www/html/sec` 目录设置摘要认证的用户访问控制
  * 创建 `/etc/httpd/conf.d/sec-digest.conf` 文件
    * 配置 `/var/www/html/sec` 目录设置访问控制
    * 仅在 192.168.56.0/24 的网络上可以使用用户认证访问
      * 使用 HTTP 的摘要认证
      * jason 用户可以使用口令 `JaP455` 访问
  * 使用 `htdigest` 命令设置摘要认证口令文件 `/etc/httpd/.dpasswd` 
* 检查语法正确性并重新启动 Apache 
* 在客户端进行浏览测试
  * 本地：`apachectl fullstatus`
  * 本地：`elinks http://127.0.0.1/server-status`
  * 本地：`elinks http://127.0.0.1/sec/`
  * 本地：`elinks http://192.168.56.71/sec/`
  * 远程：http://IPorFQDN/server-status
  * 远程：http://IPorFQDN/sec/


>**提示**
>* 在 192.168.56.0/24 之外的主机上测试，例如在 c6-v1 容器里测试 


## 任务5：基于 IP 和 Port 的虚拟主机

### 要求

* 假设 Apache 主机的 IP 为 192.168.56.71
* 配置基于端口号的 虚拟主机 http://192.168.56.71:8888
* 配置基于 IP 的 虚拟主机 http://192.168.56.111

### 准备

* 准备虚拟站点目录和 index.html 文件
      # mkdir -p /srv/www/192.168.56.{111_80,71_8888}/{htdocs,logs}
      # for i in 192.168.56.{111_80,71_8888} ;\ 
          do echo "$i" > /srv/www/$i/htdocs/index.html ; done 
      # tree /srv/www
```
/srv/www/
├── 192.168.56.111_80
│     ├── htdocs
│     │   └── index.html
│     └── logs
└── 192.168.56.71_8888
        ├── htdocs
        │   └── index.html
        └── logs
```
* 准备被 Apache 主配置文件包含的用于存放虚拟主机配置文件的目录
      # mkdir /etc/httpd/vhosts.d
      # echo 'IncludeOptional vhosts.d/*.conf' >> /etc/httpd/conf/httpd.conf

### 步骤

* 配置基于端口号的虚拟主机
  * 创建  `/etc/httpd/vhosts.d/192.168.56.71_8888.conf`
    * 配置虚拟主机的文档根目录为  `/srv/www/192.168.56.71_8888/htdocs`
* 配置基于 IP 的虚拟主机
  * 为本机的 host-Only 网卡绑定第2个IP地址 192.168.56.111/24
  * 创建  `/etc/httpd/vhosts.d/192.168.56.111.conf`
    * 配置虚拟主机的文档根目录为  `/srv/www/192.168.56.111_80/htdocs`
* 检查语法正确性并重新启动 Apache 
* 配置防火墙允许访问 8888 端口
* 配置域名解析 （bind 或 /etc/hosts）
  * 将 `h111.olabs.lan` 的 IP 设置为地址 192.168.56.111
* 在客户端进行浏览测试
  * `elinks http://192.168.56.71:8888`
  * `elinks http://www.olabs.lan:8888`
  * `elinks http://192.168.56.111`
  * `elinks http://h111.olabs.lan`

## 任务6：基于 域名 的虚拟主机

### 要求

* 创建由 root 管理的 www.olabs.net 和 wiki.olabs.net 的虚拟主机
* 创建由 olabsorg 管理的 www.olabs.org 和 wiki.olabs.org 的虚拟主机

### 准备

* 为 root 用户准备虚拟站点目录和 index.html 文件
      # mkdir -p /srv/www/olabs.net/{www,wiki}/{htdocs,logs,conf}
      # echo "www.olabs.net" > /srv/www/olabs.net/www/htdocs/index.html 
      # echo "wiki.olabs.net" > /srv/www/olabs.net/wiki/htdocs/index.html
* 为 olabsorg 用户准备虚拟站点目录和 index.html 文件
      # useradd -d /srv/www/olabs.org  olabsorg
      # su - olabsorg -c "mkdir -p ~olabsorg/{www,wiki}/{htdocs,logs,conf}"
      # su - olabsorg
      $ echo "www.olabs.org" > www/htdocs/index.html
      $ echo "wiki.olabs.org" > wiki/htdocs/index.html
      $ exit
* 显示 /srv/www 目录结构
      # tree /srv/www
```
/srv/www
├── olabs.net
│   ├── wiki
│   │   ├── conf
│   │   ├── htdocs
│   │   │   └── index.html
│   │   └── logs
│   └── www
│       ├── conf
│       ├── htdocs
│       │   └── index.html
│       └── logs
└── olabs.org
      ├── wiki
      │   ├── conf
      │   ├── htdocs
      │   │   └── index.html
      │   └── logs
      └── www
          ├── conf
          ├── htdocs
          │   └── index.html
          └── logs
```
* 准备被 Apache 主配置文件包含的用于存放虚拟主机配置文件的目录
```
grep 'vhosts.d' /etc/httpd/conf/httpd.conf &> /dev/null \
  || echo 'IncludeOptional vhosts.d/*.conf' >> /etc/httpd/conf/httpd.conf
```

### 步骤

* 创建  `/etc/httpd/vhosts.d/olabs.org.conf`
  * 配置 www.olabs.org 的虚拟主机
    * 配置虚拟主机的文档根目录为  `/srv/www/olabs.org/www/htdocs` 
    * 配置虚拟主机的错误日志为 `/srv/www/olabs.org/www/logs/error_log`
    * 配置虚拟主机的访问日志为 `/srv/www/olabs.org/www/logs/access_log`
  * 配置 wiki.olabs.org 的虚拟主机
    * 配置虚拟主机的文档根目录为  `/srv/www/olabs.org/wiki/htdocs` 
    * 配置虚拟主机的错误日志为 `/srv/www/olabs.org/wiki/logs/error_log`
    * 配置虚拟主机的访问日志为 `/srv/www/olabs.org/wiki/logs/access_log`
* 创建  `/etc/httpd/vhosts.d/olabs.net.conf`
  * 配置 www.olabs.net 的虚拟主机 
    * 配置虚拟主机的文档根目录为  `/srv/www/olabs.net/www/htdocs` 
    * 配置虚拟主机的错误日志为 `/srv/www/olabs.net/www/logs/error_log`
    * 配置虚拟主机的访问日志为 `/srv/www/olabs.net/www/logs/access_log`
  * 配置 wiki.olabs.net 的虚拟主机
    * 配置虚拟主机的文档根目录为  `/srv/www/olabs.net/wiki/htdocs` 
    * 配置虚拟主机的错误日志为 `/srv/www/olabs.net/wiki/logs/error_log`
    * 配置虚拟主机的访问日志为 `/srv/www/olabs.net/wiki/logs/access_log`
* 创建  `/etc/httpd/vhosts.d/olabs.lan.conf`
  * 为主服务器配置默认虚拟主机，域名为 `www.olabs.lan`
    * `<VirtualHost _default_:80>` 
* 为所有虚拟主机配置日志滚动
```
if [ -e /etc/logrotate.d/httpd_vhosts ] ; then :
else
   cp /etc/logrotate.d/httpd{,_vhosts}
   sed -i 's#/var/log/httpd#/srv/www/*/*/logs#' /etc/logrotate.d/httpd_vhosts
fi
```
* 配置域名解析 （bind 或 /etc/hosts）
  * 将 {www,wiki}.olabs.{org,net} 的 IP 设置为本机地址 192.168.56.71
* 检查语法正确性并重新启动 Apache 
* 检查 Apache 基于域名的虚拟主机配置
* 在客户端进行浏览测试
  * `elinks http://www.olabs.net`
  * `elinks http://wiki.olabs.net`
  * `elinks http://www.olabs.org`
  * `elinks http://wiki.olabs.org`
  * `elinks http://www.olabs.lan`


## 任务7：基于 SSL/TLS 的 虚拟主机

### 要求

* 配置对 www.olabs.lan 的 HTTPS 访问
* 配置对 wiki.olabs.net 的 HTTPS 访问

### 步骤

* 安装 mod_ssl
* 为默认虚拟主机配置 SSL/TLS
  * 修改 `/etc/httpd/conf.d/ssl.conf` 
    * 使用 第8章 任务10 创建的证书和私钥文件 `myservers.{crt,key}` 
* 为 wiki.olabs.net 虚拟主机配置 SSL/TLS
  * 修改 `/etc/httpd/vhosts.d/olabs.net.conf`
    * 创建 wiki.olabs.net:443 虚拟主机
    * 使用 第8章 任务10 创建的证书和私钥文件 `myservers.{crt,key}` 
* 检查语法正确性并重新启动 Apache 
* 检查 Apache 基于域名的虚拟主机配置
* 配置防火墙允许访问 https 服务
* 在客户端进行浏览测试
  * `https://www.olabs.lan`
  * `https://wiki.olabs.net`

## 任务8：重定向

### 要求

* 将 http://olabs.org 永久重定向到 http://www.olabs.org
* 将 http://dl.olabs.org 永久重定向到 http://www.olabs.org/download
* 将 http://wiki.olabs.net 永久重定向到 https://wiki.olabs.net
* 将 http://help.olabs.net 永久重定向到 https://wiki.olabs.net

### 步骤

1. 将 http://olabs.org 永久重定向到 http://www.olabs.org
  * 修改 `/etc/httpd/vhosts.d/olabs.org.conf` 
    * 创建基于域名 olabs.org 的虚拟主机
      * 永久重定向到 http://www.olabs.org 
2. 将 http://dl.olabs.org 永久重定向到 http://www.olabs.org/download
  * `mkdir /srv/www/olabs.org/www/htdocs/download`
  * 修改 `/etc/httpd/vhosts.d/olabs.org.conf` 
    * 创建基于域名 dl.olabs.org 的虚拟主机
      * 永久重定向到 http://www.olabs.org/download 
3. 将 http://wiki.olabs.net 永久重定向到 https://wiki.olabs.net
  * 修改 `/etc/httpd/vhosts.d/olabs.net.conf` 
    * 修改基于域名 wiki.olabs.net:80 的虚拟主机
      * 永久重定向到 https://wiki.olabs.net 
4. 将 http://help.olabs.net 永久重定向到 https://wiki.olabs.net
  * 修改 `/etc/httpd/vhosts.d/olabs.net.conf` 
    * 创建基于域名 help.olabs.net 的虚拟主机
      * 永久重定向到 https://wiki.olabs.net 
5. 重新加载 Apache 配置
  * 检查 Apache 基于域名的虚拟主机配置
  * 检查语法正确性并重新启动 Apache 
6. 配置域名解析 （bind 或 /etc/hosts）并测试
  * 将 {,dl.}olabs.org、{help,wiki}.olabs.net 的 IP 设置为本机地址 192.168.56.71
  * 在客户端进行浏览测试
         curl -I http://olabs.org
         curl -IL http://olabs.org
         curl -I http://download.olabs.org
         curl -IL http://download.olabs.org
         curl -I http://wiki.olabs.net
         curl -IL http://wiki.olabs.net
         curl -I http://help.olabs.net
         curl -IL http://help.olabs.net

## 任务9*：限制每 IP 的最大连接数和限速

### 要求

* 为 http://www.olabs.org/download 的访问限制带宽为 500 KB/sec
* 为 http://www.olabs.org/download 的访问限制每个 IP 的最大连接数为 5

### 步骤

* 限速
  * 修改 `/etc/httpd/vhosts.d/olabs.org.conf`
  * 为 www.olabs.org 的 /download 限制带宽为 500 KB/sec
* 限制每个 IP 的连接数
  * 安装 mod_limitipconn
  * 修改 `/etc/httpd/conf.modules.d/10-limitipconn.conf`
    * 在 `IfModule` 容器中添加 `MaxConnPerIP 0` 表示默认无限制
  * 修改 `/etc/httpd/vhosts.d/olabs.org.conf`
    * 为 www.olabs.org 的 /download 限制每个 IP 的最大连接数为 5
* 检查 Apache 基于域名的虚拟主机配置
* 在客户端进行浏览测试


>**参考**
>* [Configure mod_ratelimit](https://www.server-world.info/en/note?os=CentOS_7&p=httpd2&f=3)
>* [Use mod_limitipconn](https://www.server-world.info/en/note?os=CentOS_7&p=httpd2&f=9)


## 任务10*：CentOS 6 和 Debian 9 上的 Apache

### 要求
* 在 CentOS 6 上配置 Apache 2.2
  * 在容器 c6-v1 上完成 任务1~任务9 的功能 
* 在 Debian 9 上配置 Apache 2.4
  * 在容器 d9-v1 上完成 任务1~任务9 的功能 

>**参考**
>* [Apache on CentOS 6](https://www.server-world.info/en/note?os=CentOS_6&p=httpd)
>* [Apache on Debian 9](https://www.server-world.info/en/note?os=Debian_9&p=httpd)