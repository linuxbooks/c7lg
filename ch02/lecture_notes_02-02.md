# CH02U02 - Shell 特性

## 什么是 Shell

* Shell是系统的用户界面，提供了用户与内核进行交互操作的一种接口(**命令解释器**) 。
* Shell接收用户输入的命令并把它送入内核去执行。
* Shell起着协调用户与系统的一致性和在用户与系统之间进行交互的作用。

## Shell 的主要版本

* bash ：Bourne Again Shell （bash, bsh 的扩展）。
  * 是 Linux 使用的默认 Shell
* tcsh ：是 C Shell 的扩展。
* ksh ：是 UNIX 系统上的标准 Shell。

* 系统可用的 Shell
      cat /etc/shells

## 文件通配符

* *：匹配任何字符和任何数目的字符
  * 能匹配文件或目录名中的 .
  * 不能匹配首字符是 . 的文件或目录名
* ?：匹配单一数目的任何字符
* [ ]：匹配[ ]之内的任意一个字符
* [! ]：匹配除了[! ]之外的任意一个字符，!表示非的意思

>**参考**
>
>* $ man 7 glob

## 文件通配符 - 字符类型

* `[[:lower:]]` 等价于 `[a-z]`
* `[[:upper:]]` 等价于 `[A-Z]`
* `[[:alpha:]]` 等价于 `[a-zA-Z]`
* `[[:digit:]]` 等价于 `[0-9]`
* `[[:alnum:]]` 等价于 `[a-zA-Z0-9]`
* `[[:cntrl:]]` 任何一个控制字符
* `[[:blank:]]` 任何一个 空格符 或 制表符（呈水平排列的空白字符）
* `[[:space:]]` 任何一个 空格符 或 制表符 或 换行符 或 换页符 或 回车符（呈水平或垂直排列的空白字符）
* `[[:print:]]` 任何一个可打印字符，包括空格
* `[[:graph:]]` 任何一个可打印字符，不包括空格
* `[[:punct:]]` 除了空白字符和字母数字之外的任何一个可打印字符（标点符号）

## 通配符使用举例

```
ls *.c          # 列出当前目录下的所有C语言源文件
ls /home/*/*.c  # 列出/home目录下所有子目录中的所有C语言源文件
ls n*.conf      # 列出当前目录下的所有以字母n开始的conf文件
ls test?.dat    # 列出当前目录下的以test开始的，随后一个字符是任意的.dat文件
ls [abc]*       # 列出当前目录下的首字符是a或b或c的所有文件
ls [!abc]*      # 列出当前目录下的首字符不是a或b或c的所有文件
ls [a-zA-Z]*    # 列出当前目录下的首字符是字母的所有文件
```

## 命令行补全

* 使用方法
  * 直接补全：`<Tab>`
  * 显示与输入开头的内容匹配的列表： `<Tab><Tab>`
* 可以补全
  * 命令名
  * 路径与文件名
  * 用户： `~<TAB><TAB>`
  * 变量： `$<TAB><TAB>`

## 命令历史

* bash 自动保存输入的命令历史
* 查看命令历史
  * `history` ： 查看所有命令历史 
  * `history n` ： 查看命令历史中最近的 n 条命令
* 相关的环境变量
  * `HISTSIZE`： 命令历史记录的条数
  * `HISTFILE`： 默认为 ~/.bash_history
  * `HISTFILESIZE`： 命令历史文件记录历史的条数
  * `HISTIGNORE`：指定不被记入命令历史的命令（多个用:间隔）
  * `HISTCONTROL`：控制命令历史的记录方式
    * *ignoredups*：忽略重复（连续且相同）的命令
    * *ignorespace*：忽略所有以空白字符开头的命令
    * *ignoreboth*：ignoredups & ignorespace
    * *erasedups*：剔除整个命令历史中的重复条目
* 操作命令历史
  * `history -a` ： 追加当前会话缓冲区的命令历史列表至命令历史文件中
  * `history -r` ： 读取命令历史文件并将其内容追加到当前会话缓冲区的历史列表中
  * `history -c` ： 手动清除当前会话缓冲区的命令历史列表

## 使用命令历史

>* 使用 up（向上）和 down（向下）键来上下浏览以前输入的命令

* `!!` 		重复前一个命令
* `!n`		按照 history 命令输出中的序号来重复对应命令
* `!-n`		重复n个命令之前的那个命令
* `!string`	重复前一个以 “string” 开头的命令
* `!?string`	重复前一个包含 string 的命令

## 命令行编辑  

* 重新调用前一个命令中最后一个参数
  * `<Esc>,.` （点击 Esc键，然后点击 . 键）
  * `<Alt>+.`（按住 Alt键的同时点击 . 键）
  * `!$` 
* `^old^new`
  * `cp  filter.c    /usr/local/src/project`
  * `^filter^frontend`
