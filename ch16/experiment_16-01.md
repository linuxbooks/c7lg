# 实验指导 16 - 邮件服务

>#### 学习目标
>* 配置基于系统用户的邮件服务器
>* 使用 swaks/mail 进行邮件测试
>* 安装配置 WebMail


## 任务1：安装配置邮件服务

* 基于 Linux 系统用户实现邮件服务
* 允许 Postfix 为本地服务器及本地域投递邮件
* 通过 Postfix 的映射表配置将发往 root 的邮件同时发给 tonny 用户
* 基于 SASL 配置 SMTP 身份认证
* 配置 Postfix 支持 ESMTPS （25/tcp）
* 配置 Dovecot 支持 POP3S （995/tcp）、IMAPS （993/tcp）
* 安装一款 WebMail 

>* **常见的 Webmail**
>  * RoundCube - http://roundcube.net
>  * SquirrelMail - http://squirrelmail.org
>  * RainLoop - http://www.rainloop.net
>* [Top 9 Best Email Clients for Linux](https://itsfoss.com/best-email-clients-linux/)

## 任务2*：安装 iRedMail

* 在新建的 虚拟机/容器 里安装 [iRedMail](http://www.iredmail.org)

