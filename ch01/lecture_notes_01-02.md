# CH01U02 - 安装 Linux 

## 安装前的准备

* 获知 CentOS 7 发型注记
  * https://wiki.centos.org/Manuals/ReleaseNotes
  * https://access.redhat.com/documentation/en/red-hat-enterprise-linux/
* [RHEL/CentOS technology capabilities and limits](https://access.redhat.com/articles/rhel-limits)
* 获取 CentOS 7 的 ISO 文件
  * https://www.centos.org/download/
  * https://wiki.centos.org/Download
  * 校验 ISO 文件的完整性
  * 物理机安装需要刻录光盘或写入U盘
* 为安装 Linux 系统规划硬盘空间
  * 考虑是否支持双系统引导
  * 考虑分区或 LVM 布局
* 为安装 Linux 系统规划网络配置信息 

## 硬盘分区表（DPT）

* 两种磁盘地址表示
  * **CHS**：[柱面-磁头-扇区（Cylinder-Head-Sector）](https://en.wikipedia.org/wiki/Cylinder-head-sector)
  * **LBA**：[逻辑块地址（logical block addressing）](https://en.wikipedia.org/wiki/Logical_block_addressing)
* 两种类型的磁盘分区表
  * **MBR** -- [主引导记录（Master Boot Record）](https://en.wikipedia.org/wiki/Master_boot_record)
    * 位于：**磁盘主引导扇区**，即硬盘的第一个扇区
      * 使用**CHS** 地址表示位于硬盘的 0柱面，0磁头，1扇区。
    * 组成：启动引导器（BootLoader）、**硬盘分区表（Disk Partition Table）** 和 有效结束标志
  * **GPT** -- [全局唯一标识分区表（GUID Partition Table）](https://en.wikipedia.org/wiki/GUID_Partition_Table)
    * GPT 使用 **LBA** 替换了 **CHS** 地址表示
    * 主分区表位于磁盘开始的 LBA 1~33 ，次分区表位于磁盘结尾的 LBA -1 ~ -33

|   　    | MBR/DOS  | GPT  
| ------- | -------------------------------- | --------------------------------
| 位于    | 硬盘主引导扇区的第447~510字节中   | LBA1 ~ LBA33 和 LBA -1 ~ LBA -33
| 分区个数 | 4个主分区，或3个主分区加一个扩展分区 | 128 个主分区
| 分区大小 | 最大 2.2TB（2^32 sectors × 512 bytes） | 最大 9.4ZB （2^64 sectors × 512 bytes）
| 冗余支持 | 　 | 提供备份分区表和循环冗余校检 (CRC) 保护

>* **GUID** -- Globally Unique IDentifiers
>* [MBR、GPT的结构和区别](http://dmwing.blog.51cto.com/11607397/1843254)

## MBR 示意图

![MBR Scheme](/assets/figs/MBR_Scheme.png)

## GPT 示意图

![GPT Scheme](/assets/figs/GPT_Scheme.png)

## 两种类型的系统固件

|   　         | legacy **BIOS** firmware            | **UEFI** firmware 
| ------------ | ----------------------------------- | -------------------
| BootLoader   | 位于硬盘主引导扇区的前446字节中 | 位于独立 **ESP**（EFI System Partition）分区
| 对 GPT 的支持 | 仅能读取 GPT 中的 LBA0        | 可以直接读取
| 特点         |  已过时                      | 可操作性、安全性、兼容性、可扩展性

>* **BIOS** -- [Basic Input/Output System](https://en.wikipedia.org/wiki/BIOS)
>* **UEFI** -- [Unified Extensible Firmware Interface](https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
>* **ESP** -- [EFI System Partition](https://en.wikipedia.org/wiki/EFI_system_partition)
>* [GPT+UEFI与BIOS+MBR有什么区别（Windows）](http://www.kqidong.com/bios/876.html)
>* [UEFI+GPT与BIOS+MBR各自有什么优缺点](https://www.zhihu.com/question/28471913)

|   　      |   **BIOS**         |   **UEFI**
| --------- | ---------------------------- | -------------------
|  **MBR**  | 可对额外的数据磁盘使用 GPT 分区   | 降级为成 Legacy 模式并开启 CSM（Compatibility Support Module），无实际意义
|  **GPT**  | 可启动，且需创建为 GRBU 使用的 **BIOS boot** 分区 | 可启动，且需创建 **ESP** 分区

>* [类 UNIX 操作系统对 GPT 的支持](https://en.wikipedia.org/wiki/GUID_Partition_Table#UNIX_and_Unix-like_systems)

## 磁盘分区的设备名

* Linux 中用设备名来访问设备，磁盘也不例外
  * Linux 下的设备名存放在 /dev 目录中
  * 磁盘设备以 **sd** 开始
  * 以字母 a、b、c 等区分不同的硬盘
  * 以数字 1、2、3 等区分不同的分区
* 例如
  * /dev/sda1 表示第1块硬盘的第1个分区
  * /dev/sdc7 表示第3块硬盘的第7个分区

> 对于 MBR 分区表，数字编号 1~4 留给主分区或扩展分区使用，逻辑分区编号从 5 开始

## Linux 环境下如何使用分区

* 在 Linux 环境下没有 Windows 中盘符（如：C:）的概念
* 将每个分区当成目录使用，此目录称为“挂装点”（Mount Point）

![文件系统挂装点](/assets/figs/monunt-point.png)

>* https://wiki.archlinux.org/index.php/Partitioning

## Linux 下的文件系统

* 在 Linux 系统上划分了分区之后，还要在分区上创建文件系统
  * Linux 下创建文件系统的操作相当于 Windows 下的磁盘格式化操作
* Linux 下常用的文件系统类型为：ext2/3/4、XFS、ZFS、btrfs
  * Windows 系统常用的文件系统类型为 FAT32、exFAT（FAT64）、NTFS

## LVM 的引入

* 逻辑盘卷管理（LVM，Logical Volume Manager）
  * 是建立在 硬盘 和/或 物理分区 之上的一个逻辑层
  * 为文件系统屏蔽下层磁盘分区布局
  * 提高磁盘分区管理的灵活性
* 使用 LVM 的优势
  * 可以在多个物理磁盘设备间重新组织文件系统
  * 可以重新设定（扩展/收缩）文件系统的大小

![LVM 结构图](/assets/figs/lvm.png)

## 执行安装

* 安装程序的启动方式：
  * 光盘
  * USB设备
  * 引导装载程序，比如 GRUB
  * 网络（PXE）
* 支持的安装源：
  * 网络服务器（ftp、http 或 nfs）
  * 光盘
  * 硬盘

## 多种安装方式

* 本地安装和远程安装
  * **本地安装**：安装源保存在本地光盘或本地硬盘的ext2/3/4分区或vfat(FAT32)分区
  * **远程安装**：安装源保存在网络服务器中，并以 HTTP/FTP/NFS协议的服务器提供
* 手动安装和自动安装
  * **手动安装**：在安装过程中逐一回答安装程序所提出的问题
  * **自动安装**：以自动应答文件（Kickstart 文件）自动回答安装程序所提出的问题

>* [hardened-centos7-kickstart](https://github.com/fcaviggia/hardened-centos7-kickstart)
>* [centos-7-kickstart-example](https://github.com/archonik/centos-7-kickstart-example)

## 安装程序 —— Anaconda

* 是由 Python 语言编写的 Linux 安装程序
  * Anaconda 是基于Linux平台的应用程序，因此必须先启动一个Linux内核以便运行之
* Anaconda 的三种工作模式
  * Update模式 —— 用于安装和更新
  * Kickstart模式 —— 用于实现自动安装
  * Rescue模式 —— 用于为无法引导的系统故障修复
* Anaconda 的访问界面
  * 图形安装界面 —— 默认界面
  * 文本安装界面 —— 通过 `inst.text` 启用
  * VNC 安装界面 —— 通过 `inst.vnc` 启用
    * 使用 `inst.vncconnect=<HOST>:<PORT>` 指定主动连接的VNC客户端的主机名或IP地址以及端口号(默认端口号为5900) 
    * 使用 `inst.vncpassword=<PASSWORD>` 指定VNC的联机口令

## 本地光盘最小化安装 CentOS 7

* 使用光盘引导系统
* 选择安装过程使用的语言
* 安装信息概要
  * 本地化 
    * 语言
    * 日期时间
    * 键盘
  * 软件
    * 安装源
    * 软件包选择  
  * 系统
    * 安装位置
      * 选择要安装的硬盘并配置分区/逻辑卷布局
        * 可以手动或者自动设置 
      * 引导装载程序配置
    * KDUMP：是否启用KDUMP（当系统崩溃时将内存内容导出为磁盘文件） 
    * 网络和主机名：配置安装后的系统的主机名和网络参数
* 开始安装
* 用户设置
  * 设置超级用户 root 的口令
  * 添加普通用户并为其设置口令 
* 安装完成
