# 阶段测验 3


## 一、判断题

```
1. rndc 与 bind 的通信是利用基于共享加密的数字签名技术来实现的，所以要让 rndc 控制 bind，必须配置验证密钥。 ( )

2. 在CentOS环境下，默认的apache子进程将以apache用户和apache组来运行。( )

3. 不同的操作系统之间无法进行数据交换。( )

4. LAMP 代表了 Linux 平台上的 Apache、MySQL 以及 PHP、Perl 和 Python等网络编程语言的结合。( )

7. 在任何一个需要动态分配IP地址的subnet语句里，至少要有一个range语句，用于说明要分配的IP地址范围。( )

8. Vsftpd 不支持对不同的 主机/网络 实施不同的配置。( )

9. 远程服务器只开启了对 22 和 80 端口的访问，若客户端需要访问远程服务器的 3306 端口，
   在不修改服务器防火墙配置的情况下，可以通过创建SSH隧道的方式访问远程服务器的 3306 端口。( )

10. 配置 Apache 2.4 的基于域名的虚拟主机，必须使用 NameVirtualHost 指令。( )

```

## 二、单选题

```
1. 下面哪个命令不能检查服务配置文件语法的正确性。 （   ）

    A. httpd -t
    B. dhcpd -t
    C. postconf -t
    D. named-checkconf
    E. testparm

2. 下面哪个DHCP服务配置参数用于为客户机指定默认网关  （   ）

    A. domain-name
    B. domain-name-servers
    C. ntp-servers
    D. routers

3. 在Linux环境下，若bind服务器的主配置文件内容如下：（   ）

    options {
        directory "/var/named";
    };
    zone "localhost" IN {
        type master;
        file "localhost.zone";
        allow-update { none; };
    };
	
    则loscalhost的正向解析域的数据库文件的绝对路径文件名是什么？

    A. /localhost.zone
    B. /var/named/localhost.zone
    C. /etc/localhost.zone
    D. /etc/named/localhost.zone

4. 下面是bind服务器 test.com 域的正向解析数据库文件的内容：（   ） 

    $ttl 38400
    test.com.       IN      SOA     cent7.test.com root.cent7.test.com (
                        1061808326
                        10800
                        3600
                        604800
                        38400 )
                    IN      NS      cent7.
    cent7           IN      A       192.168.1.100

	在此文件中有几处错误？

	A. 1            B. 2             C. 3            D. 4

5. 下面哪个 test.com 域的 SOA 记录是正确的？（   ）

    A.
    test.com.       IN      SOA     cent7. root.cent7.test.com (
                            1061808326
                            10800
                            3600
                            604800
                            38400 )
    B.
    test.com.       IN      SOA     cent7.test.com root.cent7.test.com (
                            1061808326
                            10800
                            3600
                            604800
                            38400 )
    
    C.
    test.com.       IN      SOA     cent7.test.com. root@cent7.test.com. (
                            1061808326
                            10800
                            3600
                            604800
                            38400 )
    D.
    test.com.       IN      SOA     cent7.test.com. root.cent7.test.com. (
                            1061808326
                            10800
                            3600
                            604800
                            38400 )

6. Apache 配置文件 /etc/httpd/conf/httpd.conf 中的 “KeepAlive On”表示什么？ （   ）

    A. 每请求一个文件就跟apache服务器建立一次连接
    B. 每次连接apache服务器能提出多个文件请求
    C. 每请求一个文件，apache服务器需要建立多次连接
    D. 以上均不对

7. 当 Apache 服务器启动时，httpd进程的数目由配置文件 httpd.conf 中的什么配置语句决定？（   ）

    A. StartServers
    B. SpareServers
    C. InitServers
    D. MinSpareServers

8. 下面关于Apache配置的叙述错误的是？（   ）

    A. 对指定目录的访问权限配置可以放在主配置文件的<Directory>或<DirectoryMatch>容器中
    B. 对指定目录的访问权限配置可以放在此目录的.htaccess配置文件中
    C. 对指定文件的访问权限配置可以放在主配置文件的<Files>或<FilesMatch>容器中
    D. 对指定文件的访问权限配置可以放在文件所在目录的.htaccess配置文件中
    E. 对指定URL的访问权限配置可以放在主配置文件的<Location>或<LocationMatch>容器中

9. 在/etc/named.conf文件中用下列那种类型定义根区域？（   ）

    A. master          B. slave           C. hint             D. root

10. 在apache服务器的配置文件httpd.conf中，哪个参数用于指定apache服务器的根目录？（   ）

    A. Root         B. ServerRoot      C. DocuementRoot       D. HttpdRoot

11. 在apache服务器的配置文件httpd.conf中，哪个参数用于指定apache的文档根目录？（   ）

    A. FileRoot        B. ServerRoot       C. DocuementRoot    D. HttpdRoot  

12. 下面哪个数据库软件不能运行于 Linux 环境？ （   ）

    A. MySQL                   B. MSSQL               C. PostgreSQL
    D. Oracle                  E. Sybase              F. SqLite

13. 不能使用哪种方法建立 Apache 虚拟站点: （   ）

    A. 使用多个IP地址                         B. 使用不同的端口    
    C. 启动多个Apche服务器                    D. 使用不同的域名

14. 下列哪条命令可以启动 CentOS 下的 apache 服务? （   ）

    A. /etc/httpd start	                   B. service httpd start	
    C. service apache2 start               D. service apache start		

15. 下列哪条命令可以停止CentOS 下的 bind 服务? （   ）

    A. /etc/bind stop                 B. service bind stop
    C. /etc/named stop                D. service named stop		

16. 对于 CentOS 提供的 vsftpd 默认设置来说，下列错误的是 （   ）

    A. 允许匿名用户和本地用户登录
    B. 匿名用户不能离开匿名服务器目录/var/ftp，且能进行上传和下载
    C. 本地用户可以离开自家目录切换至有权访问的其他目录，并在权限允许的情况下进行上传和下载
    D. 本地用户的登录名为本地用户名，口令为此本地用户的口令

17. 要设置 vsftpd 本地用户的最大传输速率为500KB/s，需要在主配置文件中设置如下哪个语句：（   ）

    A. local_max_rate=50000                B. anon_max_rate=50000
    C. virtual_max_rate=50000              D. guest_max_rate=50000

18. 在vsftpd中，要设置虚拟用户的最大传输速率为500KB/s，需要在主配置文件中设置如下哪个语句：（   ） 

    A. local_max_rate=50000                B. anon_max_rate=50000
    C. virtual_max_rate=50000              D. guest_max_rate=50000

19. 在vsftpd中，用于设置用户连接服务器后的显示信息的指令是：（   ）

    A. message_file         B. ftpd_banner      C. dirmessage_enable       D. banner

20. 下面哪个不是 vsftpd 的配置指令：（   ）

    A. listen       B. listen_port       C. listen_address       D. listen_hostname

21. 下面是一个 bind 服务器配置的 test.com 正向域的SOA记录：

    test.com.       IN   SOA     cent7.test.com. root.cent7.test.com. (
                        1061808326
                        10800
                        3600
                        604800
                        38400 )
    下面说法错误的是？ （   ）

     A. 1061808326是本区信息文件的版本号
     B. 当配置文件修改以后，要修改版本号，一般将版本号加1
     C. 数字10800、3600、604800和38400的单位是秒
     D. 604800是辅助域名服务器向本地主服务器更新数据库的时间间隔

22. 关于 Linux 服务器，下列说法错误的是？ （   ）

    A. 配置 Apache 2.2 的基于 IP 的虚拟主机，不需要使用 NameVirtualHost 指令。
    B. 如果用户在远程FTP服务器上拥有账号，且此账号只能用于文件传输服务，则称此用户为FTP虚拟用户。
    C. 在Linux环境下，可以使用 iptable 命令来配置 NAT。 
    D. vsftpd从版本1.1.3以后内置了对TCP_wrappers的支持，为独立启动的vsftpd提供基于主机的访问控制。 
    E. 在 CentOS 环境下，默认的 apache 子进程将以 nobody 用户和 nobody 组来运行。

23. 在apache服务运行时，httpd进程的最大数目由配置文件 httpd.conf 中的什么配置语句决定？（   ） 

    A. StartServers           B. SpareServers           C. InitServers
    D. MaxSpareServers        E. MinSpareServers

24. Samba的两个守护进程的名称是？ （   ）

    A. sambad & bossad              B. smbd & nmbd
	C. cifsd & smbd                 D. samba & netbios 

25. 在Linux环境下，下面哪个命令可以像FTP客户端程序那样访问Samba的共享资源？（   ） 

    A. mount         B. smbftp         C. smbclient         D. smbmount

26. 使用 CentOS 默认安装的 apache 服务时，其主配置文件是？ （   ）

    A. /etc/httpd/conf/apache.conf
    B. /etc/httpd/httpd.cfg
    C. /etc/httpd/conf/httpd.conf
    D. /etc/httpd/apache.conf

27. 在postfix服务器的配置文件main.cf中，使用哪个参数设置接受邮件时收件人的域名？（   ）

    A. myorigin                B. myhostname            C. mydestination
    D. mydomain                E. mynetworks

28. 在postfix服务器的配置文件main.cf中，使用哪个参数设置发件人所在的域名？（   ）

    A. myorigin                B. myhostname            C. mydestination
    D. mydomain                E. mynetworks

29. 下列服务器软件中哪些不属于 MTA？（   ）

    A. sendmail                B. postfix               C. exim
    D. dovecot                 E. qmail

30. DNS域名系统主要负责主机名和（   ）之间的解析。 

    A. IP地址        B. MAC地址         C. 网络地址      D. 主机别名

31. Bind服务器的正向区文件中不可以存在哪个类型的资源记录 （   ）

    A. A     B. NS      C. MX      D. PTR      E. SOA     F. CNAME

32. postfix 服务器的主配置文件是？ （   ）

    A. /etc/postfix/master.cf
    B. /etc/main.cf
    C. /etc/postfix/main.cf
    D. /etc/postfix.cf

33. 用户发送邮件所使用的协议是？ （   ）

    A. imap 	      B. smtp       C. pop3       D. snmp

34. DNS允许将子域授权给其他组织进行管理，采用委托管理的优越性表现在 （   ）

    A. 分散工作负载
    B. 提高了域名服务器的响应速度
    C. 提高了网络带宽的利用率
    D. 以上均正确

35. Samba中，将不存在用户访问视为Guest账号访问，已存在的用户必须使用正确的口令访问的配置为 （   ） 

    A. map to guest = Never  
    B. map to guest = Bad User  
    C. map to guest = Bad Password  
    D. map to guest = Bad Uid  

36. 在 CentOS 7 中，启动基于 NFS V3 的NFS服务时，一定要先开启什么服务。（   ）

    A. XDR                  B. RPC               C. rpcbind 
    D. portmap              E. portmapper        F. nfs

37. NFS服务启动将通过读取本地服务器的哪个配置文件向网络上的主机提供 NFS文件共享服务。 （   ）

    A. /etc/hosts                B. /etc/inittab
	C. /etc/fstab                D. /etc/exports  

38. SAMBA 服务的默认安全级别是： （   ）

    A. share    B. user     C. server     D. domain     E. ads 

39. WWW服务器在因特网上使用最为广泛，它采用的是什么结构。（   ）

    A. C/S          B. B/S         C. 集中式          D. 分布式
	
40. 下面哪个命令可以列出 Apache 的所有模块 （   ）
	
    A. httpd -S       B. httpd -l      C. httpd -M      D. httpd -V
	
41. 下面哪个不是基于 PHP 的编程框架   （   ）

    A. Laravel            B. symfony           C. Zend
    D. Django             E. CakePHP           F. ThinkPHP

42. 网络管理具备以下几大功能：配置管理、（   ）、性能管理、安全管理和计费管理等。

    A. 故障管理    B. 日常备份管理   C. 升级管理    D. 发送邮件

43. 关于代理服务器的论述，正确的是 （   ） 。

    A. 使用 Internet 上已有的公开代理服务器，只需配置客户端。
    B. 代理服务器只能代理客户端http 的请求。
    C. 设置好的代理服务器可以被网络上任何主机使用。
    D. 使用代理服务器的客户端没有自己的ip 地址。

44. 在下列的名称中，不属于DNS 服务器类型的是：（   ）

    A. Primary Master Server
    B. Secondary Master Server
    C. root and  hint
    D. Cache_only Server

45. DHCP 是动态主机配置协议的简称，其作用是可以使网络管理员通过一台服务器来管理一个网络系统，
    自动地为一个网络中的主机分配 （   ） 地址。
	
    A. 网络         B. MAC       C. TCP       D. IP	

46. 关于DNS 服务器，叙述正确的是 （   ）。

    A. DNS 服务器配置不需要配置客户端
    B. 建立某个分区的DNS 服务器时只需要建立一个主DNS 服务器
    C. 主DNS 服务器需要启动 named 守护进程，而辅DNS 服务器不需要
    D. DNS 服务器的 /var/named/named.ca 文件包含了根名字服务器的有关信息	

47. 下面的 Apache 配置用于 （   ）

    <FilesMatch \.php$> 
        SetHandler application/x-httpd-php
    </FilesMatch>

    AddType text/html .php
    DirectoryIndex index.php

    A. 使Apache以其模块方式支持PHP脚本语言
    B. 使Apache以CGI方式支持PHP脚本语言
    C. 使Apache以Fast-CGI方式支持PHP脚本语言
    D. 以上均不对

48. Tomcat 的主配置文件为： （   ）

    A. server.conf     B. server.xml    C. web.xml    D. context.xml

49. 下面哪个命令可以重新加载 postfix 的配置文件。 （   ）

    A. postfix reload                   B. postconf reload
	C. doveadm reload                   D. doveconf reload

50. 下面哪个命令可用于为Linux客户释放IP参数。 （   ）

    A. ipconfig /release
    B. ipconfig /renew
    C. dhclient -r 
    D. dhclient 
    E. ifconfig -r

51. 下面哪个命令用于生成 vsftpd 虚拟用户的口令数据库文件 （   ）

    A. pure-pw      B. db_load      C. pdbedit      D. postmap

52. 下面的描述错误的是 （   ）

    A. 在 Vsftpd 中，ssl_enable=YES 用于开启 SSL 的连接支持
    B. 在 Apache 中，SSLEngine on 用于启用 SSL 引擎支持
    C. 在 Postfix 中，smtpd_tls_wrappermode=yes 用于开启 SMTPS 协议支持
    D. 在 Postfix 中，smtpd_tls_security_level=may 用于向远程 SMTP 客户端宣布 STARTTLS 支持，
	   并要求客户端必须使用TLS加密连接
    E. 在 Dovecot 中，ssl=yes 用于开启 SSL 的连接支持

53. 在 vsftpd 中，将所有本地用户都被限制在其主目录下，没有任何例外的配置是 （   ）

    A. chroot_local_user=YES
       chroot_list_enable=YES
       chroot_list_file=/etc/vsftpd/chroot_list
    B. chroot_local_user=NO
       chroot_list_enable=YES
       chroot_list_file=/etc/vsftpd/chroot_list
    C. chroot_local_user=YES
       chroot_list_enable=NO
       chroot_list_file=/etc/vsftpd/chroot_list
    D. chroot_local_user=NO
       chroot_list_enable=NO
       chroot_list_file=/etc/vsftpd/chroot_list

54. 在 vsftpd 中，只有列在/etc/vsftpd/chroot_list中的用户被限制在其主目录下的配置是 （   ）

    A. chroot_local_user=YES
       chroot_list_enable=YES
       chroot_list_file=/etc/vsftpd/chroot_list
    B. chroot_local_user=NO
       chroot_list_enable=YES
       chroot_list_file=/etc/vsftpd/chroot_list
    C. chroot_local_user=YES
       chroot_list_enable=NO
       chroot_list_file=/etc/vsftpd/chroot_list
    D. chroot_local_user=NO
       chroot_list_enable=NO
       chroot_list_file=/etc/vsftpd/chroot_list

55. 在 vsftpd 中，只有列在/etc/vsftpd/user_list中的用户可以访问当前vsftpd服务器的配置是 （   ）

    A. userlist_enable=YES
       userlist_deny=YES
       userlist_file=/etc/vsftpd/user_list
    B. userlist_enable=YES
       userlist_deny= NO
       userlist_file=/etc/vsftpd/user_list
    C. userlist_enable=NO
       userlist_deny=YES
       userlist_file=/etc/vsftpd/user_list
    D. userlist_enable=NO
       userlist_deny= NO
       userlist_file=/etc/vsftpd/user_list

56. 在 vsftpd 中，限制最大连接数的配置语句是 （   ）

    A. local_max_rate          B. anon_max_rate
    C. max_per_ip              D. max_clients

57. 在 vsftpd 中，仅为不同的本地用户实施不同配置的语句是 （   ）

    A. local_enable=YES
       guest_enable=NO
       user_config_dir=/etc/vsftpd/userconf
    B. local_enable=NO
       guest_enable=YES
       user_config_dir=/etc/vsftpd/userconf
    C. local_enable=YES
       guest_enable=YES
       user_config_dir=/etc/vsftpd/vuserconf
    D. local_enable=NO
       guest_enable=YES
       user_config_dir=/etc/vsftpd/vuserconf

58. 在 vsftpd 中，对所有非匿名用户登录都强制使用SSL安全连接发送用户口令，而无需对数据传输进行加密的配置是 （   ）

    A. ssl_enable=YES
       force_anon_logins_ssl=YES
       force_anon_data_ssl=YES
    B. ssl_enable=YES
       force_anon_logins_ssl=YES
       force_anon_data_ssl=NO
    C. ssl_enable=YES
       force_anon_logins_ssl=NO
       force_anon_data_ssl=YES
    D. ssl_enable=YES
       force_local_logins_ssl=YES
       force_local_data_ssl=YES
    E. ssl_enable=YES
       force_local_logins_ssl=NO
       force_local_data_ssl=YES
    F. ssl_enable=YES
       force_local_logins_ssl=YES
       force_local_data_ssl=NO

59. 当远程用于以root用户访问本地的/data NFS共享时仍具有root	权限，则本地/etc/exports文件的配置为 （   ）

    A. /data   192.168.1.0/24(rw,root_squash)
    B. /data   192.168.1.0/24(rw,no_root_squash)
    C. /data   192.168.1.0/24(rw,all_squash)
    D. /data   192.168.1.0/24(rw,no_all_squash)

60. 为了查看NFS服务器上哪些共享目录已经被客户端挂载，应使用命令 （   ）

    A. showmount -a 192.168.0.251
    B. showmount -e 192.168.0.251
    C. showmount -d 192.168.0.251
    D. showmount -v 192.168.0.251
    E. smbclient -L 192.168.0.251

61. 用于删除名为 jason 的 Samba 用户账号的命令是 （   ）

    A. smbpasswd -a jason
    B. smbpasswd -d jason
    C. smbpasswd -e jason
    D. smbpasswd -x jason

62. Samba服务器的文件系统上 /var/lib/mldonkey 及其子目录的属主和组均为 mldonkey。
    若希望所有具有Samba账号的用户均可读取 [MLdonkey] 共享中的文件和目录，
	而只有名为 osmond 的Samba用户可以修改 [MLdonkey] 共享中的文件名、创建子目录、移动文件到子目录。
	则下面的Samba共享配置正确的是 （   ）

    A. [MLdonkey]
            comment = MLdonkey
            path = /var/lib/mldonkey/incoming
            writable = yes
    
    B. [MLdonkey]
            comment = MLdonkey
            path = /var/lib/mldonkey/incoming
            writable = yes
            valid users = mldonkey
    
    C. [MLdonkey]
            comment = MLdonkey
            path = /var/lib/mldonkey/incoming
            writable = yes
            guest ok = yes
            guest account = mldonkey
    
    D. [MLdonkey]
            comment = MLdonkey
            path = /var/lib/mldonkey/incoming
            writable = yes
            guest ok = yes
    		guest only = yes
            guest account = osmond
    
    E. [MLdonkey]
            comment = MLdonkey
            path = /var/lib/mldonkey/incoming
            writable = yes
            force group = mldonkey
            force user = mldonkey
            admin users = osmond

63. 下面关于 Apache 2.4 的配置描述错误的是 （   ）

    A. 当KeepAlive为on时，MaxKeepAliveRequests 200 用于限制每次连接可处理的最大请求数目为200
    B. DefaultType text/plain 用于设置服务器对于不认识的文件类型的默认类型为纯文本
    C. UserDir public_html 用于设定用户放置网页的目录为 $HOME/public_html
    D. Port 1080 用于将 Apache 服务器的端口号设置为 1080
    E. DocumentRoot /home/htdocs 用于设定 Apache 服务器的网页根目录为 /home/htdocs

64. 对于下面的Apache配置片段，描述错误的选项是  （   ）

    Alias /inside    /home/www/inside/
    <Directory /home/www/inside>
        Options Indexes FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 192.168.1.5
    </Directory>
    
    A. 对 /inside 的访问将映射到文件系统中的/home/www/inside目录 
    B. 若 /home/www/inside 目录中没有 index.html 文件将显示目录列表
    C. 若 /home/www/inside 目录及子目录中存在符号链接文件则跟随符号链接
    D. 不读取 /home/www/inside 目录及子目录中的基于目录的配置文件 .htaccess
    E. 只允许IP 地址为 192.168.1.5 的主机访问
    F. 拒绝所有主机访问（包括IP 地址为 192.168.1.5 的主机）

65. 用于清除域名服务器缓存中内容的命令是 （   ）

    A. rndc status         B. rndc stats        C. rndc dumpdb
    D. rndc stop           E. rndc flush        F. rndc clear

66. 下面用于为基于SSL的 Apache 指定SSL证书和私钥文件的配置语句是 （   ）

    A. SSLCertificateFile		/etc/pki/tls/certs/olabs.net.crt
       SSLCertificateKeyFile	/etc/pki/tls/private/olabs.net.key
    B. rsa_cert_file=/etc/pki/tls/certs/olabs.net.crt
       rsa_private_key_file=/etc/pki/tls/private/olabs.net.key
    C. smtpd_tls_cert_file = /etc/pki/tls/certs/olabs.net.crt
       smtpd_tls_key_file = /etc/pki/tls/private/olabs.net.key
    D. ssl_cert = </etc/pki/tls/certs/olabs.net.crt
       ssl_key = </etc/pki/tls/private/olabs.net.key

67. 下面哪个是PHP的FastCGI进程管理器 （   ）

    A. php-cli       B. php-cgi       C. php-fpm       D. mod_php

68. 下面哪个PHP模块提供了对IMAP协议支持 （   ）

    A. php-imap      B. php-ldap      C. php-snmp    D. php-xmlrpc

69. 下面哪个是 Ruby 语言的模块管理工具  （   ）

    A. pear         B. gem         C. pip         D. pecl       E. cpan

70. 下面哪个PHP模块提供了对MySQL数据库的支持  （   ）

    A. php-pdo              B. php-mysql            C. php-pgsql
    D. php-pecl-apcu        E. php-pecl-redis       F. php-pecl-memcached

71. 下面哪个软件不能用于 Web 日志分析统计 （   ）

    A. AWStats       B. Piwik       C. LogAnalyzer      D. Webalizer

72. 下面哪个软件可以实现 MTA 的功能 （   ）

    A. Dovecot       B. Cyrus-IMAP      C. COURIER-IMAP      D. Postfix

73. 下面哪个是 Postfix 的邮件队列管理器 （   ）

    A. Incoming               B. qmgr                C. Active
	D. Deferred               E. Corrupt             F. Hold

74. 为入站邮件改写地址，同时负责出站邮件的路由抉择的 Postfix 组件是 （   ）

    A. pickup                 B. smtpd                  C. smtp
	D. cleanup                E. trivial-rewrite        F. local

75. 下面关于 Postfix 运行机制描述错误的是 （   ）

    A. Postfix 的主服务守护进程主导邮件的处理流程，同时是Postfix其他组件的总管
    B. Postfix 的主控进程和组件进程均以常驻内存的运行方式运行
    C. Postfix 的组件之间是通过UNIX的Socket或受保护的目录之下的先入先出命名管道（FIFO）进行通信
	D. Postfix 的主服务守护进程是以root身份运行的，而各组件是以postfix用户身份运行的
    E. Postfix 可以很容易地配置各个组件运行于 chroot 环境

76. 下面哪个命令可以显示支持的SASL服务插件类型  （   ）

    A. postconf -l             B. postconf -m            C. postconf -a
    D. postconf -A             E. postconf -df           F. postconf -nf

77. 下面关于 Postfix 的描述错误的是 （   ）

    A. 默认可以转发客户IP地址能匹配 $mynetworks 的发往任意目标地址的邮件
    B. 默认可以转发目标地址域能匹配 $relay_domains 所指定的域及其子域的邮件
    C. 可以使用 access 映射表实现中继控制
    D. 可以使用基于 SASL 的 SMTP 认证机制实现用户级别的邮件中继控制
    E. 通过修改/etc/postfix/main.cf文件，可以配置基于 SMTPS 协议（465/tcp）的服务

78. Postfix中，用于限制可以向Postfix发起SMTP连接的客户端的主机名或IP地址的配置是 （   ）

    A. smtpd_client_restrictions
    B. smtpd_helo_restrictions
    C. smtpd_sender_restrictions
    D. smtpd_recipient_restrictions

79. 用于处理所有认证的 Dovecot 组件是 （   ）

    A. imap-login/pop3-login      B. log              C. auth
	D. imap/pop3                  E. config           F. anvil

80. 显示Dovecot配置中所有修改了默认值的参数以及明确设置了默认值的参数，可以使用命令 （   ）

	A. doveconf -d                  B. doveconf -a
    C. doveconf -n                  D. doveconf -N
	
```

