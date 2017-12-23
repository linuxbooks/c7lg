# 实验指导 4 - 本地存储管理

>#### 学习目标
> * 分区工具
>   * 使用 `fdisk`/`cfdisk`  管理 MBR 分区
>   * 使用 `**gdisk**`/`cgdisk`  管理 GPT 分区
>   * 使用 `parted` 管理 MBR/GPT 分区
>   * 使用 `partx`/`kpartx` 通知内核强制重读磁盘分区表
> * 文件系统管理
>   * 使用 `mkfs.{ext4,xfs}` 创建文件系统
>   * 使用 `mount`/`umount` 挂装/卸装 文件系统
>   * 使用 `fuser` 终止所有正在访问某挂载点的进程
>   * 使用 `blkid` 命令显示文件系统的 卷标/UUID
>   * 修改 `/etc/fstab` 在系统启动时挂装文件系统
>   * 使用 `mkswap`、`swapon`/`swapoff` 管理交换空间
>   * 使用 `fsck`/`xfs_repair` 检查和修复文件系统
> * 磁盘/文件系统常用工具
>   * `dd`、`df`、`du`
>   * `find`
> * 磁盘限额
>   * 使用 `setquota` 或 `edquota` 配置 ext3/4 文件系统的磁盘限额
>   * 使用 `xfs_quota` 配置 xfs 文件系统的磁盘限额
> * 逻辑卷管理
>   * 使用 `{pv,vg,lv}create` 创建 物理卷/卷组/逻辑卷
>   * 使用 `{pv,vg,lv}{s,display}` 查看 物理卷/卷组/逻辑卷
>   * 使用 `{vg,lv}{extend,reduce}` 扩展和收缩 卷组/逻辑卷 
>   * 使用 `resize2fs` 扩展和收缩 ext 文件系统
>   * 使用 `xfs_growfs` 扩展 xfs 文件系统


## 任务1：磁盘分区

* 为虚拟机添加一块 20G 大小的硬盘
* 为磁盘设置 GPT 分区表
* 添加 3 个分区，分别为
  * 5G, Linux 分区类型
  * 3G, Linux 分区类型
  * 1G，swap  分区类型
* 在不重启系统的前提下，让 Linux 内核重新读取新硬盘的分区表

>#####参考
>* https://wiki.archlinux.org/index.php/Partitioning
>* https://wiki.archlinux.org/index.php/Fdisk


## 任务2：创建和 挂装/卸装 文件系统

* 在大小为 5G 的分区上创建 xfs 文件系统
* 在大小为 3G 的分区上创建 ext4 文件系统
* 创建两个文件系统挂装点 /mnt/{xfs，ext4}
* 将大小为 5G 的文件系统手动挂装到 /mnt/xfs
* 将大小为 3G 的文件系统手动挂装到 /mnt/ext4
* 检查文件系统的挂装情况
* 复制 /usr 整个目录的内容到 /mnt/xfs
* 进入 /mnt/ext4 目录，将 /etc 整个目录的内容复制到当前目录
* 使用 fuser 命令分别查看两个挂装点目录下有无进行在运行
* 分别手动卸装 /mnt/{xfs，ext4}

## 任务3：交换空间

* 交换分区
  * 在大小为 1G 的分区上创建 swap 空间
  * 查看当前 swap 空间大小
  * 激活大小为 1G 的 swap 空间
  * 查看当前 swap 空间大小
  * 去激活大小为 1G 的 swap 空间
  * 查看当前 swap 空间大小
* 交换文件
  * 创建一个大小为 512M 的交换文件
  * 为此交换文件创建 swap 空间
  * 查看当前 swap 空间大小
  * 激活交换文件上的 swap 空间
  * 查看当前 swap 空间大小
  * 去激活交换文件上的 swap 空间
  * 查看当前 swap 空间大小

## 任务4：配置系统启动时挂装

* 将大小为 5G 的 xfs 文件系统挂装到 /data（使用文件系统UUID）
* 将大小为 3G 的 ext4 文件系统挂装到 /srv
* 激活大小为 1G 的交换分区
* 模拟系统启动，检查文件系统和交换分区的挂装情况

## 任务5：挂装 iso 文件

* 下载一个 iso 文件
      wget -c http://www.tinycorelinux.net/8.x/x86/release/Core-current.iso 
