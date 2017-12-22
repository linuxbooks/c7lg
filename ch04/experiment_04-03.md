# 实验指导 4.3 - 磁盘常用工具和磁盘限额

>#### 学习目标
> * 磁盘/文件系统常用工具
>   * `dd`
>   * `df`
>   * `du` 
>   * `find`
> * 磁盘限额
>   * 使用 `setquota` 或 `edquota` 配置 ext3/4 文件系统的磁盘限额
>   * 使用 `xfs_quota` 配置 xfs 文件系统的磁盘限额


## 任务1：df 和 du

* 显示 /etc 目录中每个文件的磁盘占用
* 显示 /etc 目录总共占用了多少
* 显示 xfs 和 ext4 文件系统的剩余空间
* 显示除了 tmpfs 之外，所有文件系统的剩余空间，并按照使用率降序输出

## 任务2：使用 dd 命令将 iso 文件的内容写入U盘

>**提示** 本任务使用虚拟块设备模拟了一个 16M 大小的 U盘

* 准备 loop 设备
      # dd if=/dev/zero of=/tmp/vdisk1.dd bs=1M count=16
      # losetup -fP /tmp/vdisk1.dd
      # losetup -a
      /dev/loop0: [64768]:4221244 (/tmp/vdisk1.dd)
      # lsblk -io NAME,TYPE,SIZE,MOUNTPOINT,FSTYPE,MODEL| egrep 'loop|^NAME'
* 准备 iso 文件
      # wget http://www.tinycorelinux.net/8.x/x86/release/Core-current.iso
* 将 iso 文件的内容写入虚拟块设备
      # dd if=Core-current.iso of=/dev/loop0
      # lsblk -io NAME,TYPE,SIZE,MOUNTPOINT,FSTYPE,MODEL| egrep 'loop|^NAME'
* 检查写入的虚拟块设备（U盘）内容
  * 将虚拟块设备 挂装到 /mnt/iso
  * 显示挂装点内容
  * 解除挂装

## 任务3： find 命令

* 查找 /var 目录下属主为root，且属组不为 root 的所有文件或目录
* 查找 /var 目录下属主为root，且属组不为 root 的所有常规文件
* 查找 /bin /sbin 目录下所有 设置了 SUID 或 SGID 的文件
* 查找 /etc 目录下最近一周内修改过其内容且大小小于 2k 的文件
* 查找当前系统上没有属或属组，且最近一周内曾被访问过的文件或目录
* 查找 /etc 目录下所有用户都没有写权限的文件
* 查找 /etc 目录下至少有一类用户没有执行权限的文件
* 删除 /tmp/test 目录下 30 天前 60 天内修改的文件
* 删除 /tmp/test 目录下 30 天前修改的文件
* 复制 两周之前早 9:00 到两月之前 19:00 点之间修改的文件 到 /backup/1目录下


> **提示** 可以使用如下脚本在 /tmp/test 目录下先随机生成 200 个 100 天以内的文件，再使用 find 命令按时间戳查找和删除
```
#!/bin/bash
[ -d "/tmp/test" ] || mkdir /tmp/test
for d in $(shuf -i $(date +%s -d '-100 days')-$(date +%s) -n 200)
do 
   time=$(date -d "@$d" +%F)
   touch -d "$time" /tmp/test/file_$time
done
```

## 任务4： 在 ext4 文件系统上配置用户的磁盘限额

** 要求：**

* 创建用户、组并设置其成员
  * 创建用户 fanny 和 ann
  * 创建组 webs 和 apps
  * 分别将 fanny 和 ann 加入组 webs 和 apps 
* 对挂装在 /srv 目录上的 ext4 文件系统设置用户配额
  * 创建 fanny 用户并设置其为 webs 组的成员
  * 为用户 fanny 设置容量软限制 400M、容量硬限制 500M 的块配额
  * 为用户 fanny 设置文件数软限制 2000、文件数硬限制 2500 的 inode 配额
  * 创建新用户 ann，并以 fanny 用户为参考用户设置其用户的磁盘配额
* 对挂装在 /srv 目录上的文件系统设置组配额
  * 为组 webs 设置容量软限制 1G、容量硬限制 2G 的块配额
  * 为组 webs 设置文件数软限制 20000、文件数硬限制 25000 的 inode 配额
  * 创建新组 apps，并以 webs 组为参考组设置 apps 组的磁盘配额
* 检查配额
  * 查看磁盘限额报告
  * 查看 fanny 的用户配额
  * 查看 apps 的组配额

## 任务5： 在 xfs 文件系统上配置用户的磁盘限额

** 要求：**


* 对挂装在 /data 目录上的 xfs 文件系统设置用户配额
  * 创建 fanny 用户并设置其为 webs 组的成员
  * 为用户 fanny 设置容量软限制 400M、容量硬限制 500M 的块配额
  * 为用户 fanny 设置文件数软限制 2000、文件数硬限制 2500 的 inode 配额
  * 创建新用户 ann，并以 fanny 用户为参考用户设置其用户的磁盘配额
* 对挂装在 /data 目录上的 xfs 文件系统设置组配额
  * 为组 webs 设置容量软限制 1G、容量硬限制 2G 的块配额
  * 为组 webs 设置文件数软限制 20000、文件数硬限制 25000 的 inode 配额
  * 创建新组 apps，并以 webs 组为参考组设置 apps 组的磁盘配额
* 检查配额
  * 查看磁盘限额报告
  * 查看 fanny 的用户配额
  * 查看 apps 的组配额
