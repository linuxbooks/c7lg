# 阶段测验 1


## 一、判断题

```
1. linux 内核 1.0 的发布时间为 1994 年。( )

2. Linux 支持几乎所有的网络协议，所以人们通常用它来作为服务器使用。( )

3. 只有GPL协议是自由软件协议。( )

4. Linux 兼容于 SYSV和BSD UNIX，并且符合 POSIX 标准。( )

5. Linux 支持多种文件系统在文件级别上的互操作；不同种类的文件系统上的可执行文件是不能兼容执行的。( )

6. 普通用户可以使用 logout 或 exit 关机；超级用户可以使用 shutdown 或 halt 关机。( )

7. 不经用户同意，超级用户root 在操作系统中无权改变其他用户的登录口令。( )

8. 命令 wc abc.txt 和 wc <abc.txt，无论输出结果还是运行机制均相同。( )

9. 普通用户的Shell提示符是 #；超级用户的Shell提示符是 $ 。( )

10. Linux 的内核是计算机硬件的首次扩充，它实现了操作系统的基本功能。( )
```

## 二、单选题

```
1. Linux 属于（  ）软件。

    A. 自由	      B. 共享		C. 支撑		 D. 数据库

2. Linux的标志图案是（   ）。

    A. 大象       B. 海豚       C. 骆驼      D. 企鹅

3. 你的公司需要建立一个内部的小型局域网，在有限的财政预算且遵循商业版权的情况下，应该选用哪种网络操作系统：（   ）

    A. HP-UX         B. Solaris        C. Windows 2012 Server
    D. Linux         E. Netware        F. IBM AIX

4. 下面叙述错误的是：（   ）

    A. Linux支持几乎所有的网络协议，所以人们经常用它来作为服务器使用。
    B. Linux只能作为网络服务器的操作系统使用，而不能作为客户机的操作系统使用。
    C. Linux兼容于SYSV和BSD UNIX,并且符合POSIX标准。
    D. Linux操作系统是于1991年4月，是由芬兰人Linus Torralds独立草创的。
    E. Linux的内核一直由Linus Torralds维护着。

5. 下面说法错误的是：（   ）

    A. 自由软件不能用于商用。
    B. 两个传统公认的UNIX标准版本是 System VUNIX 和 BSD UNIX。
    C. Richard M. Stallman 是自由软件的创始人，是 GNU Project 和 FSF 的创始人。
    D. Linux 操作系统可以说是UNIX操作系统的一个克隆体，它最初由芬兰赫尔辛基大学的 Linus Torvalds 创建。

6. 绝大多数的 Linux 默认的 Shell 是：（   ）

    A. Bourne-again Shell
    B. Korn Shell
    C. Command.exe
    D. Gnome
    E. KDE 

7. 下列说法错误的是： （   ）

    A. Firefox 和 Thunderbird 有 Windows 和 Linux 两种版本分别用于两种平台。 
    B. Linux 下没有 BT 下载工具可用。 
    C. 可以使用 VNC、Webmin、SSH 实现对远程 Linux 系统的管理。 
    D. 在 Linux 桌面环境下可以使用 GAIM 实现即时通讯。 

8. 下面关于虚拟内存的叙述错误的是：（   ）

    A. 它允许同时运行更多的程序
    B. 它是 RAM 和交换空间的组合
    C. 它使用换页技术将程序和数据段换入和换出RAM
    D. 它使程序运行更快

9. 在Linux环境下，用ps -ef命令显示进程。进程A的PID为234，PPID为223。进程B的PID为241，PPID为234。
   可以从中得出什么结论？（   ）

    A. 进程A是进程B的父进程
    B. 进程A是孤儿进程，进程B是僵死进程
    C. 进程B是一个守护进程，进程A是一个特殊程序
    D. 进程B是进程A的父进程

10. 执行以下的命令后的显示结果为：（   ）

    $ mkdir temp; cd temp
    $ var=CentOS
    $ touch myfile
    $ echo "$var `ls` $(ls)"

    A.  $var `ls` $(ls)
    B.  CentOS myfile myfile
    C.  CentOS `ls` myfile
    D.  $var myfile myfile 

11. 在Linux环境下，执行以下的命令后的显示结果为：（   ）

    $ mkdir temp; cd temp
    $ var=ls
    $ touch myfile
    $ echo \$var $var \$\(ls\) ${var} $(ls)

    A.  $var ls $(ls) ls myfile
    B.  ls ls myfile ls myfile
    C.  ls ls ls ls myfile
    D.  $var myfile myfile ls myfile  

12. 在Vi中，将从当前位置开始到文件尾的内容另存为文件file的命令为: （   ）

    A. :w file 
    B. :.,$w file
    C. :1,.w file 
    D. :f file

13. 在Vi中，能删除从当前行开始的3行的命令为（   ）。

    A. 3dd    B. dd3    C. 3xx    D. xx3

14. 在Linux环境下，要添加一个环境变量且对所有用户生效，应该修改哪个文件? （   ）

    A. /etc/sysconfig/profile
    B. /etc/sysconfig/profile 
    C. /etc/bashrc
    D. /etc/profile
    E. /etc/env

15. 命令: cat > test，从何处获得标准输入? （   ）

    A. 文件 test
    B. 键盘 
    C. 标准错误输出 
    D. 终端屏幕

16. 要删除abc目录及其全部内容的命令为： （   ）

    A. rm abc       B. rm -r abc       C. rmdir abc       D. rmdir -r abc

17. 在使用mkdir命令创建新的目录时，在其父目录不存在时先创建父目录的选项是：（   ）

    A -m        B -d          C -f         D -p

18. 下面关于i节点描述错误的是？ （   ）

    A.  i节点和文件是一一对应的
    B.  i节点能描述文件占用的块数
    C.  i节点描述了文件大小和指向数据块的指针
    D.  通过i节点实现文件的逻辑结构和物理结构的转换

19. 下列关于链接描述，错误的是：（   ）

    A. 硬链接就是让链接文件的i节点号指向被链接文件的i节点
    B. 硬链接和符号连接都是产生一个新的i节点
    C. 链接分为硬链接和符号链接
    D. 硬连接不能链接目录文件

20. 对名为fido的文件用chmod 551 fido 进行了修改，则它的权限字符串是：（   ）

    A. -rwxr-xr-x    B. -rwxr--r--     C. -r--r--r--      D. -r-xr-x--x

21. 一个文件名字为rr.gz，可以用来解压缩的命令是： （   ）

    A. tar       B. gzip      C. xz      D. uncompress

22. 要使用一个文件的内容作为一个Linux命令的输入，则该命令必须（   ）。

    A. 使用过滤程序
    B. 对文件中的数据进行格式化 
    C. 使用输出重定向 
    D. 能读取标准输入

23. 具有很多C语言的功能，又称过滤器的应用程序是？（   ）

    A. csh        B. tcsh        C. awk       D. sed

24. 下列Linux命令中，哪个命令与网络无关。（   ）

    A. ping         B. route        C. netstat         D. chmod

25. Linux系统中具有最高权限的用户名是：（   ）

    A. administrator    B. root      C. supervisor     D. admin

26. 当一个普通用户执行ls -l命令时，应该显示哪些内容？ （   ）

    A. 隐含目录和文件 
    B. 当前目录的父目录
    C. 用户家目录下的所有文件 
    D. 有权访问的当前目录下的文件

27. 下面哪个命令可以显示文件 /etc/motd 的磁盘块占用数？（   ）

    A. du /etc/motd             B. df /etc/motd 
    C. ls -l /etc/motd          D. ls -al /etc/motd

28. 用于挂起程序执行的操作是： （   ）

    A. <Ctrl>+D        B. <Ctrl>+C      C. <Ctrl>+Z      D. <Ctrl>+]

29. 终止一个前台进程可能用到的命令或操作。（   ）

    A. kill     B. <CTRL>+<C>     C. shutdown     D. halt

30. 让程序在服务器后台执行cmd命令，即使注销登录，程序也能继续执行的命令是：（   ）

    A. nohup cmd &        B. cmd &       C. nohup cmd      D. cmd

31. 假设当前目录下没有文件aaa和文件bbb，执行下列命令后aaa和bbb的权限为：（   ）

    $ umask 022
    $ touch aaa
    $ umask 077 
    $ touch bbb

    A. 文件aaa的权限为755，文件bbb的权限为700
    B. 文件aaa的权限为644，文件bbb的权限为600
    C. 文件aaa的权限为755，文件bbb的权限为700
    D. 文件aaa的权限为755，文件bbb的权限为644

32. 下面关于用户管理的叙述中错误的是：（   ）

    A. CentOS下有标准组和私有组之分
    B. 默认情况下，在添加新用户的同时会创建与用户同名的私有组
    C. 用户管理的目的是帮助系统管理员对使用系统的用户进行跟踪，并控制用户对系统资源的访问 
    D. 账号系统文件包括/etc/passwd 、/etd/shadow 和/etc/group、/etc/gshadow
    E. 文件/etc/passwd和文件/etc/shadow对任何人都具有读权限

33. 命令 grep -c "^$" 将显示:  （   ）

    A. 空行数 
    B. 包含$字符的行数 
    C. 最后一个字符是$的行数 
    D. 第一个字符是$的行数 

34. 要想将用户自己更改的环境变量在以后登录时起作用，应该将其添加到：（   ）

    A. ~/.bashrc
    B. ~/.bash_profile
    C. ~/.bash_history
    D. /etc/bashrc

35. 大多数Linux命令所使用的强制执行参数为（   ）。

    A. -f         B. -R      C. -r        D. -i

36. 文件标志b表示（   ）。

    A. 字符设备文件     B. 目录文件     C. 块设备文件    D. 套接字

37. 下面为用户 bill 发信的命令是？（   ）

    A. mail bill 
    B. mail < bill 
    C. mail > bill 
    D. mail -u bill 

38. 下面哪个是标准串口设备：（   ）

    A. /dev/ttyS1    B. /dev/lp1    C. /dev/tty1     D. /dev/ttys1

39. 下面哪条命令用于返回上一次使用cd命令进入的目录？（   ）

    A. cd `pwd`    B. cd /    C. cd -    D. cd ..

40. 对所有用户增加对文件test的读权限所使用的命令为（   ）。
    
    A. chmod ar+ test
    B. chmod a+r test
    C. chmod +ar test
    D. chmod r+ test

41.管道符是（   ）。

    A. <          B. |        C. >>        D. >

42. cmd1&&cmd2||cmd3 的含义是（   ）。

    A. 当cmd1执行成功，cmd2执行失败时才执行cmd3
    B. 当cmd1，cmd2执行成功时才执行cmd3
    C. 当cmd1，cmd2执行失败时才执行cmd3
    D. 当cmd1执行失败，cmd2执行成功时才执行cmd3

43. 在哪个目录中包含 mail spools、print spools和log文件。 （   ）

    A.  /etc       B. /bin      C.  /var      D.  /opt 

44. Linux文件系统的文件都按其作用分门别类地放在相关的目录中，对于外部设备文件，一般应将其放在（   ）目录中。

    A. /bin        B. /etc      C. /dev       D. /lib

45. 下面哪条命令可以显示文本文件的最后20行。（   ）

    A. end -n 20 filename 
    B. last -n 20 filename 
    C. head -20 filename 
    D. tail -n 20 filename 

46. 在Vi的编辑模式下，从当前光标开始向文件尾端查找字符串ABC命令为（   ）。

    A. ?ABC         B. /ABC/      C. /ABC       D. ?ABC?

47. 用于实现下述功能的命令是（   ）。
    将列表显示结果存入文件temp；同时对列表显示结果进行字数统计，并将字数统计结果追加到文件temp。

    A. ls |tee temp |wc –w
    B. ls > temp
    C. ls |tee temp |wc –w >>temp
    D. ls |tee /dev/tty1 |wc –w

48. 下列提高工作效率的功能中，哪个不是的bash的功能？ （   ）

    A. 自动命令行补齐         B. 使用鼠标复制和粘贴   
    C. 别名                   D. 命令历史

49. 下列对shell变量FRUIT操作，正确的是：（   ）

    A. 为变量赋值：$FRUIT=apple           B. 显示变量的值：fruit=apple
    C. 显示变量的值：echo $FRUIT          D. 判断变量是否有值：[ -f “$FRUIT” ]

50. 下列哪个目录中的内容被复制到新建用户的主目录下？ （   ）

    A．/home/$USER 
    B．/var/log/users 
    C. /etc/skel 
	D. /etc/profile

51. 下面哪条命令用于查看登录用户的默认值： （   ）

    A．useradd -D
    B．useradd -g
    C. useradd -default
	D. skel -d

52. 用于显示后台作业和被挂起的进程状态的命令是：（   ）

    A. jobs         B. ps        C. at        D. bg          E. fg

53. 下面哪个是空设备：（   ）

    A. /dev/ram1    B. /dev/loop0    C. /dev/null    D. /dev/zero

54. 下面哪种 VMWare 产品可用于在 Windows 桌面环境下安装并运行 Linux 虚拟机。（   ）

   A. VMware Fusion
   B. VMware Workstation Pro
   C. VMware Workstation Player
   D. VMware vSphere Hypervisor (ESXi)
   E. VMware Tools

55. 下面哪个命令用于删除soft用户对test目录的ACL权限。 （   ）

   A. setfacl -d u:soft  test
   B. setfacl -k u:soft  test
   C. setfacl -x u:soft  test
   D. setfacl -b test
   E. setfacl -k test

56. 下面哪个命令用于删除test目录的所有ACL权限。 （   ）

   A. setfacl -d u:soft  test
   B. setfacl -k u:soft  test
   C. setfacl -x u:soft  test
   D. setfacl -b test
   E. setfacl -k test

57. 下面哪个命令用于删除test目录的默认ACL权限。 （   ）

   A. setfacl -d u:soft  test
   B. setfacl -k u:soft  test
   C. setfacl -x u:soft  test
   D. setfacl -b test
   E. setfacl -k test

58. 若当前系统中已经安装了Windows系统，在安装Linux的分区过程中应该选择（   ）选项。

   A. 使用手动分区复选框
   B. 删除硬盘上的所有Linux分区后进行安装
   C. 删除硬盘上的所有分区后进行安装
   D. 使用现存的Linux分区进行安装

59. 以降序方式显示使用磁盘空间最多的普通用户的前十名的命令是（   ）。

   A. du -cks /home/* |sort -rn |head -11   
   B. du -cks /home/* |sort -n  |head -11
   C. du -cks /home/* |sort -r  |head -11   
   D. du -cks /home/* |sort     |head -11
   E. du -cks /home/* |sort -rn |head -10   
   F. du -cks /home/* |sort -r  |head -10

60. 下面哪条命令能列出设备检测情况以及Linux启动时装配设备驱动程序的情况。（   ）

   A. boot         B. dmesg           C. fsck           D. sysinfo           E. grub

61. CnetOS 7 中，SELinux 的默认设置是（   ）

   A. 限制            B. 允许            C. 强制           D. 禁用
   
62. 初次启动 CentOS 时一般需要添加一个用户账号，此用户属于哪个类型的用户？（   ）

   A．超级用户        B. 系统用户         C. 普通用户        D. 管理员用户   

63. 如何快速切换到用户 John 的主目录？ （   ）

   A. cd @John        B. cd #John         C. cd &John       D. cd ~John 

64. 关于“cat name test1 test2 >name”命令，以下说法中正确的是 （   ）

   A. 此命令正确，作用是把test1 test2文件的内容合并到name文件 
   B. 此命令错误，不能将输出重定向到输入文件中 
   C. 当name文件为空时，此命令正确  
   D. 此命令错误，应为“cat name test1 test2 >>name”

65. 创建当前目录下名为 “-test” 的文件的可以用以下哪个命令？  （   ）

   A. touch –test    B. touch '-test'     C. touch ./-test     D. touch \-test 

66. 显示当前目录下名为 “-test” 的文件的内容可以用以下哪个命令？ （   ）

   A. cat –test      B. cat ./-test        C. cat '-test'      D. cat \-test 
  
67. 删除当前目录下名为 “-test” 的文件可以用以下哪个命令？ （   ）

   A. rm -f –test     B. rm -f ./-test     C. rm -f '-test'    D. rm -f \-test 
    
68. 想了解命令logname的用法，使用以下哪个命令可得到帮助？ （   ）
  
   A. logname --man    B. logname /?    C. help logname    D. logname --help

69. 如果忘记了ls命令的用法，可以采用（   ）命令获得帮助 

   A. ？ls           B.  help ls          C. get ls          D.  man ls

70. clear命令的作用是  （   ）

   A. 清除屏幕      B.关闭终端窗口      C.打开终端窗口     D. 调整窗口大小

71. CentOS 中用户曾经使用过的命令保存于哪个文件？ （   ）
 
   A.  .bashrc      B.  .bash_history        C.  .bash_profile      D.  .history 

72. 确定 myfile 文件类型的命令是什么? （   ）

   A. type myfile     B. type -q myfile     C. file myfile     D. whatis myfile 

73. Linux 中用于分隔路径的目录名和文件名的字符是什么？ （   ）

   A. slash (/)       B. period (.)         C. dash (-)        D. asterisk (*) 
 
74. 哪个符号加在命令后面可以在后台执行程序? （   ） 

   A. @               B. &              C. #              D. *

75. 在vi编辑器里，哪个命令能将光标移到第200行? （   ） 

   A. 200g            B. :200           C. g200           D. G200

76. 在 Vi 中，替换所有 ”old” 字符串为 ”new” 的命令是？ （   ）
 
   A. :r/old/new       B. :s/old/new      C. :1,$s/old/new/g      D. :s/old/new/g 

77. 所有用户登录的缺省配置文件是： （   ）

   A. /etc/profile      B. /etc/login.defs     C. /etc/.login     D. /etc/.logout  

78. 重定向的符号 “<<" 表示： （   ）

   A. 追加式输出重定向  
   B. 从本地 Here 文件获得输入  
   C. 输出重定向，原来的文件被改写  
   D. 从跟随其后的字符串获得输入  

79. 当程序正从键盘上读取标准输入时，如果希望终止输入，告诉系统已经输完了全部内容，可以键入 （   ）

   A. Ctrl+Z            B. Ctrl+W            C. Ctrl+D          D. Ctrl+V  

80. ls [ad]* 命令解释正确的是：（   ）
 
   A. 显示以a或者d为开头，其他任何字符为结尾的文件（或目录）  
   B. 显示以a或者d出现0次或无数次的文件（或目录）  
   C. 显示包含字母a或者d，其他任何字符为结尾的文件（或目录）  
   D. 显示从字母a到d为开头，其他任何字符为结尾的文件（或目录）  

81. 执行ps命令，有如下输出，如要强行终止 rsync 的运行，需要执行的命令是：（   ）

   PID   TTY     TIME CMD
   333 pts/1 00:00:00 login
   336 pts/1 00:00:00 bash
   337 pts/1 00:12:13 rsync
   356 pts/1 00:00:00 ps 

   A. kill -9 rsync                   B. kill -9 pts/1  
   C. kill -9 337                     D. kill -9 !337  

82. 能杀死后台进程的是 （   ）

   A. ctrl+z           B. ctrl+c         C. kill          D. ctrl+d  

83. 为了将当前目录下所有 .txt 文件打包并压缩归档到文件 this.tar.xz，可以使用：（   ）

   A. tar -Jvf this.tar.gz ./*.txt 
   B. tar -Jcvf this.tar.gz ./*.txt
   C. tar -Jxvf this.tar.gz ./*.txt 
   D. tar -Jtvf this.tar.gz ./*.txt  

84. 对 /etc 下所有文件打包压缩的命令是： （   ）

   A. tar -ztf etc.tar.gz /etc  
   B. tar -zxf etc.tar.gz /etc  
   C. tar -zcf etc.tar.gz /etc  
   D. gzip /etc  

85. tar 命令的 r选项 含义是： （   ）

   A. 产生一个归档  
   B. 向归档文件末尾增加新的文件  
   C. 将归档文件内容展开  
   D. 使用gzip/gunzip来压缩归档文件  

86. 为了将当前目录下的归档文件 myftp.tbz 解压缩到 /tmp目录下，我们可以使用: （   ） 

   A. tar xvjf myftp.tbz -C /tmp        
   B. tar xvjf myftp.tbz -R /tmp
   C. tar xvjf myftp.tbz -X /tmp         
   D. tar xvjf myftp.tbz /tmp

87. 一个文件名字为 abc.zip，可以用哪个命令来解压缩?  （   ）

   A. zip           B. unzip          C. compress           D. gzip

88. 查看当前用户可用环境变量的命令是？ （   ）
 
   A. which           B. man            C. at              D. env  

89. 可以使用哪个命令查找出当前用户运行的所有进程的信息： （   ）

   A. ps -a           B. ps -u          C. ls -a           D. ls -l  

90. 如果需要设置一个可执行文件，使它以文件所有者的权限运行，而非执行它的用户权限。此时需要额外设置该文件的 （   ）

   A. set-GID 位         B. 粘滞位        C. set-UID 位        D. UMASK  

91. Linux 系统中，进程有若干优先级，最低的优先级是：（   ） 

   A. 18                 B. 19               C. 10              D. 20  

92. 目录的可执行权限意味着： （   ）

   A. 目录下可以建立文件                   B. 从该目录中删除文件  
   C. 可以使用cd命令进入此目录             D. 可以查看该目录下的文件  

93. vi 中删除整行文本的指令是: （   ）

   A. d                B. yy                C. dd               D. q  

94. ls –al 命令列出下面的文件列表，问哪一行代表是符号链接文件。（   ）

   A. -rw-------  2 hel  users    56  sep 09 11:05  hello
   B. -rw-------  2 hel  users    56  sep 09 11:05  bonjour
   C. drwx------  1 hel  users  1024  sep 10 08:10  hi
   D. lrwxrwxrwx  1 hel  users     2  sep 10 08:12  salut -> hi    

95. Linux文件权限一共10位长度，分成四段，第三段表示的内容是（   ） 

   A. 文件所有者所在组的权限              B. 文件所有者的权限
   C. 文件类型                            D. 其他用户的权限

96. 将 urls.txt 文件中的域名取出，进行计数统计并按统计字段逆序输出，错误的是。（ ）
     如处理：
     http://a.domain.com/1.html
     http://b.domain.com/1.html
     http://c.domain.com/1.html
     http://a.domain.com/2.html
     http://b.domain.com/2.html
     http://a.domain.com/3.html
     得到如下结果: 域名的出现的次数 域名
       3 a.domain.com
       2 b.domain.com
       1 c.domain.com

   A. cat urls.txt | sed -e ' s/http:\/\///' -e ' s/\/.*//' | sort | uniq -c | sort -rn
   B. awk -F/ '{print $3}' urls.txt |sort|uniq -c|sort -nr
   C. cut -d'/' -f3 urls.txt |sort|uniq -c|sort -nr
   D. awk 'BEGIN{FS="/"}{arr[$3]++}END{for(i in arr) print arr[i],i}' urls.txt| sort -r
   E. awk 'BEGIN{FS="/"}{arr[$3]++}END{for(i in arr) print arr[i],i}' urls.txt| sort -rn

97. 以下哪一项不是进程和程序的区别？（   ）

   A. 程序是一组有序的静态指令。进程是一次程序的执行过程
   B. 程序只能在前台运行，而进程可以在前台或后台运行
   C. 程序可以长期保存，进程是有生命周期的
   D. 程序没有状态，而进程是有状态的

98. 如果你是系统管理员，jack 用户忘记了自己的口令，他希望你帮他重置口令，你可以通过（   ）来实现。 

   A. 删除 /etc/shadow 文件中jack 用户帐户所对应的记录行   
   B. 编辑 /etc/shadow 文件，将jack 用户帐户所对应记录中的口令节内容删除  
   C. 删除 /etc/passwd 文件，将该用户帐户所对应记录中的口令节内容删除   
   D. 执行命令 passwd jack ;  chage -d 0 jack

99. 与命令 lscpu |egrep "AMD-V|VT-x" 功能不等价的命令是 （   ） 

   A. egrep "vmx|svm" /proc/cpuinfo| uniq | fmt -3| egrep "vmx|svm"
   B. fmt -3 /proc/cpuinfo |egrep "vmx|svm" | uniq
   C. lscpu |grep 'Virtualization'
   D. lscpu

100. 下面描述错误的是（   ） 

   A. 使用 lshw -c display 命令可以显示显卡的制造厂商及型号
   B. 使用 lshw -c disk 命令可以显示磁盘的实际尺寸
   C. 使用 lshw -c memory 命令 和 free 命令可以查看物理内存的大小
   D. 使用 lshw -c network  命令可以显示网卡的制造厂商及型号
   E. 使用 lshw -c processor 命令可以显示 CPU 的制造厂商及型号
   F. 使用 lshw -c usb 命令可以显示所有 USB 设备
```

