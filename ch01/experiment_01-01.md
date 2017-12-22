# 实验指导 1.1 - 安装 Linux 虚拟机

>#### 学习目标
> * 安装和使用 VirtualBox
> * 最小化安装 CentOS 7


## 任务1：下载并安装 VirtualBox

1、从 <https://www.virtualbox.org/wiki/Downloads> 下载

* VirtualBox platform packages
* Oracle VM VirtualBox Extension Pack

2、双击下载文件安装

## 下载并校验 CentOS 7 ISO

1、从 <http://mirrors.163.com/centos/7/isos/x86_64/> 下载

* CentOS-7-x86_64-Minimal-1611.iso
* sha256sum.txt

2、从 <https://git-scm.com/download/win> 下载 Git for Win 并双击安装

3、校验 CentOS 7 ISO

（1）在文件管理器中进入 ISO文件和 sha256sum.txt 所在目录

（2）鼠标右键点击空白处，在菜单中运行 “Git Bash Here”

（3）执行命令进行校验

    $ grep 'Minimal' sha256sum.txt | sha256sum -c
	或
    $ sha256sum -c sha256sum.txt 2>&1 | grep OK

## 任务2：创建并运行 VirtualBox 虚拟机

1、运行 VirtualBox，单击 “新建” 按钮

（1）虚拟电脑名称和类型

* 名称：cent7h1
* 类型：Linux
* 版本：Red Hat （64-bit）

（2）内存大小 1024M

（3）虚拟硬盘 

* 虚拟硬盘文件类型：VMDK
* 分配类型：动态分配
* 大小：20G
   
2、单击 “设置” 按钮

（1）存储：为虚拟光驱分配 ISO 文件

（2）网络：1）网卡1：NAT ； 2）网卡2：Host-only

3、单击 “启动” 按钮运行虚拟机

## 任务3：最小化安装 CentOS 7

1、进入安装引导界面，选择 “Install CentOS 7” 并回车

2、选择安装过程使用的语言 “中文”

3、安装配置

（1）配置键盘布局  —— 英语（美国） 

（2）安装设备并分区 —— 自动配置分区（使用 LVM 方式），修改自动分区布局，将 / 文件系统所在的逻辑卷调整为 8GiB

（3）配置网络和主机名

  1）开启两个以太网卡
  
  2）对于被 VirtualBox 设置了 NAT 类型的网卡使（由 VirtualBox 自动分配网络参数）
  
  3）对于被 VirtualBox 设置了 Host-only 类型的网卡设置静态网络参数 192.168.56.71/24，并设置开机启用此网卡

（4）用户设置

  1）设置root用户口令
  
  2）创建名为 student 的的普通用户、设置其口令，并将其加入 wheel 组

（5）安装完毕，重新启动


## 参考资源

* https://wiki.centos.org/Download/Verify
* https://www.centos.org/keys/
* https://wiki.centos.org/TipsAndTricks/sha256sum

* https://access.redhat.com/documentation/zh_cn/red-hat-enterprise-linux/
* https://access.redhat.com/documentation/zh-CN/Red_Hat_Enterprise_Linux/7/html/Installation_Guide/