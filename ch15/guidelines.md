# CH15 - 教学指导

## 教学模块和知识点

> 1. 可以作为教师教学和考试出题的依据。
> 2. 可以作为学生学习的依据。


### 模块407 - Web 编程语言与 Web 框架

|  编号  |           知识点                          | 掌握程度 | 上机操作 |
| ------ | ----------------------------------------- | -------- | -------- |
| 407-01 | 安装 Perl                                 |   掌握   |          |
| 407-02 | 使用 `cpan` 管理 Perl 模块                |   熟悉   |   是*    |
| 407-03 | Perl 语言框架： Catalyst                  |   了解   |          |
| 407-04 | 安装 Python                               |   掌握   |          |
| 407-05 | 使用 `pip/easy_install` 管理 Python 模块  |   熟悉   |   是*    |
| 407-06 | Python 语言框架： Django/Flask            |   了解   |          |
| 407-07 | 安装 PHP                                  |   掌握   |   是     |
| 407-08 | 使用 `composer/pear/pecl` 管理 PHP 模块   |   熟悉   |   是*    |
| 407-09 | PHP 语言框架： Laravel/symfony/Phalcon/ThinkPHP   |   了解   |          |
| 407-10 | 安装 Ruby                                 |   掌握   |   是     |
| 407-11 | 使用 `gem` 管理 Ruby 模块                 |   熟悉   |   是*    |
| 407-12 | Ruby 语言框架： Ruby on Rails             |   了解   |          |
| 407-13 | 安装 Go                                   |   掌握   |   是     |
| 407-14 | 使用 `gopm` 管理 Go 模块                  |   熟悉   |   是*    |
| 407-15 | Go 语言框架：  revel                      |   了解   |          |
| 407-16 | 安装 Nodejs                               |   掌握   |   是     |
| 407-17 | 使用 `yarn/npm` 管理 Nodejs 模块          |   熟悉   |   是*    |
| 407-18 | JS 语言框架：  AngularJS/VueJS            |   了解   |          |



### 模块408 - 数据库与键值缓存系统

|  编号  |           知识点                             | 掌握程度 | 上机操作 |
| ------ | -------------------------------------------- | -------- | -------- |
| 408-01 | MySQL/MariaDB 关系数据库简介                 |   了解   |          |
| 408-02 | MyISAM/InnoDB/Maria 等存储引擎的特点及选择   |   理解   |          |
| 408-03 | 安装和启动 MySQL/MariaDB 服务                |   掌握   |   是     |
| 408-04 | 为 MySQL/MariaDB 的 root 用户设置口令        |   掌握   |   是     |
| 408-05 | 单实例 MySQL/MariaDB 服务的配置              |   掌握   |   是     |
| 408-06 | CLI 客户工具：mysql                          |   熟悉   |   是     |
| 408-07 | GUI 客户工具：HeidiSQL                       |   熟悉   |   是     |
| 408-08 | WUI 客户工具：phpMyAdmin/Adminer             |   熟悉   |   是     |
| 408-09 | MySQL/MariaDB 数据库的备份与恢复             |   掌握   |   是     |
| 408-10 | mongoDB 文档数据库简介                       |   了解   |          |
| 408-11 | 安装、启动和配置 mongoDB                     |   了解   |          |
| 408-12 | Memcached 简介                               |   了解   |          |
| 408-13 | 安装、启动 Memcached                         |   掌握   |   是     |
| 408-14 | 单实例 Memcached 服务的配置                  |   掌握   |   是*     |
| 408-15 | 使用管理工具 `memcached-tool`                |   熟悉   |   是     |
| 408-16 | Redis 简介                                   |   了解   |          |
| 408-17 | 安装、启动和配置 Redis                       |   掌握   |   是*     |
| 408-18 | 单实例 Redis 服务的配置                      |   掌握   |   是     |
| 408-19 | 使用管理工具 `redis-cli`                     |   熟悉   |   是     |


### 模块409 - 基于 Apache 的动态网站技术

