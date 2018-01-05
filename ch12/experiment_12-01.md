# 实验指导 12 - FTP 服务和 NFS 服务

>#### 学习目标
>* 配置匿名 FTP 服务
>* 配置本地用户 FTP 服务
>* 配置虚拟用户 FTP 服务
>* 配置基于 SSL/TLS 的 FTP 服务
>* 配置 NFS 服务和远程挂载


## 任务1：配置匿名 FTP 服务

**要求**
* 关闭本地用户访问
* 设置用户登录后提示为 “Welcome to our anonymous FTP service.”
* 匿名用户不能离开匿名服务器目录 /var/ftp，且只能下载不能上传
* 允许匿名用户上传到目录 /var/ftp/upload
* 允许匿名用户在 /var/ftp/upload 目录中创建目录、文件更名、删除文件
* 设置所有客户机的最大连接数为 100
* 设置每个客户机的最大连接数为 2
* 设置最大传输速率为 500KB/s
* 设置数据被动连接端口范围：10100~10200
* 开启防火墙允许访问 ftp 服务
* 自定义 firewalld 的配置文件 ftp.xml 添加被动连接端口范围

## 任务2：配置本地用户 FTP 服务

**要求**
* 关闭匿名用户访问
* 设置用户登录后提示为 “Welcome to our FTP service.”
* 本地用户可以上传、下载、创建目录、文件更名、删除文件
* 将本地用户限制在其自家目录中
* 禁止 fany 用户访问 FTP 服务
* 设置所有客户机的最大连接数为 200
* 设置每个客户机的最大连接数为 2
* 设置最大传输速率为 500KB/s
* 设置 tony 用户的最大传输速率为 1MB/s
* 设置数据被动连接端口范围：10100~10300
* 禁止 192.168.122.0/24 访问 FTP 服务
* 开启防火墙允许访问 ftp 服务
* 自定义 firewalld 的配置文件 ftp.xml 添加被动连接端口范围


## 任务3：配置基于 SSL/TLS 的 FTP 服务

**要求**
* 匿名用户无需SSL支持
* 本地用户的登录和数据传输均启用SSL/TLS
* 使用 第8章 任务10 创建的证书和私钥文件
  * ftp.olabs.lan.{crt,key}


## 任务4：配置虚拟用户 FTP 服务

**要求**
* 关闭匿名和本地用户访问
* 设置用户登录后提示为 “Welcome to our FTP service.”
* 虚拟用户可以上传、下载、创建目录、文件更名、删除文件
* 将虚拟用户限制在其登录目录中
* 开启防火墙允许访问 ftp 服务

```
# cat /etc/vsftp/vusers.txt
virtual-username1
password1
virtual-username2
password2
virtual-username3
password3
# useradd -d /srv/vftp -s /sbin/nologin vftp
# for u in `sed -n 1~2p /etc/vsftp/vusers.txt`；do
   mkdir -p /srv/vftp/$u
   chown vftp: /srv/vftp/$u
done
# db_load -T -t hash -f /etc/vsftp/vusers.txt /etc/vsftp/vusers.db
# chmod 600 /etc/vsftp/vusers.*
```

## 任务5：配置 NFS 服务和远程挂载

**要求**
* 在服务器端设置共享
  * 所有网络客户可只读访问 /var/ftp/pub  
  * 为 192.168.56.0/24 和 192.168.122.0/24 可只读访问 /var/ftp/yum ，但是 192.168.56.100/24 可读写
  * 为 192.168.56.30 设置对 /backup 的读写共享，且 root 可以以 root 权限访问而不是默认的 nfsnobody 用户权限
  * 为 192.168.56.0/24 设置对 /var/ftp/update 的读写共享，且全部访问者均映射为服务器本地的ftp用户和ftp组 
  * 开启防火墙对 NFS 服务的访问
  * 使用 `exportfs` 重新导出全部共享
* 在客户端挂载共享
  * 使用 `showmount` 查看 NFS 服务器的共享目录
  * 编辑 `/etc/fstab` 设置远程挂载




