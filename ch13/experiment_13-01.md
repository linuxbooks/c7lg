# 实验指导 13 - Samba 服务

>#### 学习目标
>* 配置任何人均可读写的共享
>* 配置认证用户或组可读写的共享
>* 使用 `smbpasswd` 命令管理 Samba 账户数据库
>* 使用 `testparm` 命令检查配置文件的正确性
>* 在 Linux 系统上使用 `smbclient` 命令访问 Samba 共享
>* 在 Linux 系统上挂装 Samba 共享 

## 任务1：配置任何人均可读写的共享

**要求**
* 全局配置
  * 无需用户认证（将不存在用户访问视为Guest账号访问）
  * 将工作组设置为 Windows 默认的 `WORKGROUP`
  * 仅允许本地回环网络和 192.168.56.0/24 访问
  * 指定客户端支持的最高协议版本为 `SMB3` 
* 共享名 `[share]`
  * 共享目录 `/srv/samba/share`
  * 任何人均可读写
* 共享名 `[ftp]`
  * 共享目录 `/var/ftp/upload`
  * 任何人均可读写
  * 对共享目录写入的文件具有 ftp 的属主及组
* 使用 `testparm` 命令检查配置文件的正确性
* 开启防火墙对 samba 服务的访问
* 测试
  * 在 Windows 系统上测试
  * 在 Linux 系统上使用 `smbclient` 命令测试 
  * 在 Linux 系统上挂装 Samba 共享进行测试 

>**提示** 注意 `map to guest = Bad User` 和 `map to guest = Never` （默认值）的区别。

## 任务2：配置认证 用户/组 可读/写 的共享

**要求**
* 全局配置
  * 需用户认证（用户必须输入正确的口令方可访问）
  * 将工作组设置为 Windows 默认的 `WORKGROUP`
  * 仅允许本地回环网络和 192.168.56.0/24 访问
  * 指定客户端支持的最高协议版本为 `SMB3` 
* 共享名 `[homes]`
  * 共享用户自家目录
  * 仅用户自己可读写
  * 仅用户自己可以看到 
* 共享名 `[cdrom]`
  * 共享目录 `/media/cdrom`
  * 任何认证用户均可读
* 共享名 `[tmp]`
  * 共享目录 `/tmp`
  * 任何认证用户均可读写
* 共享名 `[staff]`
  * 共享目录 `/srv/samba/staff`
  * `staff` 组成员均可读写
  * 新建的文件或目录的组为 `staff`
  * 其他人没有任何权限
* 共享名 `[staff2]`
  * 共享目录 `/srv/samba/staff2`
  * `staff` 组成员均可读
  * `staff` 组成员 tony 可读写
  * 新建的文件或目录的组为 `staff`
  * 用户 osmond（不是 `staff` 组成员）可读写 
  * 其他人没有任何权限
* 使用 `smbpasswd` 命令创建 Samba 用户
* 使用 `testparm` 命令检查配置文件的正确性
* 开启防火墙对 samba 服务的访问
* 测试
  * 在 Windows 系统上测试
  * 在 Linux 系统上使用 `smbclient` 命令测试
  * 在 Linux 系统上挂装 Samba 共享进行测试 


>**参考**
>* http://www.techrepublic.com/article/how-to-manage-user-security-in-samba/