|  编号  |           知识点                                | 掌握程度 | 上机操作 |
| ------ | ----------------------------------------------- | -------- | -------- |
| 409-01 | CGI 技术及其特点                                |   理解   |          |
| 409-02 | 使用 ScriptAlias/AddHandler 配置 CGI            |   掌握   |   是     |
| 409-03 | AWStats 日志统计分析工具的安装配置              |   掌握   |   是     |
| 409-04 | LAMP 简介                                       |   熟悉   |          |
| 409-05 | PHP 及其相关模块的配置                          |   掌握   |   是     |
| 409-06 | 配置 Apache 基于 mod_php 的 PHP 支持            |   掌握   |   是     |
| 409-07 | 配置 Apache 基于 php-fpm 的 PHP 支持            |   掌握   |   是     |
| 409-08 | 安装配置基于 LAMP 的管理工具 phpMyAdmin/LogAnalyzer |   掌握   |   是     |
| 409-09 | 安装配置 LAMP 的 BLOG/WIKI/FORUM/CMS 等典型应用 |   熟悉   |   是     |
| 409-10 | 安装配置基于 laravel/symfony 框架的应用         |   熟悉   |   是*    |
| 409-11 | 配置 Apache 支持 Python 的 WSGI 模块            |   熟悉   |   是*    |
| 409-12 | 安装配置基于 Django 框架的应用（如：[Weblate](https://docs.weblate.org/en/latest/admin/install.html)） |   了解   |     |
| 409-13 | 配置 Apache 支持 Ruby 的 Passenger 模块         |   了解   |   是*    |
| 409-14 | 安装配置基于 RoR 框架的应用（如：[Gitlab](https://docs.gitlab.com/ce/README.html)）  |   了解   |          |
| 409-15 | 从 SCL 仓库安装各种版本的软件并使用 `scl` 命令切换 |   掌握   |   是     |
| 409-16 | 从源代码编译安装 LAMP 环境                      |   了解   |   是*    |


### 模块410 - 代理与反向代理

|  编号  |           知识点                             | 掌握程度 | 上机操作 |
| ------ | -------------------------------------------- | -------- | -------- |
| 410-01 | 代理服务的概念和工作原理                     |   理解   |          |
| 410-02 | Varnish 的安装、初始化和启动                 |   了解   |   是*    |
| 410-03 | 使用 Varnish 配置缓存代理                    |   熟悉   |   是*    |
| 410-04 | Squid 的安装、初始化和启动                   |   了解   |   是*    |
| 410-05 | 使用 Squid 配置缓存代理                      |   熟悉   |   是*    |
| 410-06 | Polipo 的安装、初始化和启动                  |   了解   |   是*    |
| 410-07 | 使用 Polipo 配置缓存代理                     |   了解   |   是*    |
| 410-08 | 反向代理服务的概念和工作原理                 |   理解   |          |
| 410-09 | 使用 Apache 配置反向代理                     |   掌握   |   是     |
| 410-10 | 使用 Nginx 配置反向代理                      |   了解   |   是*    |
| 410-11 | 使用 Varnish 配置反向代理                    |   了解   |   是*    |
| 410-12 | 使用 Squid 配置反向代理                      |   了解   |   是*    |


### 模块411 - JDK 和 Tomcat

|  编号  |           知识点                             | 掌握程度 | 上机操作 |
| ------ | -------------------------------------------- | -------- | -------- |
| 411-01 | 安装配置 JDK                                 |   掌握   |   是     |
| 411-02 | Tomcat 简介                                  |   了解   |          |
| 411-03 | 安装和配置默认的 Tomcat 实例                 |   掌握   |   是     |
| 411-04 | 安装和配置第二个 Tomcat 实例                 |   掌握   |   是     |
| 411-05 | 配置基于 Tomcat 虚拟主机                     |   熟悉   |   是*    |
| 411-06 | 配置 Apache 反向代理 Tomcat                  |   掌握   |   是     |
| 411-07 | 配置 Nginx 反向代理 Tomcat                   |   熟悉   |   是*    |
| 411-08 | 部署基于二进制包发布的 Tomcat                |   了解   |   是*    |


## 本章学习材料

* **教材和课件 第15章**
* linux.vbird.org
  * [WWW 伺服器](http://linux.vbird.org/linux_server/0360apache.php)
* 马哥教育 视频
  * [Linux运维视频课程-Web服务进阶](http://edu.51cto.com/course/course_id-5547.html)
  * [Linux必备web服务入门及高级进阶](http://edu.51cto.com/course/course_id-866.html)
  * [Nginx应用基础及配置详解](http://edu.51cto.com/course/course_id-5550.html)
  * [马哥教育2016高薪Linux培训教程-Web服务之Tomcat](https://www.chuanke.com/2309244-178898.html)
* 布尔教育 视频
  * [MySQL 性能优化](https://www.chuanke.com/1053373-215686.html)
* https://www.codecasts.com/
  * [从零部署一个网站](https://www.codecasts.com/series/deploy-a-website-from-scratch)
