# 实验指导 15.1 - LAMP

>#### 学习目标
>* 配置基于 php5_module 模块的 LAMP 环境
>* 配置基于 php-fpm 和 proxy_fcgi_module 模块的 LAMP 环境
>* 安装 SCL 仓库中的 PHP 7.0
>* 安装配置 LAMP 应用
>* 配置 AWStats 实现虚拟主机访问日志分析统计

## 任务1：安装配置 LAMP 环境(1)

### 要求

基于 CentOS7 官方仓库和 EPEL 仓库配置 LAMP 环境
* Aache2.4 + mpm_prefork_module + php5.4 + php5_module 
* MariaDB5.5

### 步骤

1. 安装配置 MariaDB/MySQL 服务
  * 安装 mariadb 和 mariadb-server 
  * 配置 MariaDB
    * 编辑主配置文件 `/etc/my.cnf`，在 `[mysqld]` 段里设置
      * character-set-server=utf8
      * collation-server=utf8_general_ci 
      * max_connections = 50 （默认最大并发连接数为100）
    * 编辑主配置文件 `/etc/my.cnf.d/client.cnf`，在 `[client]` 段里设置
      * character-set-server=utf8
  * 启动 MariaDB 服务，并设置开机启动
  * 配置 MariaDB 服务的 root 用户口令
    *  `mysqladmin -u root password 'Med7ahBuu7ru2Wooyohg'`
    *  或 `mysql_secure_installation`
  * 安装 EPEL 仓库中的并获取更多的配置建议
