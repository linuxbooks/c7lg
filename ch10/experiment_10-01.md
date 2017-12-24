# 实验指导 10 - Shell 编程

>#### 学习目标
> * 掌握脚本的编辑、运行和调试方法
> * 掌握 bash 变量的定义、引用、替换扩展
> * 掌握 bash 的各种流程控制语句
> * 掌握 bash 函数的定义和调用方法
> * 掌握命令行参数的使用方法
> * 掌握避免错误的处理方法使得脚本更健壮

## 任务1：编写一个最小化安装 CentOS7 后的配置脚本

**要求：**

1. 配置 YUM 并更新系统
  * 安装 EPEL 仓库
  * 导入已安装所有仓库的 GPG 签名文件 `/etc/pki/rpm-gpg/RPM-GPG-KEY-*`
  * 配置所有仓库的国内镜像URL
  * 更新系统
2. 安装常用的必要的软件
  * bash-completion vim-enhanced
  * net-tools psmisc yum-cron yum-utils
  * wget curl elinks lftp mailx mutt rsync ntp
  * sysstat htop dstat nload nethogs iftop
  * rkhunter aide denyhost fail2ban lynis
3. 系统基本配置
  * 设置语言、时区
  * 设置主机名
  * 创建一个普通用户并为其设置口令
  * 禁用 chrony 和 ntp 服务
  * 使用 ntpdate 配置每日时间同步
  * 限制每个用户能打开的最大文件数
  * 限制仅 wheel 组的人才能使用 sudo 和 su 命令
  * 关闭 SELINUX
  * 预先写入 root 远程 ssh 登录的公钥
  * 确保网络参数配置正确后关闭 NetworkManager 服务
4. 安全配置
  * SSH
    * 允许使用口令登录但 root 用户只能使用密钥登录
    * 关闭 DNS 反向解析检查
    * ssh 回话闲置 5 分钟后自动注销登录
    * 安装配置 fail2ban
  * 口令
    * 口令必须大于12个字符
    * 必须至少包含四类字符中的一个
  * 网络 
    * 开启防火墙

## 任务2：根据 shell 类型统计用户数

**要求：**

1. shell 类型通过命令行参数 `-s <SHELL>` 的形式指定
  * 显示 shell 类型为 SHELL 的用户数并列出所有用户名
  * SHELL 必须是 `/etc/shells` 文件中存在的类型，否则不执行脚本且退出状态码为1
2. 当没有给出命令行参数或命令行参数为 `-h | --help` 时，显示帮助信息并退出
3. 当命令行参数为其他值时，显示提示信息且退出状态码为2

若脚本名为 usersbysh，执行效果如下：

```
$ usersbysh -s bash
bash - 3 users , they are: root,student,tony
$ echo $?
0

$ usersbysh -s zash
Invalid shell.
$ echo $?
1

$ usersbysh
Usage: usersbysh -s <SHELL>|-h|--help
根据 shell 类型统计用户数并显示用户列表
$ echo $?
0

$ usersbysh --help
Usage: usersbysh -s <SHELL>|-h|--help
根据 shell 类型统计用户数并显示用户列表
$ echo $?
0

$ usersbysh -a
usersbysh：无效选项 -- a
Try 'usersbysh --help|-h' for more information.
$ echo $?
2
```

## 任务3：根据用户选择显示不同类型的系统信息

**要求：**

1. 向用户展示功能菜单，具有如下功能：
  * 显示所有登录用户
  * 显示系统平均负载
  * 显示物理内存的使用
  * 显示交换空间的使用
  * 显示磁盘空间的使用
  * quit或q
2. 读取用户从键盘上的选择
  * 根据不同的选择执行相应的命令
  * 选择 quit 或 q 时退出脚本
  * 输入错误的选择时退出脚本，且退出状态吗返回1

## 任务4：任务3扩展

**要求：**

1. 当用户选择显示相应信息后不退出，而让用户继续选择，继续显示相应内容，用户选择 quit 菜单项才退出。
2. 使用 `while` 语句 和 `select` 语句分别完成。

## 任务5：检测与服务器处于同一子网的每台主机的连通性

**要求：**

1. 通过 `ip|ifconfig` 命令获取本机 IP 地址
  * 使用变量替换扩展删除最后一位十进制数  
