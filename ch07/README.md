# CH07 系统日常维护

本章讲解 系统监视、内核管理、启动过程、系统备份、故障排查等系统日常维护内容。

* 系统监视
  * 影响系统性能的因素
  * 性能分析标准的经验准则
  * 使用系统监视工具
* 内核管理
  * 管理内核模块
  * 内核升级
  * 调整内核参数（/proc 和 sysctl）
* 系统启动过程
  * GRUB2 的操作界面
  * 使用 `grub2-mkconfig` 工具生成 GRUB2 的配置文件
  * Systemd 的目标管理与运行级别
  * 使用 `systemd-analyze` 分析启动过程性能
* 备份与恢复
  * 备份类型
  * 使用 `cp`、`tar`、`dd`、`rsync` 等命令实施备份
  * 使用 `rsnapshot` 工具实现快照型备份
  * 使用 `lsyncd` 实现实时同步
* 故障排查
  * 使用 安装光盘/LiveCD 援救环境修复系统启动故障和其他故障
  * 进入 Systemd 的 `rescue`/`emergency` 目标
  * 为内核传递 `rd.break` 参数中断 systemd 的执行并修复故障
  * 修复 root 口令丢失、分区、文件系统、LVM、软件包、网络等故障


>* [CH07 - 教学指导](guidelines.md)
>* [CH07 - 实验指导](experiment_07-01.md)
>* [CH07 - 家庭作业](assignments.md)