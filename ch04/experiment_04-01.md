# 实验指导 4.1 - 磁盘分区与文件系统管理

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
      wget http://www.tinycorelinux.net/8.x/x86/release/Core-current.iso 
* 创建 /mnt/iso 挂装点
* 将 iso 文件只读挂装到 /mnt/iso
* 显示挂装点目录的内容
* 解除挂装

## 任务6：文件系统检查和修复

>**对挂装点 /data 和 /srv 分别进行如下操作

* 手动卸装文件系统
* 检查文件系统
* 向挂装点对应的分区里写入连续随机数据，模拟分区损坏
  * 越过 100 块，像设备写入 10 块（每块 512 字节）数据
* 检查文件系统
* 修复文件系统
* 重新挂装文件系统，并查看分区中的原有数据