## 三、多选题

```
1. 下面商用操作系统有：(   ) 

   A. Linux       B. Widnows      C. SUN Solaris    D. FreeBSD
   E. IBM AIX     F. SGI Irix     G. HP/UX          H. Mac OS X

2. 下面哪个不是商用操作系统？ (   )

   A. Widnows 10          B. SUN Solaris            C. Debian GNU/Linux
   D. Mac OS X            E. CentOS Linux           F. Red Hat Enterprise Linux

3. 下列哪些命令可以分屏显示文本文件的内容？ （   ）

   A. cat         B. more         C. file          D. less        E. tac        F. rev

4. 下面哪些是开放源代码软件的特点。 (    )

   A. 开放源代码软件一般是免费发布的，您可以在Internet上自由下载，用户无需缴纳License费用。
   B. 开放源代码软件由一个核心组织领导， 通常由一个很大的社区在Internet上协作开发完成。
      这种“集市”式的开发模式使得其通常有着比封闭源代码软件更高的质量。
   C. 用户可以得到软件的源代码，更容易根据自己的特殊要求，进行定制。
   D. 开放源代码软件的生命周期不依附于某个公司，因此有更强的生命力。

5. 下面哪些是Linux操作系统的特性。  (    )

   A. 多用户多任务的系统
   B. 具有出色的稳定性和速度性能
   C. 具有可靠的系统安全性
   D. 提供了丰富的网络功能
   E. 标准兼容性和可移植性
   F. 提供了良好的用户界面

6. 下面哪些是 Debian 系列的 Linux 发型。(    )

   A. Red Hat Enterprise Linux
   B. Q4OS
   C. Mandrake Linux
   D. LinuxMint
   E. Ubuntu Linux
   F. Gentoo Linux
   G. CentOS Linux
   H. elementary OS
   I. Debian Linux 

7. 下面哪些是 Fedora 系列的 Linux 发型。(    )

   A. Red Hat Enterprise Linux
   B. Alpine Linux
   C. Mandrake Linux
   D. LinuxMint
   E. Ubuntu Linux
   F. Arch Linux
   G. CentOS Linux
   H. Rockstor 
   I. Fedora

8. 下面关于GNU和GPL的叙述正确的是（    ）

   A. GNU 是由“GNU's Not Unix”所递归定义出的首字母缩写语。
   B. GNU 的首要目标是制作自由软件。即便 GNU 不比 UNIX 有技术优势，它却有一个允许用户合作的社会优点，
      和一个与道德有关的优点，也就是尊重用户的自由。
   C. 最知名的自由软件协议是GPL ( General Public License，GNU通用公共许可证 ) ，
      她是自由软件基金会（FSF）制定的。
   D. GPL的核心内容是：软件的源程序可以自由流通，软件公司不应该把源程序拒为己有，
      或借发行编译过的软件赢利，软件公司要赚取的应该是系统集成和服务的费用。

9. Shell是： （    ）

   A. 编译器                 B. 命令解释器
   C. 脚本编辑器             D. 程序设计语言

10. ifconfig 和 ip 命令的输出如下：

    # ifconfig eth0
    eth0      Link encap:Ethernet  HWaddr 00:1D:09:2C:F5:4D
              inet addr:110.194.59.131  Bcast:110.194.59.191  Mask:255.255.255.192
              inet6 addr: fe80::21d:9ff:fe2c:f54d/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:1192090411 errors:0 dropped:0 overruns:0 frame:0
              TX packets:1790057039 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000
              RX bytes:189631301456 (176.6 GiB)  TX bytes:2456205479326 (2.2 TiB)

    # ip addr show eth0
    1: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000
        link/ether 00:1d:09:2c:f5:4d brd ff:ff:ff:ff:ff:ff
        inet 110.194.59.131/26 brd 110.194.59.191 scope global eth0
        inet6 fe80::21d:9ff:fe2c:f54d/64 scope link
           valid_lft forever preferred_lft forever
 
   下列哪些选项可以显示 eth0 网络接口当前的 IPv4 地址。 （    ）

   A. ifconfig eth0 | grep 'inet addr' | cut -d':' -f2 | cut -d' ' -f1
   B. ifconfig eth0 | grep 'inet ' | awk -F '[ :]+' '{print $4}'
   C. ifconfig eth0 | awk -F\: '/inet / {print $2}' | awk '{print $1}'
   D. ifconfig eth0 | grep 'inet ' | sed 's/[a-zA-Z:]//g' | awk '{print $1}'
   E. ip addr show eth0 |grep 'inet '| awk -F '[ /]+' '{print $3}'
   F. ip addr show eth0 |grep 'inet '| sed 's/[a-zA-Z: ]//g' | cut -d'/' -f1
   G. ip addr show eth0 |grep 'inet '| sed 's/[a-zA-Z: ]//g' | awk -F '/' '{print $1}'   

11. 在Linux环境下，将当前目录下的文件file的所属组改为softgrp的命令是：(    )

   A. chown softgrp file
   B. chmod softgrp file
   C. chown .softgrp file
   D. chmod .softgrp file
   E. chgrp softgrp file
   F. chgrp .softgrp file

12. 在 CentOS7 下，使用如下哪些命令可以立即关闭Linux系统?  （    ）

   A. halt 
   B. /sbin/stop 
   C. poweroff
   D. shutdown -h now
   E. init 0
   F. systemctl poweroff

13. 在 CentOS7 默认情况下，用于重启的命令是：（    ）

   A. shutdown -r now
   B. halt
   C. reboot
   D. init 6
   E. <Ctrl>+<Alt>+<Del>
   F. systemctl reboot

14. 下面用于对文本文件abc中出现字符串“Linux”的行进行计数的命令是：（    ）

   A. cat abc | find "Linux" | wc  
   B. cat abc | grep "Linux" | wc
   C. cat abc | find "Linux" | wc -l
   D. cat abc | grep "Linux" | wc -l
   E. grep 'Linux' abc |wc -l
   F. grep 'Linux' abc |wc 
   G. grep -c 'Linux' abc

15. 显示文本文件 abc 每一行最后1个字符的命令是： （    ）

   A. rev abc | cut -c1 
   B. tac abc | cut -c1
   C. cat abc | cut -c1 
   D. rev abc | awk -F "" '{print $1}' 

16. 下面只用于显示所有目录的命令是： （    ）

   A. ls –d       B. ls –a     C. ls -l|grep ^d      D. ls -F|grep /$

17. 下面哪个命令用于写盘并退出Vi？ （    ）

   A. q!        B. yy       C. ZZ     D. :wq 
   E. !save     F. quit     G. ZQ

18. 将test的文件属主设置为具有读、写、执行权限，将同组人和其他人设置读和执行权限，下面的命令正确的是（    ）。

   A. chmod 755 test
   B. chmod a+rx,u+w test
   C. chmod u+rwx,g+rx,o+rx test
   D. chmod a+rwx,g-w,o-w test

19. 下面用于显示当前内存使用情况的命令是：（    ）

   A. dmesg        B. free      C. du      D. df       E. cat /proc/meminfo

20. 下面用于暂时锁定某用户账号的命令是： （     ）

   A. usermod -L username 
   B. usermod -U username
   C. passwd -l username
   D. passwd -u username

21. 下面用于恢复暂时锁定的用户账号的命令是：（    ）

   A. usermod -L username 
   B. usermod -U username
   C. passwd –l username
   D. passwd –u username

22. 下面哪些命令用于清空当前目录下abc文件的内容？ （    ）

   A.  touch abc
   B.  cp /dev/null abc
   C.  mv /dev/zero abc
   D.  mv abc /dev/zero
   E.  cp abc /dev/null
   F.  > abc
   G.  : > abc

23. find命令可以用于查找的哪些指定信息的文件或目录： （    ）

   A. 文件的所有权
   B. 文件最后被访问的时间
   C. 大于指定大小的文件
   D. 已经设置setuserid的文件

24. Linux文件类型有哪些：（    ）

   A. 普通文件       B. 链接文件       C. 目录文件
   D. 设备文件       E. 临时文件       F. 系统文件

25. 关于硬链接的描述正确的（    ）。 

   A 可跨文件系统创建           B 不可以跨文件系统创建 
   C 为链接文件创建新的i节点    D 可以做目录的链接
   E 链接文件的i节点与被链接文件的i节点相同

26. 下面是 Apache 访问日志 access_log 的三行截取：

    192.168.33.1 - - [17/Sep/2016:08:40:44 +0800] "GET / HTTP/1.1" 200 10 "-" "curl/7.29.0"
    192.168.33.9 - - [17/Sep/2016:08:40:44 +0800] "GET / HTTP/1.1" 200 10 "-" "curl/7.29.0"
    192.168.33.9 - - [17/Sep/2016:08:40:45 +0800] "GET / HTTP/1.1" 200 10 "-" "curl/7.29.0"

    且 CentOS7 系统执行了如下的语言环境和时区设置：

    # localectl set-locale zh_CN.utf8
    # timedatectl set-timezone Asia/Shanghai

    下面哪些选项可以大致统计 Apache 前1秒的访问数？ （    ）

    A. grep -c $(date -d '1 minute ago' +'%d/%h/%Y:%R') access_log
    B. grep -c $(date -d '1 hour ago' +'%d/%h/%Y:%H') access_log
    C. grep -c $(date -d '1 second ago' +'%d/%h/%Y:%T %z') access_log
    D. grep -c $(LANG=C date -d '1 minute ago' +'%d/%h/%Y:%R') access_log
    E. grep -c $(LANG=C date -d '1 hour ago' +'%d/%h/%Y:%H') access_log
    F. grep -c $(LANG=C date -d '1 second ago' +'%d/%h/%Y:%T %z') access_log
    G. grep -c $(LANG=C date -d 'TZ="Asia/Shanghai" 1 minute ago' +'%d/%h/%Y:%R') access_log
    H. grep -c $(LANG=C date -d 'TZ="Asia/Shanghai" 1 hour ago' +'%d/%h/%Y:%H %z') access_log
    I. grep -c $(LANG=C date -d 'TZ="Asia/Shanghai" 1 second ago' +'%d/%h/%Y:%T %z') access_log
    J. grep -c $(LANG=C date -d 'TZ="Asia/Shanghai" 1 second ago' +'%d/%h/%Y:%T') access_log
	
27. 下面叙述错误的是： （    ）

   A. 在一个Linux系统下只能有一个交换分区
   B. 在一个Linux系统下可以有多个交换分区
   C. 可以用交换文件来扩充交换分区的容量
   D. 当使用交换文件时，无法设置其在开机时自动挂装

28. 向 /etc/resolv.conf 文件追加一笔 DNS 客户配置的命令是（    ）。  

   A. # echo 'nameserver 114.114.114.114' > /etc/resolv.conf
   B. # echo 'nameserver 114.114.114.114' >> /etc/resolv.conf
   C. $ echo 'nameserver 114.114.114.114' | sudo tee /etc/resolv.conf
   D. $ echo 'nameserver 114.114.114.114' | sudo tee -a /etc/resolv.conf

29. 下面哪些软件可用于在 Windows 桌面环境下安装并运行 Linux 虚拟机 （    ）。

   A. VMware Fusion
   B. VMware Workstation Pro
   C. VMware Workstation Player
   D. VMware vSphere Hypervisor (ESXi)
   E. Oracle VM VirtualBox
   F. Citrix XenServer
   G. Proxmox Virtual Environment
   H. RDOproject.org
   I. oVirt.org
   J. Windows Hyper-V

30. 目录/training的所有者为root，所属组为root，其他人无任何权限。若希望用户alex在此目录下创建文件，
    而用户tom可以读取该目录下的文件，则下面的哪些FACL设置可以保证所有的文件以及未来生成的文件的权限正确。（    ）

   A. setfacl -m u:alex:rwx /training  
   B. setfacl -m u:tom:rx /training
   C. setfacl -m d:u:alex:rwx /training  
   D. setfacl -m d:u:tom:rx /training
   
31. 将系统时间修改为 2008年7月24日15时56分 的命令是？  （    ）

   A. date 072415562008              B. date 200807241556                 C. date 155607242008
   D. date -s '20080724 1556'        E. timedatectl set-time '2008-07-24 15:56'

32. 已知某用户st，其用户目录为 /home/st。若当前目录为 /home，使用哪些命令可进入 /home/st/test 目录？（    ）

   A. cd test         B. cd /st/test       C. cd st/test      D. cd home      E. cd /home/st/test

33. CentOS 7 所支持的安装方式有（    ）。  
 
   A. 通过Telnet进行网络安装         B. 从本地硬盘驱动器进行安装
   C. 通过NFS进行网络安装            D. 通过HTTP进行网络安装

34. 下列哪几个符号是Linux通配符（    ）。  

   A. #           B. @            C. *             D. ?          E. []        F. [!]  

35. ls –al 命令的列表输出如下，如下叙述正确的是（    ）。  

   -rw-------  2 hel  users    56  sep 09 11:05  hello
   -rw-------  2 hel  users    56  sep 09 11:05  bonjour
   drwx------  2 hel  users  1024  sep 10 08:10  hi
   lrwxrwxrwx  1 hel  users     2  sep 10 08:12  salut -> hi    

   A. hello 是 bonjour 的硬链接文件
   B. bonjour 是 hello 的硬链接文件
   C. hi 是 salut 的符号链接文件
   D. salut 是 hi 的符号链接文件

36. 要安全删除Linux必须进行那两个步骤？ （    ）

   A. 删除引导装载程序             B. 删除超级 用户
   C. 删除Linux的磁盘分区          D. 删除安装日志文件 

37. 要查看 httpd 服务进程的信息，可以使用命令？ （    ）

   A. pstree|grep httpd  
   B. ps aux|grep httpd   
   C. pgrep httpd   
   D. ps -ef|grep httpd   
   E. ps $(pgrep httpd)  
   F. lsof -i:80 
   G. ps $(pidof httpd)

38. 要强制杀死 rsync 进程，可以使用命令？ （    ）

   A. kill -9 rsync  
   B. killall -9 rsync  
   C. kill -9 $(pgrep rsync)
   D. kill -9 $(pidof rsync) 
   E. pgrep rsync | xargs kill -9
   F. pidof rsync | xargs kill -9

39. 执行如下命令之后，顺序执行选项中的 cd 命令，哪些可以正确执行？ （    ）

   $ mkdir -p ~/centos7/{book,labs,test}/{base,sys,net}
   $ cd ~/centos7/test

   A. cd test/base
   B. cd base/sys/net
   C. cd sys
   D. cd ../labs/net
   E. cd centos7/book
   F. cd -
   G. cd ../sys 
   H. cd centos7/labs/sys
   I. cd ~ 
   J. cd centos7/sys
   K. cd centos7/labs/sys
   L. cd 

40. 执行如下命令之后，顺序执行选项中的命令，哪些可以正确执行？ （    ）

   $ mkdir -p ~/centos7/{book,labs,test}
   $ touch ~/centos7/{book,labs,test}/ch{01..16}.md
   $ cd ~/centos7/test

   A. ls test/ 
   B. ls ~/centos7
   C. less book/ch01.md
   D. vi ../labs/ch01.md
   F. tree centos7
   G. tree ../book 
   H. tree ~/centos7/test
   I. rm -rf test 
   J. rm -f *
   K. cp ../centos7/labs/ch01.md .
   L. cp ../labs/ch01.md .
```

