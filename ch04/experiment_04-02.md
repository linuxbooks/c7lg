# 实验指导 4.2 - 逻辑卷管理

>#### 学习目标
> * 使用 `{pv,vg,lv}create` 创建 物理卷/卷组/逻辑卷
> * 使用 `{pv,vg,lv}{s,display}` 查看 物理卷/卷组/逻辑卷
> * 使用 `{vg,lv}{extend,reduce}` 扩展和收缩 卷组/逻辑卷 
> * 使用 `resize2fs` 扩展和收缩 ext 文件系统
> * 使用 `xfs_growfs` 扩展 xfs 文件系统

## 任务1：创建基于新硬盘上的卷组和逻辑卷

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


## 任务2：扩展现有的卷组和逻辑卷

1. 为系统中已经存在的 home 逻辑卷准备新的分区
  * 在第2块硬盘（/dev/sdb）上，使用全部剩余空间添加 1 个分区，类型为 8e00
  * 重启系统，使得 Linux 内核重新读取硬盘的新分区表
2. 管理LVM
  * 在新建的分区上创建物理卷
  * 将此物理卷扩展到 home 逻辑卷所在的卷组中
  * 扩展名为 home 的逻辑卷，大小为 8G
3. 扩展逻辑卷上的 xfs 文件系统
4. 若安装 CentOS 时没有使用硬盘的所有空间，请将剩余的所有空间加到 / 文件系统所在的卷组中

## 任务3：缩减逻辑卷

1. 解除对 mysql 逻辑卷 的挂装
2. 强行检查 mysql 逻辑卷上的 ext4 文件系统
3. 将 mysql 逻辑卷缩减至原始大小的 50%
4. 缩减 mysql 逻辑卷上的 ext4 文件系统使之适应逻辑卷的新大小
5. 重新挂装 mysql 逻辑卷
6. 检查 mysql 逻辑卷上文件系统的大小

## 任务4*：逻辑卷快照

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