## 三、多选题

```

1. 下列哪些参数可以用于 Apache 服务器的配置文件httpd.conf中？（     ）

    A. ServerType 
    B. NameVirtualHost  
    C. Forwarders 
    D. DocumentRoot
    E. Port 
    F. Email

2. 在Linux系统中，下列哪些文件与名称解析无关？ （     ）

    A. /etc/host.conf
    B. /etc/resolv.conf
    C. /etc/hosts
    D. /etc/nsswitch.conf
    E. /etc/hosts.allow
    F. /etc/hosts.deny

3. Apche服务器可以使用哪些方法建立虚拟站点 （     ）

    A. 使用多个IP地址   
    B. 使用不同的端口    
    C. 启动多个Apche服务器  
    D. 使用不同的域名

4. 在 Apache 2.4 中，提供多进程多线程混合模型的运行机制是	（     ）
	
	A. Profork	     B. Worker        C. Event        D. httpd-itk

5. 在 Apache 正在运行时，执行了命令
    # mv access_log access_log.bak
	# touch access_log
    执行后，下面的叙述正确的是 （      ）

    A. 后续访问日志会写入 access_log
	B. 后续访问日志会写入 access_log.bak
	C. 默认地，Apache 启动时会将访问日志写入 access_log 文件
	D. 在 Apache 启动时，会记录访问日志 access_log 的文件描述符（fd），
	   运行时会将访问日志将写入 fd 指定的文件，fd 会指向 access_log 文件的 inode
	E. 使用 mv 命令改名后，access_log.bak 的 inode 与原来 access_log 的 inode 一致
    F. 重启 Apache 服务后，按照默认配置访问日志会写入 access_log，若其不存在则创建之

6. 在 CentOS 中，为了避免泄露 Apache 服务信息，下面的选项正确的是 （      ）

    A. 使用命令 sed -i 's/^/#/g' /etc/httpd/conf.d/welcome.conf 避免显示测试页面
	B. 在 Apache 的主配置文件中设置 ServerTokens Prod 避免在HTTP响应头中显示 Apache 的版本号和操作系统信息
	C. 在 Apache 的主配置文件中设置 ServerSignature Off 避免在错误页面中显示 Apache 的版本号
	D. 在 PHP 的住配置文件中设置 expose_php = Off 避免在HTTP响应头中显示 PHP 的版本号

7. 在 CentOS 中，要使用vsftpd配置一个支持续传的匿名站点，需要如下那些指令？（      ）

    A. write_enable=YES
    B. anon_upload_enable=YES
    C. anon_mkdir_write_enable=YES
    D. anon_other_write_enable=YES
    E. anon_world_readable_only=NO

8. 在 BIND 的 named.conf 配置文件中用于设置DNS转发的指令有：（      ）

    A. relay       B. forward       C. forwarders       D. forwarding

9．下面哪些是权威性DNS服务器  （      ）

    A. 主域名服务器（Primary Name Server）
    B. 辅域名服务器（Secondary Name Server）
    C. 残根域名服务器（Stub Name Server）
    D. 惟高速缓存服务器（Caching-only Server）
    E. 转发服务器（Forwarding Server）

10. 在Linux环境下，下列叙述正确的是：（      ）

    A. 文件/etc/portlist包含了各种不同的服务及其端口号的列表
    B. 可以用ipconfig命令列出当前系统中的所有网络接口信息
    C. Samba服务的两个守护进程的名称是 samba 和 netbios
    D. /etc/exports 是NFS的共享配置文件
	E. 使用命令 mysqldump -u root -p test > test.sql 可以备份MySQL的名为test的数据库
    F. 使用命令 mysql -u root -p test < test.sql 可以恢复已备份的名为test的数据库

11. 下列关于DNS轮询描述正确的是： （      ）

    A. 定义多个主机域名指向同一个IP地址。
    B. 定义同一个主机域名指向多个IP地址。
    C. 定义多个别名指向同一个主机域名。
    D. 可实现简单的负载均衡。

12. Apache服务器的httpd.conf配置文件中用于定义用户认证的指令有：（      ）

    A. AuthName               B. AuthType            C. Require
    D. AuthUserFile           E. Deny                F. Allow

13. Apache服务器的httpd.conf配置文件中用于定义主机访问控制的指令有：（      ）

    A. Order      B. Access      C. Deny      D. Allow     E. Require

14. 对于 CentOS 提供的 vsftpd 默认设置来说，下列正确的是？ (      ) 

    A. 允许匿名用户和本地用户登录
    B. 匿名用户不能离开匿名服务器目录/var/ftp，且能进行上传和下载
    C. 本地用户可以离开自家目录切换至有权访问的其他目录，并在权限允许的情况下进行上传和下载
    D. 本地用户的登录名为本地用户名，口令为此本地用户的口令
    E. 只有写在文件/etc/vsftpd.ftpusers中的本地用户才能登录

15. 可以通过哪些服务传输文件   （        ）

    A. nfs    B. ftp    C. scp/sftp     D. rsync     E. samba     F. http

16. 下面关于 Apache 中 .htacces 文件及其作用域描述正确的是（       ）。

    A. Apache 可以使用分布在整个网站目录树中的特殊文件来进行分散配置，这样的特殊配置文件称为基于目录的配置文件。 
    B. 基于目录的配置文件通常叫 .htaccess ，但是也可以用 AccessFileName 指令来改变它的名字。 
    C. 基于目录的配置文件 （.htaccess 文件）中指令的作用域是存放它的那个目录及其所有子目录。 
    D. .htaccess 文件的语法与主配置文件相同。
    E. 放在 <Directory> 容器中的指令几乎都可以出现在 .htaccess 文件中，具体能出现哪些指令
       由主配置文件中的 AllowOverride 指令来决定。

17. 用户接收邮件所使用的协议是？ （       ）

    A. imap         B. smtp          C. pop3        D. snmp

18. 下面哪些软件可以实现基于反向代理的负载均衡。（       ）

    A. Nginx        B. Apache       C. Squid        D. Haproxy      E. Vanish

19. 下面哪些不是基于 PHP/Perl/Python/Ruby 的编程框架  （      ）

    A. Django         B. Meteor           C. symfony          D. Grok
    E. Flask          F. AngularJS        G. Catalyst         H. RubyonRails

20. 在Linux下，下面关于挂载 Windows 系统共享目录的命令描述错误的是。（      ）

    # mount.cifs //192.168.1.1/share /mnt/win -o user=lrj

	A. 将 Windows系统（IP为192.168.1.1）上的名为share的共享挂载到本地 /mnt/win 目录
	B. 执行命令前必须保证Linux系统上有同名的lrj用户存在
	C. 命令执行时，应该输入 192.168.1.1 上名为 lrj 用户的口令
    D. 命令执行时，应该输入本地 lrj 用户的口令
	E. 在 mount.cifs 命令行上可以使用 -o guest 替换 -o user=lrj 实现以guest用户挂载
    F. 使用命令 umount -t cifs /mnt/win 或 umount.cifs /mnt/win 可以卸载已挂载的共享

21. 下面哪些软件可用于键值缓存系统 （       ）

    A. MySQL           B. MariaDB           C. Memcached           D. Redis

22. 下面哪些是使用 Ruby 语言开发的基于仓库管理的协同开发平台   （       ）

    A. Indefero     B. Gitlab      C. Trac       D. Gforge       E. Redmine

23. 下面哪些是 Python 语言的模块管理工具  （         ）

    A. pear              B. gem             C. pip             D. brew
    E. easy_install      F. cpan            G. choco           H. apt
	I. npm               J. yum             K. yarn            L. composer

24. 下面哪些是 CGI 技术的优点 （      ）

    A. CGI不依赖于任何特定的服务器体系结构（类 UNIX/Windows；单线程/多线程，等等）
    B. CGI已经在几乎所有的Web服务器上实现（如：Apache、IIS等）
    C. 不同的CGI请求无法共享内存或其他上下文信息
    D. 服务器上大量的CGI并发进程的初始化所用的时间成为网站性能的瓶颈
    E. CGI 程序可以用任何一种语言编写，只要这种语言具有标准输入、标准输出和环境变量支持
	F. CGI程序运行在独立的进程中，CGI程序的错误不会导致Web服务器崩溃

25. 下面哪些是邮件投递代理（Mail Delivery Agent，MDA）软件  （       ）

    A. procmail       B. maildrop      C. fetchmail      D. Sieve      E. getmail

```