2. 安装配置 PHP
  * 安装 PHP 及相关模块
         yum install php \
          php-{pdo,mcrypt,mbstring,intl,gd,pecl-{imagick,memcached,redis}
  * 检测安装的 PHP （cli） 版本
         php -v
  * 配置 PHP
    * 编辑主配置文件 `/etc/php.ini`，在 `[PHP]` 段里设置
      * 使用 zlib 库压缩输出并设置压缩级别为 1
      * 限制一个 PHP 脚本可能消耗的最大内存量为 256M
      * 为 POST 方法指定可接受的最大尺寸为 256M
      * 设置可上传文件的最大尺寸为 20M
    * 编辑主配置文件 `/etc/php.ini`，在 `[Date]` 段里设置
      * 为日期函数定义默认时区为 `Asia/Shanghai`
3. 通过 Aapche 的 PHP 模块执行 PHP 脚本
  * 查看 Apche 的 PHP 模块 加载/配置 文件
         grep -v "^#" /etc/httpd/conf.modules.d/10-php.conf
         grep -v "^#" /etc/httpd/conf.d/php.conf
  * 检测 Apache 配置正确性并重新加载 Apache 配置
4. 测试
  * 编写 PHP 测试脚本
         echo '<?php phpinfo()?>' > /var/www/html/info.php
         echo '<?php phpinfo()?>' > /srv/www/olabs.net/www/htdocs/info.php 
  * 在客户端上测试
         elinks http://www.olabs.lan/info.php
         elinks http://www.olabs.net/info.php
  * 压力测试
         ab -n 2000 -c 100 http://www.olabs.net/info.php
5. 使用 `lynis -c` 扫描整个系统，根据报告提示加固系统

>**参考**
>* [How To Install Linux, Apache, MySQL, PHP (LAMP) stack On CentOS 7](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-centos-7)
>* [超实用压力测试工具－ab工具](https://www.jianshu.com/p/43d04d8baaf7)
>* [PHP 缓存](http://laravel-china.github.io/php-the-right-way/#caching)
>* [Easy Deployment of PHP Applications with Deployer](https://www.sitepoint.com/deploying-php-applications-with-deployer/)
>* [LAMPer 技能树](https://laravel-china.org/topics/384/lamper-skill-tree)


## 任务2：安装配置 LAMP 应用（1）

### 要求

安装配置
* phpMyAdmin
* dokuwiki (`.htaccess`)
* h5ai

### 步骤

1. 安装配置 phpMyAdmin
  * 安装 phpMyAdmin 
  * 配置 phpMyAdmin
    * 修改 phpMyAdmin 的配置文件 `/etc/phpMyAdmin/config.inc.php`
      * 为 Cookies 认证重新设置加密口令
    * 修改 Apache 的配置文件 `/etc/httpd/conf.d/phpMyAdmin.conf`
      * 配置允许 192.168.56.0/24 访问 
  * 检测 Apache 配置正确性并重新加载 Apache 服务的配置
  * 测试 phpMyAdmin 
    *  https://www.olabs.lan/phpmyadmin/
    *  https://www.olabs.net/phpmyadmin/ 
2. 安装配置 dokuwiki
  * 下载并部署 dokuwiki 站点内容
```
mkdir /srv/www/olabs.net/wiki/src
cd /srv/www/olabs.net/wiki/src
wget https://download.dokuwiki.org/src/dokuwiki/dokuwiki-stable.tgz
tar xzf dokuwiki-stable.tgz
cd ..
rm -rf htdocs
mv src/dokuwiki-2017-02-19e htdocs
```
  * 在浏览器里执行安装脚本进行安装
    * http://wiki.olabs.net/install.php
    * 根据提示信息合理设置文件系统权限
    * 安装后删除 install.php 文件
  * 编辑 Wiki 页面
  * 配置伪静态访问 
    * 编辑  `/etc/httpd/vhosts.d/olabs.net.conf` ，修改 wiki.olabs.net:443 的虚拟主机
      * 配置允许读取 `/srv/www/olabs.net/wiki/htdocs/` 目录下的配置文件 `.htaccess` 
    * 编辑 `/srv/www/olabs.net/wiki/htdocs/conf/local.php` 启用伪静态访问
      * `echo "\$conf['userewrite'] = 1;" >>  /srv/www/olabs.net/wiki/htdocs/conf/local.php`
    * 修改
      * 复制默认发布的 .htaccess.dist 为 .htaccess
        * `cp /srv/www/olabs.net/wiki/htdocs/.htaccess{.dist,}`
      * 编辑 `/srv/www/olabs.net/wiki/htdocs/.htaccess` 使之适应本站
    * 测试伪静态访问 
      * http://wiki.olabs.net/wiki/syntax  
3. 安装配置 h5ai 
  * 为 `/srv/www/olabs.org/www/htdocs/download` 目录安装配置 `h5ai`
  * 使访问 http://www.olabs.org/download 时的显示效果像 https://release.larsjung.de/

>**参考**
>* https://www.dokuwiki.org/install
>* https://www.dokuwiki.org/rewrite
>* https://larsjung.de/h5ai/

## 任务3：安装配置 LAMP 环境(2)

### 要求

基于 CentOS7 官方仓库和 EPEL 仓库配置 LAMP 环境
* Aache2.4 + **mpm_envent_module** + php5.4 + **php-fpm** + **proxy_fcgi_module**
* MariaDB5.5

### 步骤

1. 安装并启动 `php-fpm`
  * 删除用于 Apache 模块的 `php` 包
  * 安装 `php-fpm`
  * 开机/立即 启动 `php-fpm` 守护进程
2. 查看并配置 `php-fpm`
  * 查看 `php-fpm` 版本
         php-fpm -v
  * 查看 `php-fpm` 进程
         ps -HO user -p `pidof php-fpm`
         lsof -i :9000
  * 查看 `php-fpm` 的主配置文件 `/etc/php-fpm.conf`
  * 查看 `php-fpm` 进程池配置文件 `/etc/php-fpm.d/www.conf`
3. 配置 Apache
  * 配置 Apache 通过 **proxy_fcgi_module** 访问 `php-fpm`
    * 创建或编辑 `/etc/httpd/conf.d/php.conf`：
           # Allow php to handle Multiviews
           AddType text/html .php
                   
           # Add index.php to the list of files 
           # that will be served as directory indexes.
           DirectoryIndex index.php
           
           # Enable the http authorization headers.
           SetEnvIfNoCase ^Authorization$ "(.+)" HTTP_AUTHORIZATION=$1
           
           # Redirect the PHP scripts execution to the FPM backend.
           <FilesMatch \.php$>
               SetHandler "proxy:fcgi://127.0.0.1:9000"
           </FilesMatch>
           
           # Prevent .user.ini files from being viewed by Web clients.
           <Files ".user.ini">
               Require all denied
           </Files>
  * 配置 Apache 启用 **mpm_envent_module**
    * 编辑 `/etc/httpd/conf.modules.d/10-php.conf`
           # LoadModule mpm_prefork_module modules/mod_mpm_prefork.so
           # LoadModule mpm_worker_module modules/mod_mpm_worker.so
           LoadModule mpm_event_module modules/mod_mpm_event.so
  * 检测 Apache 配置正确性并重新加载 Apache 服务的配置
4. 测试 Apache 是否启用了 `FPM/FastCGI`
       elinks --dump http://localhost/info.php |grep 'Server API'
       elinks --dump  http://www.olabs.lan/info.php |grep 'Server API'
       elinks --dump  http://www.olabs.net/info.php |grep 'Server API'
5. 压力测试
       ab -n 2000 -c 100 http://www.olabs.net/info.php 

>**参考**
>* [PHP + PHP-FPM](https://www.server-world.info/en/note?os=CentOS_7&p=httpd&f=19)
>* [PHP Configuration Tips](https://developers.redhat.com/blog/2017/10/25/php-configuration-tips/)


## 任务4：安装配置 LAMP 环境(3)

### 要求

基于 SCL 仓库配置 LAMP 环境
* Aache2.4 + **mpm_envent_module** + **php70** + **php-fpm** + **proxy_fcgi_module**
* MariaDB5.5

### 步骤

1. 安装配置 SCL 仓库
       yum -y install centos-release-scl scl-utils
       rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-SIG-SCLo
       yum repolist |grep sclo
       yum makecache
2. 安装 php70 及相关模块
       yum -y install rh-php70 \
          rh-php70-php-{pdo,mcrypt,mbstring,intl,gd,pecl-{imagick,memcached,redis},fpm}
       scl -l
3. 切换 php-fpm 到新版本
       systemctl stop php-fpm
       systemctl disable php-fpm
       systemctl start rh-php70-php-fpm
       systemctl enable rh-php70-php-fpm
4. 测试
       elinks --dump http://localhost/info.php |egrep 'Server API|PHP Version'


>### 在命令行上切换使用 SCL 仓库的 PHP
>* 检测原来安装的 PHP 版本
>       which php ; php -v 
>       which php-fpm ; php-fpm -v
>* 切换新 Shell 使用 SCL 仓库的 PHP
>       scl -l
>       scl enable rh-php70 bash
>* 检测新安装的 PHP 版本
>       which php ; php -v
>       which php-fpm ; php-fpm -v
>* 退出新 shell，重新查看 PHP 版本
>       exit
>       which php ; php -v
>       which php-fpm ; php-fpm -v

>### 在命令行上默认使用 SCL 仓库的 PHP
>```
>cat >/etc/profile.d/rh-php70.sh <<_END
>#!/bin/bash
>
>source /opt/rh/rh-php70/enable
>export X_SCLS="\$(scl enable rh-php70 'echo \$X_SCLS')"
>_END
>```

>### 配置 SCL 仓库的 PHP/PHP-FPM
>* 配置文件基于 `/etc/opt/rh/rh-php70/` 目录
>  * php 配置文件: `php.ini` , `php.d/*.ini`
>  * php-fpm 配置文件: `php-fpm.conf` , `php-fpm.d/*.conf`


>### 参考
>* SCL 仓库
>  * https://wiki.centos.org/zh/AdditionalResources/Repositories/SCL
>  * https://wiki.centos.org/SpecialInterestGroup/SCLo/CollectionsList
>  * [Release Notes for Red Hat Software Collections 3.0](https://access.redhat.com/documentation/en-us/red_hat_software_collections/3/html-single/3.0_release_notes/)
>  * [Software Collections](https://www.softwarecollections.org)
>* [PHP Configuration Tips](https://developers.redhat.com/blog/2017/10/25/php-configuration-tips/)
>* http://phpversions.info/operating-systems/


>### 练习
>
>* 安装并启用 SCL 仓库中的 Mariadb v10.2
>       yum search rh-mariadb102


## 任务5：使用 AWStats 实现访问日志分析统计

### 要求

为 www.olabs.{net,org} 虚拟主机配置 AWStats 实现访问日志分析统计

### 步骤

1. 安装 awstats
2. 配置 awstats，为每个虚拟主机创建各自的配置文件
  * `/etc/awstats/awstats.www.olabs.net.conf`
  * `/etc/awstats/awstats.www.olabs.org.conf`  
3. 立即更新指定配置文件的 AWStats 的统计数据库
  * `/usr/share/awstats/wwwroot/cgi-bin/awstats.pl -config=www.olabs.net`
  * `/usr/share/awstats/wwwroot/cgi-bin/awstats.pl -config=www.olabs.org`  
4. 为了通过 CGI 访问查看 AWStats 的 WUI 配置 Apache
  * 编辑被 Apache 主配置文件包含的 `/etc/httpd/conf.d/awstats.conf`
  * 在适当位置添加 HTTP 摘要认证配置，可以使用 第14章任务4 创建的摘要认证口令文件 `/etc/httpd/.dpasswd`  
5. 检测 Apache 配置正确性并重新加载 Apache 配置
6. 通过浏览器访问 AWStats，并测试摘要认证
   * http://www.olabs.net/awstats/awstats.pl
   * http://www.olabs.net/awstats/awstats.pl?config=www.olabs.net
   * http://www.olabs.net/awstats/awstats.pl?config=www.olabs.org


>**参考**
>* [Access Log Analyzer : AWstats](https://www.server-world.info/en/note?os=CentOS_7&p=httpd&f=15)


## 任务6*：安装配置 LAMP 应用（2）

### 要求

* 为 http://blog.olabs.org 安装配置一个基于 Laravel 框架的应用

### 步骤

1. 安装配置 composer
  * 安装 composer

         # curl -sS https://getcomposer.org/installer | php

         # mv composer.phar /usr/local/bin/composer
  * 配置 composer 全局使用的镜像站点

         # composer config -g repo.packagist composer \

              https://packagist.phpcomposer.com
         # tree -F -L 2 ~olabsorg
2. 安装 laravel
       # su - olabsorg
       
       $ scl enable rh-php70 bash
       $ composer create-project  laravel/laravel blog --prefer-dist "5.5.*"
3. 配置并测试 blog.olabs.org 虚拟主机
  * 修改 `/etc/httpd/vhosts.d/olabs.org.conf` 
```
<VirtualHost *:80>
    ServerAdmin root@localhost
    ServerName blog.olabs.org:80
    DocumentRoot /srv/www/olabs.org/blog/public/
    ErrorLog  /srv/www/olabs.org/blog/logs/error_log
    CustomLog /srv/www/olabs.org/blog/logs/access_log combined
    <Directory /srv/www/olabs.org/blog/public/>
        Options +FollowSymLinks
        Require all granted

        RewriteEngine On
        RewriteCond %{REQUEST_FILENAME} !-d
        RewriteCond %{REQUEST_FILENAME} !-f
        RewriteRule ^ index.php [L]
    </Directory>
</VirtualHost>
```
  * 检测 Apache 配置正确性并重新加载 Apache 服务的配置
  * 配置 blog.olabs.org 的域名解析 （bind 或 /etc/hosts）
  * 测试 http://blog.olabs.org
4. 安装配置基于 laravel 的后台生成工具 [Voyager](https://laravelvoyager.com/)
  * 使用 composer 安装 Voyager 所需的 PHP 软件包
  * 创建 BLOG 所需的 mysql 数据库
  * 配置项目下的环境文件 `.env` 
  * 使用 artisan 执行 voyager 的安装并填充测试数据
  * 重新设置管理员 admin 的口令和 Email
  * 在浏览器中访问 BLOG 的后台管理界面  http://blog.olabs.org/admin
5. 基于 Voyager 后台编写代码，创建 BLOG 前台 http://blog.olabs.org

>**参考**
>* https://d.laravel-china.org/docs/5.5/installation
>* https://github.com/the-control-group/voyager
>* https://startbootstrap.com/template-categories/blogs/
>
>** 练习**
>* 安装  [Grav](https://getgrav.org/) 或 [BookStack](https://www.bookstackapp.com/)

## 任务7*：Memcached 和 Redis

### 要求
* 安装、配置并启动 Memcached
* 安装、配置并启动 Redis

>**参考**
>* [Memcached : Install](https://www.server-world.info/en/note?os=CentOS_7&p=memcached)
>  * [Memcached : Use it on PHP](https://www.server-world.info/en/note?os=CentOS_7&p=memcached&f=4)
>* [Redis : Install](https://www.server-world.info/en/note?os=CentOS_7&p=redis&f=1)
>  * [Redis : Use it on PHP](https://www.server-world.info/en/note?os=CentOS_7&p=redis&f=9)

## 任务8*：使用 mylvmbackup 实现 MySQL 数据库的物理备份

### 要求
* 安装 EPEL 仓库中的 mylvmbackup
* 配置 mylvmbackup
  * `/etc/mylvmbackup.conf`
* 安排每日 1点 执行的 cron 任务
  * `/etc/cron.d/mylvmbackup`

>**参考**
>* http://www.lenzg.net/mylvmbackup/
>* ` man mylvmbackup`

## 任务9*：CentOS 6 和 Debian 9 的 LAMP 环境配置

### 要求
* 在 c6-v1 容器上配置 **Apache2.4+php7.0+php-fpm+mpm_envent_module**
* 在 d9-v1 容器上配置 **Apache2.4+php7.0+php-fpm+mpm_envent_module**