* 快捷键
 * `Ctrl-a`     -     移动到行首
 * `Ctrl-e`     -     移动到行尾
 * `Ctrl-u`     -     删除到行首
 * `Ctrl-k`     -     删除到行尾
 * `Ctrl-arrow`   `ctrl-b`  `ctrl-f`   -      向左或向右移动一个字符
 * `Esc-b`      -     左移一个单词 
 * `Esc-f`      -     右移一个单词 


>**其他快捷键**
>* `Ctrl-l`     -     `clear`
>* `Ctrl-d`     -      正常终止一个进程的执行
>* `Ctrl-c`     -      强行终止一个进程的执行

## 命令别名

* 创建使用命令的快捷方式
      alias dir='ls -laF'
* 显示所有已设置的所有别名的值
      alias
* 显示指定别名的值
      alias dir 
* 取消别名的定义
      unalias dir

>* 同时存在命令和同名的别名时，若要执行原命令
>  可使用 `\COMMAND` 形式，如 `\ls`

## 命令行扩展 - ~ 扩展

* 颚化符号（~）
* 可以代表你的主目录
      cat ~/.bash_profile
* 可以代表另一个用户的主目录
      ls ~osmond/public_html

## 命令行扩展 - 大括号扩展

* 打印重复字符串的简化形式

```
$ echo file{1,3,5} 
file1 file3 file5 
$ rm -f file{1,3,5}
```

```
$ cp abc.{conf,conf.bak}
$ cp abc.conf{,.bak}
$ echo --exclude={abc,bcd,cde}
```

```
$ echo file{1..5}
file1 file3 file5 
$ cp file{1..5} mydir
$ echo 2016-{09..12} 2017-{01,02}
```

## 命令行扩展 - 命令替换

* 命令行扩展：**`$( )`** 或 **``**
  * 把一个命令的输出打印给另一个命令的参数
* 举例：

```
$ echo "This system's name is $(hostname)."
This system's name is server1.example.com
$ echo "i am `whoami`"
i am root
$ rpm -qi $(rpm -qf $(which ls))
```

## bash 变量

* 变量是被命名的值
* 用于保存数据或命令输出
* 定义变量的值（赋值）
  * `变量名=值`
* 引用变量的值（变量替换/变量引用）
  * `$变量名`
  * `${变量名}`
* 默认设置的变量是本地变量（Local variables）
  * 作用范围仅限制在其命令行所在的 Shell

```
$ HI=“hello, and welcome to $(hostname).”
$ echo $HI
Hello, and welcome to cl7h1.
```

```
linux=distro
distro=centos
echo ${!linux}  # 变量的间接引用
```

>**强引用和弱引用**
>* `""`：弱引用，其中的变量引用会被替换为变量值
>* `''`：强引用，其中的变量引用不会被替换为变量值，而保持原字符串

## 防止扩展

* 反斜线（\）会使随后的字符按原意解释
      $ echo Your cost: \$5.00 
      Your cost: $5.00