## 四、搭配题

```
1、选出 find 命令与其对应的功能

(  ) 0. find .                     A. 用户自家目录及其子目录下的硬连接数大于2的文件
(  ) 1. find /home -nouser         B. 目录 /home 下的所有目录
(  ) 2. find . -perm 755           C. 当前目录下的所有权限为755的文件、目录和全部子目录
(  ) 3. find ~ -user root          D. 目录 /home 及其子目录下小于 512k 的文件
(  ) 4. find ~ -links +2           E. 目录 /home 及其子目录下的空文件或目录
(  ) 5. find /home -type d         F. 列出 /home 及其子目录下不属于本地用户的文件或目录
(  ) 6. find /home -empty          G. 当前目录下的所有文件、目录和全部子目录
(  ) 7. find . -perm -100          H. 用户自家目录下属主为 root 的所有文件和目录
(  ) 8. find /home -size -512k     I. 目录 /home 及其子目录下大于 512k 的文件
(  ) 9. find /home -size +512k     J. 当前目录及子目录下权限至少属主可运行的所有文件

(  ) 10. find . -name ap* -o -name may*        K. 当前目录下除 book 目录的所有文件或目录
(  ) 11. find . -newer file1 ! -newer file2    L. 仅查找根文件系统下的所有符号链接
(  ) 12. find /mnt -name t.txt ! -ftype vfat   M. 用户家目录下40天前被修改过的文件
(  ) 13. find /tmp -name wa* -type l           N. 用户lrj的在 /data 目录下7天内被修改过的所有文件
(  ) 14. find -name ".*" -perm 755             O. 当前目录及子目录下的所有以 ap 或 may 开头的文件
(  ) 15. find / -xdev -type l                  P. 列出/home内的tmp.txt 查时深度最多为3层
(  ) 16. find /home -name tmp.txt -maxdepth 4  Q. 查找权限位为755的隐藏文件
(  ) 17. find /data -mtime -7 -user lrj        R. 在/mnt下查找名称为tom.txt且文件系统类型不为vfat
(  ) 18. find $HOME -type f -mtime +40         S. 更改时间比 file1 新但比 file2 旧的所有文件
(  ) 19. find . -name book -prune -o -print    T. 在/tmp下查找名为wa开头且类型为符号链接的文件

(  ) 20. find . *.c -exec cp '{}' /tmp ';'             U. 删除 /data 及其子目录下30天之内未修改过的.xz文件
(  ) 21. find . -size +3G -exec ls -lt {} \;           V. 将当前目录及子目录下的C语言文件拷到/tmp
(  ) 22. find /data -atime +30 -exec rm -rf {} \;      W. 删除 /data 及其子目录下30天内没访问过的文件或目录
(  ) 23. find /data -name "*.xz" -mtime +30 |xargs rm  X. 列出当前及其子目录下当天修改过的文件
(  ) 24. find . -mtime -1 -type f -exec ls -l {} \;    Y. 以时间顺序显示当前目录及子目录下大于3GB的文件
(  ) Z5. find ~ ( -name a.out -o -name '*.o' ) \       Z. 删除一周以来从未访问过的以 .o 结尾或名为 a.out
         -atime +7 ! -fstype nfs -exec rm {} \;           且不存在于 nfs 文件系统中的所有文件

２、 将下列的设备文件名和所对应的设备联系起来。

(  ) 1. /dev/sdb1                A. 第一个本地回环设备 
(  ) 2. /dev/tty0                B. 第二块SCSI/SATA/SAS硬盘设备的第一个分区
(  ) 3. /dev/loop0               C. 第一个远程终端设备              
(  ) 4. /dev//dev/pts/0          D. 第一个本地虚拟终端

３、 将下列实现同样功能的DOS命令或提示符和Linux命令或提示符联系起来。
     (如果你学习过DOS，通过本题可以进行对比学习；若你没学过DOS，可不做)

(  )  01. > copy  joe.txt  joe.doc         A.  $ rm *~
(  )  02. > copy  *.*  total               B.  $ mv  paper.txt  paper.asc
(  )  03. > copy  fractals.doc   prn       C.  $ less letter.txt
(  )  04. > del  temp                      D.  $ cat  letter.txt > /dev/null
(  )  05. > del  *.bak                     E.  $ cat  * > total
(  )  06. > ren  paper.txt  paper.asc      F.  $ cat  fractals.doc | lpr
(  )  07. > type  letter.txt               G.  $ rm  temp  
(  )  08. > type  letter.txt > nul         H.  $ cp  joe.txt  joe.doc
(  )  09. > dir  file.txt                  I.  $ pwd 
(  )  10. > dir  \*.tmp /s                 J.  $ mkdir  newsprogs
(  )  11. > cd                             K.  $ ls  file.txt
(  )  12. > cd ..\temp\trash               L.  $ rmdir  /progs/trubo
(  )  13. > md newprogs                    M.  $ find  / -name "*.tmp"
(  )  14. > rd \progs\trubo                N.  $ alias  disp='ls|more'
(  )  15. > doskey disp=dir/p              O.  $ cd ../temp/trash
(  )  16. > a:                             P.  /mnt/floppy $
(  )  17. > dir a:                         Q.  $ cd  /mnt/floppy
(  )  18. > copy a:*.*  .                  R.  $ ls  /mnt/floppy
(  )  19. > copy *.zip  a:\zip             S.  $ cp  /mnt/floppy/*  .
(  )  20. A:\>                             T.  $ cp  *.zip  /mnt/floppy/zip
```
## 五、简答题

1、如何为英文 CentOS7 服务器设置中文环境?

2、简述Linux 文件系统通过i 节点把文件的逻辑结构和物理结构转换的工作过程。

3、什么是符号链接，什么是硬链接？符号链接与硬链接的区别是什么？

4、简述进程的启动、终止的方式以及如何进行进程的查看。

5、exec 和 souce 区别?