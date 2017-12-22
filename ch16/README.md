# CH16 E-mail 服务

本章讲述基本的电子邮件系统的配置。

* 基本概念
  * 电子邮件系统的组成
  * 电子邮件协议
  * 邮件中继
  * MTA 与 DNS
  * LDA 与 用户邮箱
* Postfix
  * Postfix 及其特性
  * Postfix 的体系结构
  * Postfix 的多进程协作
  * Postfix 的邮件队列及其管理器
  * Postfix 映射表的功能及类型
  * Postfix 的 UCE 控制功能
* 配置 SMTP 服务实现 MTA
  * 安装和启动 Postfix
  * Postfix 的配置文件
  * 使用 `postfix` 管理服务
  * 使用 `postconf` 工具显示配置或更新配置文件
  * Postfix 的默认配置
  * 使用 swaks 测试 Postfix
  * 配置基本功能的 SMTP 服务
  * 使用 access 映射表实现中继控制
  * 使用 aliases 映射表实现别名映射
  * 使用 virtual 映射表实现虚拟别名机制
* Docecot
  * Docecot 及其特性
  * Docecot 的体系结构
  * Docecot 的多进程协作
* 配置 POP/IMAP 服务实现 MAA
  * 安装和启动 Docecot
  * Docecot 的配置文件
  * 使用 `doveadm` 管理服务
  * 使用 `doveconf` 显示 Dovecot 配置
  * 配置基本功能的 POP3/IMAP 服务
* SASL 与 TLS
  * SASL 与 SMTP 认证
  * 配置支持 SMTP 认证的 SMTP 服务
  * 配置基于 STARTTLS 的 SMTP 服务
  * 配置基于 SSL/TLS 的 SMTPs 服务
  * 配置基于 SSL/TLS 的 POP3s/IMAPs 服务


>* [CH16 - 教学指导](ch16/guidelines.md)
>* [CH16 - 实验指导](ch16/experiment_16-01.md)
>* [CH16 - 家庭作业](ch16/assignments.md)