## 四、搭配题

```
1、将服务软件与其监听的默认端口联系起来

    (   ) 01. tomcat                    A.  22
    (   ) 02. bind                      B.  53
    (   ) 03. Apache                    C.  80,443
    (   ) 04. mysql                     D.  3128
    (   ) 05. memcached                 E.  21
    (   ) 06. rsync                     F.  3306
    (   ) 07. OpenSSH                   G.  873
    (   ) 08. postfix                   H.  25
    (   ) 09. dovecot                   I.  110,143
    (   ) 10. redis                     J.  8080
    (   ) 11. squid                     K.  11211
    (   ) 12. vsftpd                    L.  6379

2、将功能相同的 Apache 2.2 和 2.4 的主机访问控制配置联系起来

    (   )  1.  Order deny,allow              A.  Require all granted
               Deny from all

    (   )  2.  Order allow,deny              B.  Require all denied
               Allow from all

    (   )  3.  Order deny,allow              C.  <RequireAll>
               Deny from All                         Require all granted
               Allow from 127.0.0.1                  Require not ip 192.168.0.1
               Allow from ::1                    </RequireAll>

    (   )  4.  Order allow,deny              D.  Require ip 192.168.0
               Deny from all
               Allow from example.org

    (   )  5.  Order allow,deny              E.  Require host example.org
               Deny from all
               Allow from 192.168.0

    (   )  6.  Order Deny,Allow              F.  Require local
               Deny from 192.168.0.1               
                                          
 3、请将下面的 Postfix进程组件与其功能联系起来                                     

  (   ) 01. qmgr              A. 从maildrop邮件队列（存储由postdrop提交的邮件）中取得邮件，
                                 并将邮件传递给cleanup。
  (   ) 02. pipe              B. 从网络中获取邮件，并将邮件传递给cleanup。
  (   ) 03. pickup            C. 使用兼容于Qmail的QMQP协议从网络中获取邮件，并将邮件传递给cleanup。
  (   ) 04. local             D. 处理入站邮件，为其补足遗漏的信息头字段之后放入incoming邮件队列，并通知qmgr。
  (   ) 05. smtp	          E. 根据canonical和virtual映射表（如果存在）为入站邮件改写地址，
	                             同时负责出站邮件的路由抉择。
  (   ) 06. smtpd             F. 邮件队列管理器，负责将active邮件队列中的邮件分发给适合的MDA处理，
	                             路由决策委托给trivial-rewrite处理。
  (   ) 07. cleanup           G. LDA。根据别名表和 ~/.forward文件处理邮件。若邮件是被转发给另一个地址，
	                             则传给cleanup重新处理，否则将邮件保存在用户的邮箱中。
  (   ) 08. lmtp              H. 使用LMTP协议投递邮件。主要用于将邮件交给特殊的POP/IMAP服务器，
	                             以便使用特殊的邮箱格式来存储邮件。
  (   ) 09. qmqpd             I. 负责通过SMTP协议把邮件投递到远程主机，及Postfix的smtp客户程序。
  (   ) 10. virtual	          J. 负责将邮件投递到“虚拟邮箱”，也就是和本地的Linux账号没有关系的邮箱
  (   ) 11. master            K. 通过外部程序投递邮件。经常被用来将邮件传给外部的内容过滤程序
  (   ) 12. trivial-rewrite   L. Postfix 的主控守护进程，是其他组件的总管

4、请将软类型与知名软件联系起来

  (   ) 01. CMS                          A. MediaWiki、MoinMoin、Dokuwiki
  (   ) 02. Webmail                      B. Wordpress、Dotclear
  (   ) 03. LMS                          C. Joomla、Drupal
  (   ) 04. Static Site Generator        D. phpBB、SMF、Discuz!
  (   ) 05. BLOG                         E. Moodle、Oppia
  (   ) 06. DBadmin                      F. Zimbra、eGroupWare
  (   ) 07. Wiki                         G. Chive、phpMyAdmin、phpPgAdmin
  (   ) 08. Forum                        H. RoundCube、RainLoop、SquirrelMail
  (   ) 09. Document Generator           I. Jekyll、hyde、Hexo
  (   ) 10. Groupware                    J. Sphinx、AsciiDoc、MkDocs

```

## 五、简答题


1、FTP 协议有两种工作模式，说说它们的大概的一个工作流程？


2、简述 vsftpd 的三类用户及其特点。 


3、简述 Linux 环境下 Apache 2.4 的三种 MPM 工作模式，以及它们之间的区别。


4、简述DNS查询模式


5、当用户在浏览器当中输入一个网g 站，说说计算机对dns 解释经过那些流程？
   注：本机跟本地dns 还没有缓存。