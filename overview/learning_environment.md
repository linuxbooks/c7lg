# 学习环境

## 个人学习环境

* 自备 **笔记本电脑**/台式机
  * CPU 支持硬件虚拟化技术
  * 内存 >= 8G
  * 桌面操作系统为 **Windows 10/7** 或 MacOS 或 LinuxMint/Ubuntu
  * 能连接公网
  * 使用开源虚拟化软件 **VirtualBox** 安装 Linux 系统虚拟机

> **参考**
>
> *  Mac 用户：[Awesome Mac](https://github.com/jaywcjlove/awesome-mac)
> *  Win 用户：[Awesome Windows](https://github.com/Awesome-Windows/Awesome)

## Windows 下的软件获取

* 国内
  * 360 软件管家
  * 腾讯软件管理
  * 百度软件管理 
* 国外
  * [PortableApps for Windows](http://portableapps.com)
  * **[Chocolatey](https://chocolatey.org)**

>* [Microsoft's open source project hosting web site](http://www.codeplex.com)
>* [SourceForge](https://sourceforge.net/)

## 软件包管理器（命令行工具）

* Linux： `yum`/`apt`...
* Mac： `brew`
* Windows：`choco` 

## Chocolatey

* **以管理员身份运行** PowerShell
* 查看执行策略:  `Get-ExecutionPolicy`
* Windows PowerShell 加载配置文件并运行脚本的条件
  * *Restricted*:  允许执行单独的命令，但阻止所有脚本文件的运行
  * *RemoteSigned*: 要求从 Internet 下载的脚本和配置文件需具有受信任的发布者的数字签名
  * *AllSigned*: 要求所有脚本和配置文件都由受信任的发布者签名，包括在本地计算机上编写的脚本
  * *Bypass*: 不阻止任何内容，并且没有任何警告或提示
* **设置执行策略**: 
  * `Set-ExecutionPolicy AllSigned`
  * `Set-ExecutionPolicy RemoteSigned -Scope CurrentUser` 
* **安装** Chocolatey
  * `iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))`
* **使用** Chocolatey
  * `choco --help`
* 优缺点

> 参考： [about_Execution_Policies](https://technet.microsoft.com/zh-CN/library/hh847748.aspx)


## Windows 下的 必备/常用 工具

* 必备工具
  * **虚拟化软件** -- [VirtualBox](https://www.virtualbox.org/)
  * **`cmd` 替代品** -- [cmder/cmdermini](http://cmder.net/)
  * **Git** -- [git-for-windows](http://git-for-windows.github.io)
  * **`nodepad` 替代品** -- [nodepad++](https://notepad-plus-plus.org/)
* 常用工具
  * 远程登录工具 -- [Putty](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)
  * 命令行下载工具 -- [aria2](https://aria2.github.io/)
  * 开发环境创建工具 -- [Vagrant](https://www.vagrantup.com/)
  * 代码等宽字体 -- [Source Code Pro](http://adobe-fonts.github.io/source-code-pro/)
  * `PATH` 环境变量编辑 -- [Path Editor](https://patheditor2.codeplex.com/)
  * `HOSTS` 文件编辑器 -- [Hosts File Editor](https://scottlerch.github.io/HostsFileEditor/) 
  * 压缩/解压工具 -- [7zip](http://www.7-zip.org/)
  * 显示目录磁盘占用 -- [TreeSize](http://www.jam-software.de/treesize_free/)
  * 局域网络扫描 -- [Advanced IP Scanner](http://www.advanced-ip-scanner.com/cn/)
  * 路由跟踪 -- [Best Trace](http://www.ipip.net/)
  * MS Sysinternals Troubleshooting Utilities -- [Sysinternals Suite](https://docs.microsoft.com/en-us/sysinternals/downloads/sysinternals-suite)
  * 屏幕截图 -- [Greenshot](http://getgreenshot.org/)
  * 文件 HASH 码校验 -- [HashTab](http://implbits.com/products/hashtab/)
  * 多重引导U盘创建器 -- [YUMI](https://www.pendrivelinux.com/yumi-multiboot-usb-creator/)

> 参考：[Win下必备神器之Cmder ](https://segmentfault.com/a/1190000004408436)

## 机房环境

* 解决 Linux 系统安装问题
  * 部署 PXE 自动安装服务器（cobbler）
  * 使用现成的 **VirtualBox** 虚拟机镜像文件（`.ova`） 准备可用的Linux虚拟机
  * 使用现成的 **Vagrant** 虚拟机镜像文件（`.box`） 准备可用的Linux虚拟机
* 解决 Linux 软件安装问题
  * 从公网镜像 CentOS 的官方仓库和 EPEL 仓库到本地 YUM 服务器
  * 从公网镜像或预先下载 虚拟机镜像文件（`.ova`/[.box](http://cloud.centos.org/centos/7/vagrant/x86_64/images/)）
  * 避免镜像的另一个选择是架设面向 YUM/APT 的代理服务器并预热
* 解决 ISO 和虚拟机镜像文件的下载加速问题
  * 使用 P2P 下载工具 [Resilio](https://www.resilio.com/) 或 [Syncthing](https://syncthing.net)
