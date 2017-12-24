# 实验指导 7 - 系统维护

>#### 学习目标
> * 使用系统监视工具
>   * `uptime`/`tload`
>   * `top`/`htop`/`dstat`
>   * `free`/`vmstat`
>   * `mpstat`/`iostat`/`sar`
>   * `nload`/`nethogs`/`iftop`
> * 内核管理
>   * 安全升级内核  
>   * 使用 `sysctl` 调整内核参数
> * 系统启动过程
>   * Systemd 的目标管理与运行级别
>   * 使用 `systemd-analyze` 分析启动过程性能
>   * 自定义 Systemd 服务单元的配置文件
> * 备份与恢复
>   * 使用 `cp`、`tar`、`dd`、`rsync` 等命令实施备份
>   * 使用 `rsnapshot` 工具实现快照型备份
>   * 使用 `lsyncd` 实现实时同步    
> * 故障排查
>  * 切换进入 Systemd 的 `rescue`/`emergency` 目标
>  * 使用 安装光盘的援救环境/LiveCD 修复系统启动故障和其他故障
>  * 使用 `grub2-mkconfig` 工具重新生成 GRUB2 的配置文件
>  * 为内核传递 `rd.break` 参数中断 systemd 的执行并修复故障
>  * 修复 root 口令丢失、分区/LVM、文件系统、软件包、网络等故障


## 任务1： 使用监视工具分析系统性能

>**提示** 请先确保常用的系统监视工具已经被安装
> `yum -y install sysstat htop dstat nload nethogs iftop`

* 使用如下工具监视系统
  * `uptime`/`tload` 
  * `top`/`htop`/`dstat`
  * `free`/`vmstat`
  * `mpstat`/`iostat`/`sar`
  * `nload`/`nethogs`/`iftop`
* 系统性能分析
  * 系统平均负载为何时表示负载过重？
  * 如何找出 CPU 瓶颈？
  * 如何找出 内存 瓶颈？
  * 如何找出 I/O  瓶颈？
  * 如何找出 带宽 瓶颈？

## 任务2： 内核管理

* 升级内核
  * yum update kernel-VER 
  * yum update
* 调整内核参数
  * 使用 `sysctl` 显示内核参数
  * 使用 `sysctl -w` 设置内核参数
    * 如：开启包转发功能 


## 任务3：系统启动过程

>### BIOS/UEFI -> GRUB2 -> 内核初始化 -> Systemd 初始化

* 内核初始化
  * 参考 `man 7 dracut.bootup` 
* Systemd 初始化
  * 参考 `man 7 bootup`
* systemd 的运行目标管理
  *  显示当前已激活的目标
  *  显示当前已加载的所有目标
  *  显示当前已安装的所有目标
* systemd 的默认目标管理
  * 类似于在 CentOS 6 中配置或切换系统运行级别 
  * 显示当前的默认目标
  * 显示默认目标的依赖关系
  * 设置默认目标（下次启动时生效）为 `graphical.target`
  * 更改当前的目标（立即生效）到 `emergency.target`


## 任务4： 禁用一致的网络设备名

* 修改 `/etc/default/grub` 的 `GRUB_CMDLINE_LINUX` 配置行
* 重新生成 grub2 的配置文件
* 重新启动

## 任务5： 基于 tar 的备份

* 完全（Full）备份
  * 将 `/etc /home /srv` 目录下的所有文件打包备份到 `/backup/full-backup.tgz`
  * 将当前完全备份的日期时间戳 (`date +%F`)写入 `/backups/full-backup-date` 文件
* 增量（Incremental）备份
  * 将自昨天 0 点起有变化的数据打包备份到 `/backup/inc-backup-$(date -d yesterday "+%F").txz`
* 差分（Differential）备份
  * 将自完全备份以来有变化的数据打包备份到 `/backup/diff-backup-$(date +%F).tbz`

>* 编写一个每日执行脚本，实现每月一次完全备份，每周一次差分备份，每日一次增量备份，并删除 180 天前创建的备份文件

## 任务6： 基于 rsync 和 tar 的远程备份

**要求** 
1. 备份生产服务器（容器 c6-v1）的 /etc /home 目录到备份服务器（假如使用在第一章安装的 CentOS 7 VirtualBox 虚拟机）
2. 保留历史归档 （每月一次完全备份，每周一次差分备份，每日一次增量备份）
3. 删除 180 天前创建的备份文件

**方法**
1. 在容器 c6-v1 上执行任务5的操作，然后使用 rsync 命令同步到备份服务器
2. 优选方法
   * 在备份服务器上创建目录 /backup/c6-v1/{current,archive} 
   * 在备份服务器上每天将 c6-v1 上的 /etc /home 同步到自己的 /backup/c6-v1/current/{etc,home}
   * 在备份服务器上针对 /backup/c6-v1/current/{etc,home} 里的数据实施如 任务5 的操作，并将生成的 tar 文件存到 /backup/c6-v1/archive 目录里
   * 这样可以减轻生产服务器的负载并极大地减少了网络传输

试编写一个脚本完成上述任务。


## 任务7： 基于快照工具（rsnapshot）的备份

**要求：**备份 `/etc/ /home /srv /root` 目录下的所有内容

* 修改 rsnapshot 的配置文件 `/etc/rsnapshot.conf`
  * 假设这些目录都在某个逻辑卷中 
    * 在备份之前，对要备份的目录所在的逻辑卷创建快照
    * 将快照卷挂装到 `/mnt/snap/` 相应的子目录下
    * 备份完毕卸装快照卷并删除快照卷
  * 要求保留 6个小时快照，7 个日快照，4个周快照，6个月快照
* 添加周期性任务配置文件 `/etc/cron.d/rsnapshot` ，配置使之符合备份频率要求

## 任务8： 实时同步

* 安装并配置 `lsyncd` 
* 使 CentOS 7 VirtualBox 虚拟机 的 `/var/www` 目录与 容器 c6-v1 中的 `/var/www` 目录保持同步

## 任务9： 故障排查

* 找回丢失的 root 口令
* 使用 gpt 分区设备的备份分区表修复其主分区表
* 使用通过 dd 命令备份的 DOS（MBR） 分区表镜像文件修复 DOS 分区表