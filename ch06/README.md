# CH06 服务管理与基础服务

本章讲解服务的管理、以及三种系统基础服务。

* 守护进程和服务管理
  * 守护进程的相关概念
  * 使用 `systemctl` 显示、启动和停止服务
  * 使用 `systemctl` 配置在启动时的 启用/禁用
* 周期性任务服务
  * 周期性任务与 crond 服务
  * 修改配置文件安排 cron 任务
  * 使用 `crontab` 命令安排 cron 任务
* 系统日志服务
  * rsyslogd 日志服务
  * 配置和查看各种系统日志
  * 配置中央日志服务器
  * 日志工具 `LogRotate` 和 `LogWatch` 的配置和使用
* 安全Shell服务
  * SSH 协议和 SSH 服务
  * 配置 SSH 服务提高安全性
  * 主机密钥管理
  * 用户密钥管理


>* [CH06 - 教学指导](ch06/guidelines.md)
>* [CH06 - 实验指导](ch06/experiment_06-01.md)
>* [CH06 - 家庭作业](ch06/assignments.md)