2. 通过 ping 命令测试当前主机与 1..254 所有主机的连通性
  * 若能 ping 通就显示 "`<IP>` is up."，其中的IP要换为真正的IP地址，且以绿色显示
  * 若不能 ping 通就显示"`<IP>` is down."，其中的IP要换为真正的IP地址，且以红色显示
3. 请分别使用 `while`，`until` 和 `for` (两种形式)循环实现

> **提示** 为避免突发性的线路故障发生，在使用 ping 时，每次等待 ping 的响应时间可以设置稍长一些（如：`-W 2`）

## 任务6：任务5 的函数实现方式

**要求：**

1. 使用函数实现获取本机 IP 地址
2. 使用函数实现一台主机的连通性判定
3. 在主程序中调用函数判定指定范围内的所有主机的在线情况

> **扩展** 根据子网掩码的值确定要 ping 的主机的 IP 地址范围

## 任务7：找出使用率大于 90% 的所有分区

**要求：**

1. 使用 read 配合 while 语句实现
2. 将 df 命令的输出结果通过管道传递给 while
  * 不要对虚拟文件系统进行操作 
3. 将结果通过邮件发送给 root
  *  只有当有使用率大于 90% 的分区时才发送邮件
  *  邮件主题为：Warn: Disk Usage on <主机的FQDN>
  *  邮件体包含：找出的分区设备名（挂装点）和使用率 

>1. **思考1**：循环控制语句 
>  * 若 df 的输出结果以使用率**降序**排序后再通过管道传递给 while 时，在循环体内可以使用哪个循环控制语句配合条件判断来优化？
>  * 若 df 的输出结果以使用率**升序**排序后再通过管道传递给 while 时，在循环体内可以使用哪个循环控制语句配合条件判断来优化？  
>2. **思考2**：下面的命令行能完全实现要求的功能吗？为什么？ 
>  * `df -PT |egrep -v '^Filesystem|tmpfs'|sort -nr -k6 | awk '{print $6 , $7}'|mail -s "Warn: Disk Usage on $(hostname -f)" root`
>  * `df -PT |egrep -v '^Filesystem|tmpfs' | sed 's/%//' |awk '$6>90 {printf "%d%% used on %s (%s)\n", $6, $7, $1}'|mail -s "Warn: Disk Usage on $(hostname -f)" root`


## 任务8：找出使用率大于 N% 的所有分区

任务7 扩展

**要求：**分别实现如下两种情况

1. N 通过命令行参数传递给脚本
   * 若 N 不是值为 0~99 的数字，给出出错提示并退出脚本且退出状态码为1 
2. N 通过 read 从键盘读取
  * 使用循环由键盘读取 N，直至读取的值为 0~99 的数字为止 

>**提示** 
>判断 shell 变量的值 $n 是否为纯数字的方法
>```
>[ -n "$n"  -a  -z "$(sed 's/[0-9]//g' <<<$n)" ]
>[ -n "$n"  -a  -z "$(egrep -o '[^0-9]+' <<<$n)" ]
>[ -n "$n"  -a  -z "${n//[0-9]/}" ]
>[ -n "$n"  -a  "$n" == "${n//[0-9]/}" ]
>
>[[ -n "$n"  &&  -z "$(sed 's/[0-9]//g' <<<$n)" ]]
>[[ -n "$n"  &&  -z "$(egrep -o '[^0-9]+' <<<$n)" ]]
>[[ -n "$n"  &&  -z "${n//[0-9]/}" ]]
>[[ -n "$n"  &&  "$n" == "${n//[0-9]/}" ]]
>```


## 任务9：打印 1~N 之间的所有 奇数|偶数|素数

**要求：**

1. 编写一个函数用于判断一个字符串是否为纯数字的值 
2. 编写三个函数分别用于打印 1~N 之间的所有 奇数|偶数|素数
3. 编写一个函数显示脚本的格式和功能
3. 脚本的命令行参数
  * 第一个参数必须为一个数字，否则显示使用帮助信息，并设置退出状态码为1
  * -o|--odd ：打印奇数
  * -e|--even：打印偶数
  * -p|--prime：打印素数
  * -a|--all：打印奇数、偶数和素数
  * -h|--help：显示使用帮助信息
  * 对于其他的参数应该报错，并设置退出状态码为2
  * 可以同时指定多个参数，例如 -o -p 表示既打印奇数又打印素数

## 参考资源

* [Shell 编程之语法基础](https://linuxtoy.org/archives/shell-programming-basic.html)