* 加引号来防止扩展
  * 单引号（`''`）防止所有扩展
  * 双引号（`""`）也防止所有扩展，但是以下情况例外：
    * `$`（美元符号）　－　变量扩展
    * **`**（反引号）  －　命令替换
    * `!`（叹号）　    －　历史命令替换

## bash 变量 - 算数运算

* bash 默认的变量类型为 **字符串**
* 变量的整数运算
  * `$[算术表达式]`
  * `$((算术表达式))`
* 变量的浮点运算
  * 需借助外部工具实现，如： `bc`、`awk`


## 标准输入和标准输出

* Linux 给运行的程序提供三种 I/O 通道
  * 标准输入（STDIN）－　默认接受来自键盘的输入  -  fd=0
  * 标准输出（STDOUT）－　默认输出到终端窗口  -  fd=1
  * 标准错误（STDERR）－　默认输出到终端窗口  -  fd=2

## 输出重定向

* STDOUT 和 STDERR 可以被重定向到文件
  * 命令　操作符　文件名
* 操作符：（覆盖式）
  * `>` 　把STDOUT重定向到文件
  * `2>`　把STDERR重定向到文件
* 操作符：（追加式）
  * `>>` 　把STDOUT重定向到文件（追加式）
  * `2>>`　把STDERR重定向到文件（追加式）


## 输出重定向举例

* 覆盖式  
      ll /etc /qaz > ll.out
      ll /etc /qaz 2> ll.err
      ll /etc /qaz > ll.out 2> ll.err
* 追加式 
      ll /etc /qaz >> ll.out
      ll /etc /qaz 2>> ll.err
      ll /etc /qaz >> ll.out 2>> ll.err

## 管道

* 将 STDOUT 重定向给程序
* 管道（使用符号“|”表示）用来连接命令
  * `命令1 | 命令2`
  * 将命令1的STDOUT发送给命令2的STDIN
  * 默认地，STDERR 不能通过管道传递给下一个命令
* 用来组合多种工具的功能
      ls -C | tr 'a-z' 'A-Z'

## 管道使用举例

* less ：一页一页地查看输入：
      $ ls -l /etc | less
* grep ：过滤文本
      $ ls -l | grep "^d"
      $ cat /etc/passwd | grep ^username
      $ dmesg | grep eth0
* mail： 通过电子邮件发送输入：
      $ echo "test email" | mail -s "test" user@example.com

* 统计磁盘占用
      $ du . --max-depth=1 | sort -rn | head -11
      $ du * -cks | sort -rn | head -11
      $ du -S | sort -rn | head -11
* 统计进程
      # ps -e -o "%C : %p : %z : %a"|sort -k5 -nr （按内存使用）
      # ps -e -o "%C : %p : %z : %a"|sort -nr     （按CPU使用）
* 统计当前目录下的文件数和目录数
      $ ls -l | grep "^-" | wc -l 
      $ ls -l | grep "^d" | wc -l 
* 为用户设置临时口令
      # echo "passw0rD" | passwd --stdin user1

## 合并 STDOUT 和 STDERR

* 重定向所有输出
  * `&>`　 把所有输出重定向到文件（覆盖式）
        ll /etc /qaz &> ll.out_err 
  * `&>>`　把所有输出重定向到文件（追加式）
        ll /etc /qaz &>> ll.out_err 
* 把 STDERR 重定向给 STDOUT
  * `2>&1`： **用于以管道方式同时传递 STDOUT 和 STDERR**
        ll /etc /qaz 2>&1 | less
  * `|&`： **`2>&1 |` 的简化形式**
        ll /etc /qaz |& less
* `()`：合并多个程序的 STDOUT 和 STDERR
        ( cal -3 ; ll /etc ) | less
        ( cal -3 ; ll /etc /qaz ) | less

## 重定向到多个目标（tee）

    $　命令1 | tee　文件名 | 命令2 

* 把命令1的STDOUT保存在文件名中，然后管道输入给命令2
* 使用：
  * 保存不同阶段的输出
  * 复杂管道的故障排除
  * 同时查看和记录输出
* 举例
      ll | tee /tmp/saved-output
      ll | tee -a /tmp/saved-output | mail -s "ll-output" root
      echo "strings" | sudo tee -a somefile
      ./some_script.sh 2>&1 | awk '{ print strftime("[%Y-%m-%d %H:%M:%S]"), $0 }' | tee -a some_script.log


## 从文件中导入 STDIN

* 使用　`<`　来重定向标准输入
* 某些命令能够接受从文件中导入的STDIN：
      $ tr 'A-Z' 'a-z' < .bash_profile 
  * 相当于：
      $ cat .bash_profile | tr 'A-Z' 'a-z'
* 下载 urls.txt 中列出的所有文件
      $ xargs -n 1 curl -O < urls.txt

## Here Strings 和 Here Documents

* 就地字符串（Here Strings）
  * <<< "Strings"
```
wc -c <<< "Strings"
wc -c <<< $PATH
```
* 就地文本（Here Documents）
  * 使用 `<<终止词` 从键盘将多行内容重定向给 STDIN
  * 直到　`终止词`　位置的所有文本都发送给 STDIN
  * 可将将多行内容发送给 STDIN
```
$ cat > ~/mail.txt <<END 
> Hi Jane,
>        
> Please give me a call when you get in. 
> 
> Boris 
> END
$ mail -s "Please Call" jane@example.com < ~/mail.txt
或：
$ mail -s "Please Call" jane@example.com <<END 
> Hi Jane,
>        
> Please give me a call when you get in. 
> 
> Boris 
> END
```

## 命令的执行结果

* 命令/程序 的执行结果
 * 执行结果（屏幕输出）
 * 执行状态结果（仅关注执行成功与否）
* 执行结果的状态值
  * 使用特殊变量 `$?` 保存最近一条命令的执行状态
  * **0**：成功
  * **1-255**：失败

```
ls
echo $?
ls $RANDOM
echo $?
```

## 命令列表（在一个命令行上执行多个命令）

* 顺序执行
      cal ; date; whoami
* 用逻辑运算组合多个命令
  * `&&` ： 只有左面的命令执行正确才执行右侧的命令（短路作用）
  * `||` ： 只有左面的命令执行错误才执行右侧的命令（短路作用）
  * `!` : 对命令的执行状态按逻辑取反
* 举例
      ping -c1 8.8.8.8 &> /dev/null && echo Ping-Pong 
      grep -q '^myname:' /etc/passwd || echo myname not exist. 
      ! ping -c1 8.8.8.8 &> /dev/null || echo Ping-Pong 
      ! grep -q '^myname:' /etc/passwd && echo myname not exist. 
      grep -q '^myname:' /etc/passwd && echo "myname exist." || useradd myname


>**&&（与）**：
>* CMD1 **&&** CMD2
>  * 成功 && 成功  = 成功
>  * 成功 && 失败  = 失败
>  * **失败 &&** 成功  = 失败 （短路）
>  * **失败 &&** 失败  = 失败 （短路）
>---
>**||（或）**：
>* CMD1 || CMD2
>  * **成功 ||** 成功  = 成功 （短路）
>  * **成功 ||** 失败  = 成功 （短路）
>  * 失败 || 成功  = 成功 
>  * 失败 || 失败  = 失败


## 在 子Shell/当前Shell 中执行命令 

* 命令列表（命令组合）
      i=0
      cal ; date; echo $[i+=7]
      cal ; date; echo $[i+=7] >> /tmp/output
      cal ; date; echo $[i+=7] | wc -l
* 用子shell组合执行多个命令
      i=0
      (cal ; date; echo $[i+=7])
      echo $i
      ( cal ; date; echo $[i+=7] ) >> /tmp/output
      cal ; ( date; echo $[i+=7] ) | wc -l 
* 用当前shell组合执行多个命令
      i=0
      { cal ; date; echo $[i+=7]; } 
      echo $i
      { cal ; date; echo $[i+=7]; } >> /tmp/output
      cal ; { date; echo $[i+=7]; } | wc -l 

>```
>{
>  cal
>  date
>  echo $[i+=7]
>}
>```
>```
>(cal
> date
> echo $[i+=7])
>```

## 在 子Shell/当前Shell 中执行脚本

* 在 子Shell 中执行脚本
      bash scriptname     （脚本名可使用 绝对路径 或 相对路径 指定）
      scriptname          （脚本位于 $PATH 的搜索路径中，且具有执行权限）
      /path/to/scriptname （脚本可能不在 $PATH 的搜索路径中，但具有执行权限）
      ./scriptname        （脚本在当前目录中，且具有执行权限）
* 在 当前Shell 中执行脚本
      source scriptname   （脚本名可使用 绝对路径 或 相对路径 指定）
      . scriptname        （脚本名可使用 绝对路径 或 相对路径 指定）

## bash 如何展开命令行

1. 把命令行分成单个命令词
2. 展开别名
3. 展开大括号中的声明（{}）
4. 展开颚化声明（~）
5. 命令替换 （ $()　或　``）
6. 再次把命令行分成命令词
7. 展开文件通配（*、?、[abc]等等）
8. 准备I/0重定向（<、>）
9. 运行命令！


>**`eval`** 命令
>* 首先扫描命令行进行所有的替换（变量替换、命令替换），然后再执行命令
>* 比较
>```
>echo {$(date -d '-5 seconds' +%s)..$(date +%s)}
>eval echo {$(date -d '-5 seconds' +%s)..$(date +%s)}
>begin=$(date -d '-5 seconds' +%s)
>end=$(date +%s)
>echo {$begin..$end}
>eval echo {$begin..$end}
>```

## bash 环境变量

* 环境变量可以被 子 shell（subshell）继承
  * 作用范围则包括本 Shell 进程及其所有子进程
* 使用 `export` 内置命令将本地变量设置为环境变量
  * `export <变量名1=值1>  [<变量名2=值2> ...]`
  * `export <变量名1> [<变量名2> ...]`
* 查看环境变量
  * `env` - 查看所有的环境变量
  * `set` - 查看所有的环境变量和自定义变量
* 取消变量设置
  * `unset <变量名1> [<变量名2> ...]`
* 将环境变量转换为本地变量  
  * `export -n <变量名1> [<变量名2> ...]`


## 登录 shell 和非登录 shell

* 登录 shell 和非登录 shell 的启动配置不同
* 登录 shell
  * 任何在登录时创建的shell（包括Ｘ登录）
  * `su -` 
* 非登录 shell
  * `su`
  * 图形化终端
  * 执行的脚本
  * 任何其它 shell 实例


## shell 的环境配置文件

* 登录 shell 的环境配置文件 profile
  * `/etc/profile` （全局）
  * `~/.bash_profile` （个人）
  * 用于 设置环境变量、 运行命令（如邮件检查程序脚本）等
* 非登录 shell 的环境配置文件 bashrc
  * `/etc/bashrc`（全局）
  * `~/.bashrc`（个人）
  * 用于 设置本地变量、定义别名 等

## 环境文件读取过程

```
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

  Login shell: 
        |--> /etc/profile --> /etc/profile.d/*.sh
		|
		|-> $HOME/.bash_profile --> $HOME/.bashrc --> /etc/bashrc

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    Non-Login shell: 
        |--> $HOME/.bashrc --> /etc/bashrc --> /etc/profile.d/*.sh

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
```