* 创建 /mnt/iso 挂装点
* 将 iso 文件只读挂装到 /mnt/iso
* 显示挂装点目录的内容
* 解除挂装


## 任务6：使用 dd 命令将 iso 文件的内容写入U盘

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

## 任务7：文件系统检查和修复

>**对挂装点 /data 和 /srv 分别进行如下操作

* 手动卸装文件系统
* 检查文件系统
* 向挂装点对应的分区里写入连续随机数据，模拟分区损坏
  * 越过 100 块，像设备写入 10 块（每块 512 字节）数据
* 检查文件系统
* 修复文件系统
* 重新挂装文件系统，并查看分区中的原有数据

## 任务8：df 和 du 命令

* 显示 /etc 目录中每个文件的磁盘占用
* 显示 /etc 目录总共占用了多少
* 显示 xfs 和 ext4 文件系统的剩余空间
* 显示除了 tmpfs 之外，所有文件系统的剩余空间，并按照使用率降序输出

## 任务9： find 命令

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

## 任务10：创建基于新硬盘上的卷组和逻辑卷

1. 为逻辑卷准备新的分区
  * 为虚拟机添加第3块 10G 大小的新硬盘（/dev/sdc）
  * 为磁盘设置 GPT 分区表
  * 使用全部空间添加 1 个分区，类型为 8e00
  * 在不重启系统的前提下，让 Linux 内核重新读取新硬盘的分区表
2. 管理LVM
  * 在新建的分区上创建物理卷
  * 基于此物理卷创建名为 db 的逻辑卷
  * 在 db 卷组中创建名为 mysql 的逻辑卷，大小使用全部FREE
3. 管理基于 LVM 上的文件系统
  * 对名为 mysql 的逻辑卷创建 ext4 文件系统
  * 创建挂装点目录 /var/lib/mysql
  * 修改 /etc/fstab 设置对此逻辑卷的启动时挂载
  * 重新挂在 /etc/fstab 中的文件系统，检查挂装情况    


## 任务11：扩展现有的卷组和逻辑卷

1. 为系统中已经存在的 home 逻辑卷准备新的分区
  * 在第2块硬盘（/dev/sdb）上，使用全部剩余空间添加 1 个分区，类型为 8e00
  * 重启系统，使得 Linux 内核重新读取硬盘的新分区表
2. 管理LVM
  * 在新建的分区上创建物理卷
  * 将此物理卷扩展到 home 逻辑卷所在的卷组中
  * 扩展名为 home 的逻辑卷，大小为 8G
3. 扩展逻辑卷上的 xfs 文件系统
4. 若安装 CentOS 时没有使用硬盘的所有空间，请将剩余的所有空间加到 / 文件系统所在的卷组中

## 任务12：缩减逻辑卷

1. 解除对 mysql 逻辑卷 的挂装
2. 强行检查 mysql 逻辑卷上的 ext4 文件系统
3. 将 mysql 逻辑卷缩减至原始大小的 50%
4. 缩减 mysql 逻辑卷上的 ext4 文件系统使之适应逻辑卷的新大小
5. 重新挂装 mysql 逻辑卷
6. 检查 mysql 逻辑卷上文件系统的大小

## 任务13*：逻辑卷快照

1. 在 mysql 逻辑卷的挂装点目录里创建一个测试文件，如：
        lvs > /var/lib/mysql/test
        cat /var/lib/mysql/test
2. 对 mysql 逻辑卷创建名为 mysql_snap 的只读快照卷，大小为 1G
3. 将快照卷 mysql_snap  挂装到 /lvmsnap/mysql 目录
4. 在 mysql 逻辑卷的挂装点目录里修改测试文件，如：
        (lvs ；vgs) > /var/lib/mysql/test
        cat /var/lib/mysql/test
5. 验正快照卷的功能，如
        cat /lvmsnap/mysql/test
6. 将快照卷里的内容备份到 /backup/mysql
7. 解除对快照卷的挂装
8. 删除快照卷 mysql_snap
9. 删除 mysql 卷上的测试数据


>#####参考
>* [Linux LVM 简明教程](https://linux.cn/article-3218-1.html)


## 任务14： 在 ext4 文件系统上配置用户的磁盘限额

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

## 任务15： 在 xfs 文件系统上配置用户的磁盘限额

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
