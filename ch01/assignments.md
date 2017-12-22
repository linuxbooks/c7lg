# CH01 - 家庭作业

## 安装和使用其他 Linux 发行版 

* 安装 Debian/Ubuntu 服务器（择其一）
  * [Ubuntu Server](https://www.ubuntu.com/download/server)
  * [Debian](http://www.debian.org/CD/http-ftp/#stable)
  * [Proxmox Virtual Environment](https://pve.proxmox.com/)
    * 基于 Debian
    * 支持 KVM 和 LXC 虚拟化技术
    * 提供 CLI 和 WUI 
    * [Proxmox VE Documentation](https://pve.proxmox.com/pve-docs/)
* 安装和使用 Linux 桌面发行版（择其一）
  * [LinuxMint](https://linuxmint.com/)
  * [Ubuntu Desktop](https://www.ubuntu.com/download/desktop)
  * [Fedora Workstation](https://getfedora.org/workstation/)
  * [深度操作系统桌面版](https://deepin.org/) -- 基于 Debian
  * [优麒麟操作系统](http://www.ubuntukylin.com/) -- 基于 Ubuntu

>**参考**
>
>* [Linux Distribution Introduction and Overview](https://www.linuxtrainingacademy.com/linux-distribution-intro/)
>* [Top Ten Distributions list at DistroWatch.com](http://distrowatch.com/dwres.php?resource=major)
>* [Must-have applications for your fresh Linux desktop install](https://www.linuxtrainingacademy.com/must-have-linux-apps/)

## 使用 Windows 下的开源软件

* CMD 替代品 -- [Cmder](http://cmder.net/)
* 办公套件 -- [LibreOffice](http://www.libreoffice.org)
* 浏览器 -- [FireFox](http://firefox.com.cn)
* 文本编辑和IDE -- [Atom](http://atom.io)
* 版本控制 -- [Git](https://git-scm.com/downloads)
* 集成 GitHub 的命令行工具 -- [gitsome](https://github.com/donnemartin/gitsome)

* 电子图书管理 -- [calibre](http://calibre-ebook.com/)
* 口令管理 -- [KeePass](http://www.keepass.info/)
* 剪贴板管理器 -- [CopyQ](http://hluk.github.io/CopyQ)
* 即时通信 -- [Franz](http://meetfranz.com)、[Electronic WeChat](https://github.com/geeeeeeeeek/electronic-wechat)
* 字体编辑器 -- [trufont](https://github.com/trufont/trufont)

## Windows 软件包管理

学习 Windows 下的包管理工具 [chocolatey](https://chocolatey.org/) 的安装和使用

```
    > choco -y install cmdermini yumi wget aria2 putty mtputty sysinternals
    > choco -y install chocolateygui
```

>##### 参考
>* <https://chocolatey.org/install>
>* <https://chocolatey.org/docs>
>* [Windows下自动化部署的救赎](http://www.docin.com/p-1134872994.html) -- [视频](http://v.youku.com/v_show/id_XOTIzOTA4MjY4.html)
>* [Boxstarter](http://boxstarter.org/)
>* [Windows Sysinternals](https://technet.microsoft.com/en-us/sysinternals/bb842062.aspx) -- [微软极品Sysinternals Suite工具包使用指南](http://www.win7china.com/html/6691.html)

## 使用 Vagrant 安装 Linux 虚拟机

>* [下载 Vagrant](https://www.vagrantup.com/downloads.html) 并安装
>* [下载 VirtualBox](https://www.virtualbox.org/wiki/Downloads) 并安装

### 使用 Vagrant 安装 CentOS7

```
    > cd %USERPROFILE%
    > mkdir boxes\centos7
	> cd boxes\centos7
	
	> vagrant box add boxcutter/centos73
	> vagrant box list
	
	> vagrant init boxcutter/centos73
	
	> vagrant up
	> vagrant status
	> vagrant ssh

	[vagrant@localhost ~]$ sudo yum -y reinstall man-db man-pages
	[vagrant@localhost ~]$ sudo mandb -c
	[vagrant@localhost ~]$ man 7 passwd
	[vagrant@localhost ~]$ mkdir /vagrant/exercises
	[vagrant@localhost ~]$ touch /vagrant/exercises/test
	[vagrant@localhost ~]$ logout
	
	> vagrant halt
	> vagrant status
	> vagrant --help
```

>**参考** 
>
>* https://www.vagrantup.com/
>* [Deploy Your Very Own Linux Server with Full Root Access](https://www.linuxtrainingacademy.com/create-build-test-drive-deploy-linux-server-full-root-access/)

### 使用 Vagrant 安装 Ubuntu & gitbook

```
    > cd %USERPROFILE%
    > mkdir boxes\ubuntu1604
	> cd boxes\ubuntu1604
	
	> vagrant box add boxcutter/ubuntu1604
	> vagrant box list
	
	> vagrant init boxcutter/ubuntu1604
	> vagrant up
	> vagrant status
	> vagrant ssh
```

```
sudo curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -                            
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
sudo apt-get update && sudo apt-get install yarn

sudo yarn config get registry
sudo yarn config set registry https://registry.npm.taobao.org

sudo yarn global add gitbook-cli
nodejs -v
sudo ln -s /usr/bin/nodejs /usr/bin/node
nodejs -v
gitbook -V
```
```
    gitbook help
	gitbook init
    gitbook serve
```