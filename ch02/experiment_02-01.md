# 实验指导 2.1 - 命令行操作基础

>#### 学习目标
> * 熟悉 Linux 文件系统的层次结构
> * 熟悉 bash 的 通配符、命令补全、命令历史、命令别名 的使用
> * 掌握 `ls` , `pwd` , `cd` , `mkdir` , `rmdir` , `tree` 等目录操作命令
> * 掌握 `touch` , `cp` , `mv` , `rm` , `ln` , `file` 等文件操作命令
> * 掌握 `cat` , `more` , `less` , `head` , `tail` 等文本文件显示命令
> * 掌握 bash 的 变量定义和引用 `${}`、变量作用域
> * 掌握 bash 的 命令替换 `$()` 的使用
> * 掌握 bash 的 整数运算 `$[]` 和 `$(())` 的使用
> * 掌握 bash 的 重定向和管道 的使用
> * 掌握 bash 的 环境变量和环境配置文件 的使用

----

> **提示**： 请以普通用户student登录完成下面的操作

## 任务1： 熟悉 Linux 文件系统层次结构

```
$ ls -l /
$ tree -L 1 /
/                                 
├── bin -> usr/bin            # CentOS7中，/bin 链接至 /usr/bin 
├── boot          # 包含系统启动过程所需的文件       
├── dev               # 是一个伪文件系统，只存在内存中。包含设备文件，供用户访问硬件设备
├── etc           # 包含系统配置文件
├── home          # 普通用户主目录的父目录，如普通用户 student 的主目录为 /home/student
├── lib -> usr/lib            # CentOS7中，/lib 链接至 /usr/lib
├── lib64 -> usr/lib64        # CentOS7中，/lib64 链接至 /usr/lib64
├── media         # 包含可移动介质，如CD/DVD光盘 或 USB 的挂载点
├── mnt           # 是临时挂装文件系统的挂载点
├── opt           # 存放第三方应用程序
├── proc              # 是一个伪文件系统，只存在内存中。它以文件系统的方式为用户和程序访问系统内核数据的操作提供接口
├── root          # 超级用户 root 的主目录
├── run               # 是一个伪文件系统，只存在内存中。CentOS7中，整合了旧版本的 /var/run 和 /var/lock
├── sbin -> usr/sbin          # CentOS7中，/sbin 链接至 /usr/sbin
├── srv           # 存放各种服务的数据资料
├── sys               # 是一个伪文件系统，只存在内存中。与 /proc 类似，同时失实现了 Linux 统一设备模型
├── tmp           # 存放临时文件目录，10天内未访问、更改和修改的文件会被删除
├── usr           # 包含系统安装的程序、工具、库文件等，bin子目录下的所有用户皆可执行；sbin 下的仅 root 能执行
└── var           # 包含动态变化的数据和文件，如数据库、缓存数据、日志文件、网站内容等
```


## 任务2： 目录操作命令

```
pwd
cd /
ls -l 
ls -l /etc /var
ls -lR /etc
tree /etc
ls -ld /etc 
cd
mkdir abc bcd cde
mkdir -p def/gh/ij   # mkdir -p 用于创建目录树
tree
rmdir abc
rmdir def            # rmdir 只能删除空目录
rm -d bcd            # rm -d 用于删除空目录
ls
rm -ri cde           # rm -r 可以递归地删除目录中的所有内容，包括其中的子目录、子目录的子目录……
rm -rf def           # rm -r 可以递归地删除目录中的所有内容，包括其中的子目录、子目录的子目录……
ls
```

>**强制执行与交互确认执行**：
>
>* `-f` 参数表示强制执行
>* `-i` 参数表示以交互的确认方式执行
----
>**防止误删除**
>
>* https://linuxtoy.org/archives/rm-protection.html
>* https://github.com/alanzchen/rm-protection#comparison-with-alternative-methods

## 任务3： 绝对路径与相对路径

```
ls /etc/passwd                # 使用绝对路径
cd /etc                       # 使用绝对路径
pwd                           # 显示当前路径
ls passwd                     # 使用相对路径
ls /usr/share/man             # 使用绝对路径

^man^doc                      # 将上一条命令中的 man 替换为 doc
cd <Esc><.>                   # 按下<ESC>键再按下<.>键 用于复制上一条命令的最后一个参数 （也可同时按下 <Alt+.>）

pwd
ls zip<TAB>                   # 使用相对路径
ls ../man/man1                # 使用相对路径
ls ../../src                  # 使用相对路径
cd ../..                      # 使用相对路径
pwd
cd -                          # 进入前次进入的目录
pwd
cd ~                          # 使用绝对路径进入用户主目录，等同于不带任何参数的 cd 命令
                              # 若登录用户为 student，则 ~ 会扩展为 /home/student
```

>**提示**：绝对路径与相对路径的概念适用于所有需要操作目录/文件的命令


## 任务4： 命令补全

```
tz<TAB>                       # 当前以tz开头的命令只有tzselect一个，所以自动补全为 tzselect
pas<TAB><TAB>                 # 两次按下<TAB>键可以列出所有以pas开头的命令
passwd -<TAB><TAB>            # 两次按下<TAB>键可以列出所有当前命令可用的参数
ls /etc/pa<TAB><TAB>          # 两次按下<TAB>键可以列出/etc目录下所有以pa开头的文件或目录
echo $P<TAB><TAB>             # 两次按下<TAB>键可以列出以P开头的所有变量
echo $PA<TAB>                 # 当前以PA开头的变量只有PATH一个，所以自动补全为 PATH
```

> **提示**：<TAB> 可以补全命令、路径和/或文件名、命令参数、变量（以$开头）、用户名（以~开头）


>**命令行编辑**
> 
>* Ctrl-b —— 左移一个字符（左方向键）
>* Ctrl-f —— 右移一个字符（右方向键）
>* Esc-b  —— 左移一个单词 
>* Esc-f  —— 右移一个单词
>* Ctrl-a —— 移动到行首
>* Ctrl-e —— 移动到行尾
>
>* Ctrl-u —— 删除到行首
>* Ctrl-k —— 删除到行尾

## 任务5：命令历史

```
history       # 显示命令历史表
!!            # 执行最近一次执行过的命令，等效于 <Up>键
sudo !!       # 使用 sudo 执行最近一次执行过的命令

!15           # 执行命令历史表中的标号为15的命令
!-15		  # 执行15个命令之前的那个命令

!ls           # 执行最近一次执行过的以 ls 开头的命令
!?abc		  # 执行最近一次执行过的包含abc的命令
```

>**提示**：可以使用 Up、Down 方向键遍历命令历史表

## 任务6：复制、移动、删除文件

```
cp /etc/passwd .        # 将 /etc/passwd 文件复制到当前目录
mkdir myfiles           # 创建空目录 myfiles
cp passwd myfiles       # 将当前目录下的 passwd 文件复制到 myfiles 目录下
mv passwd mypasswd      # 将当前目录下的 passwd 文件改名为 mypasswd
mv mypasswd myfiles     # 将当前目录下的 mypasswd 文件移动到 myfiles 目录下
rm myfiles/passwd       # 删除 myfiles 目录下 的 passwd 文件
mv myfiles files        # 将目录 myfiles 改名为 files
rm files/mypasswd       # 删除目录 files 下的 mypasswd 文件

cp /etc/issue /usr/share/doc/mutt<TAB>/samples/iconv/iconv.glibc-2.1.3.rc \# 续行符 \ 表示下一行是当前行的延续
   files                                                                   # 一次性将多个文件复制到指定目录
mkdir doc
cd files
mv issue iconv.glibc-2.1.3.rc ../doc                      # 一次性将多个文件移动到指定目录
cd
rm doc/issue doc/iconv.glibc-2.1.3.rc                     # 一次性删除多个文件

## 使用 cp 命令复制目录树
#   -R, -r, --recursive     递归地复制目录
#   -a, --archive           等价于 -dR --preserve=all
#   -d                      等价于 -P --preserve=links，即不跟随的符号链接且保留硬链接
#   -P, --no-dereference    不跟随源文件的符号链接
#   -p                      等价于 --preserve=mode,ownership,timestamps
#   --preserve[=ATTR_LIST]  保留文件或目录的属性（默认为:  mode[权限],ownership[属主],timestamps[时间戳]）, 
#                           还可以指定文件或目录的其他属性: context[安全上下文], links[链接], xattr[扩展属性]
#                           all 表示尽可能地保留文件或目录的所有属性

cp -r /etc .                # 将 /etc 整个目录树（-r表示递归）复制到当前目录（仅复制有权读取的文件）
ll etc                      # 已复制的文件时间改为复制时的时间；文件的属主和组改为执行cp命令的用户
cp -a /etc .                # 将 /etc 整个目录树（-a表示归档）复制到当前目录（仅复制有权读取的文件）
ll etc                      # 已复制的文件时间保留源文件的时间、权限；文件的属主和组改为执行cp命令的用户
rm -rf etc                  # 强制删除当前目录下的 etc 目录
```

## 任务7：命令别名

```
l.
ll
which ll
alias                    # 显示当前可用的所有别名
ls
\ls                      # 使用 ls 命令而非 ls 别名
alias ren=mv             # 设置别名 ren
cd /etc
cd..
alias cd..='cd ..'       # 设置别名 cd.. ，等号右侧若包含空格应使用引号括起
cd..
cd
unalias cd..             # 取消别名 cd..
cd..
```

>**参考**：
>
> https://www.linuxtrainingacademy.com/23-handy-bash-shell-aliases-for-unix-linux-and-mac-os-x/

## 任务8： bash 变量定义、引用与显示

```
u=Unix           # 变量赋值
l=Linux          # l是字母不是数字，$1 有特殊含义且不能直接赋值
disto=CentOS
ver=7

ul="$u and $l"   # 等号右侧若包含空格需用引号括起来，双引号会扩展出变量的值
lu='$l and $u'   # 等号右侧若包含空格需用引号括起来，单引号不会扩展出变量的值
echo ${ul} ${lu}
echo $ul $lu

echo $l is a type of $u.
echo $disto$ver a type of $l.

help echo        # 显示 shell 内置命令 echo 的帮助信息

echo -n $l is a type of $u,
echo $disto$ver a type of $l.

echo "$disto$ver a type of $l."     # 双引号内的变量引用会扩展出变量的值
echo -e "$l is a type of $u, \n $disto$ver a type of $l."
echo -e "$ul \t\t $lu"

## 防止变量被扩展
echo '$disto$ver a type of $l.'     # 单引号内的变量引用不会扩展出变量的值
echo \$disto$ver a type of $l.      # \$ 还原 $ 字符本身含义，不会扩展出变量的值
echo "$disto\$ver a type of $l."    # \$ 还原 $ 字符本身含义，不会扩展出变量的值

l=disto                             # 变量可以再次赋值
echo ${!l}                          # 变量的间接引用

echo "I'm a student." 
echo Je t\'aime.

ilu="Je t'aime."
echo $ilu

echo $RANDOM  $PATH                 # 显示环境变量的值
env                                 # 显示所有环境变量
```

## 任务9： 特殊文件名

```
cd
mkdir My Document
ll
rmdir My Document
mkdir 'My Document'        # 命令操作对象包含空格，可使用单引号括起来
ll
rmdir 'My Document'
mkdir My\ Document         # 使用转义符\ 将空格还原为空格字符本意而非Shell命令行中的命令参数间隔符
ll -d My\ Document

touch un gars, une fille
ll
rm  un gars, une fille
touch 'un gars, une fille'
ll
mkdir TVseries
mv 'un gars, une fille' TVseries

touch 'a&b'  b\&a           # & 在 Shell 中有特殊含义，表示后台执行
touch 'a$b'  b\$a           # $ 在 Shell 中有特殊含义，表示引用变量的值
touch 'a*b'  b\*a           # * 在 Shell 中有特殊含义，表示通配任意个任意字符
ls

touch ./-abc                # 以-开头的文件应使用路径前缀（绝对路径、相对路径均可）
mkdir ~/-ABC                # 以-开头的目录应使用路径前缀（绝对路径、相对路径均可）
ls
```

## 任务10： 文件通配符

```
fruits="coconut cherry grape fig lemon pear plum peach papaya cranberry blueberry"
touch $fruits
touch apple banana orange raspberry
touch apple1 banana2 orange3 raspberry4
touch $RANDOM $RANDOM $RANDOM $RANDOM $RANDOM
mkdir apple$RANDOM banana$RANDOM orange$RANDOM raspberry$RANDOM
touch applePI bananaPI orangePI raspberryPI
touch a${RANDOM}x b${RANDOM}y c${RANDOM}x d${RANDOM}x e${RANDOM}z
ls
```

```
ls *                 # 列出所有文件或目录，不包含隐含文件（即以.开头的文件）
ls .*                # 列出所有隐含文件或目录
ls *berry            # 列出所有以berry结尾的文件
ls ?????             # 列出名字为5个字符的文件或目录
ls ?p*               # 列出名字中第二个字符为p的文件或目录
ls ??p*[0-9]         # 列出名字中第三个字符为p且最后一个字符为数字的文件或目录
ls [abc]*            # 列出名字以a或b或c开头的文件或目录
ls [!abc]*           # 列出名字不以a或b或c开头的文件或目录
ls *PI               # 列出名字以PI结尾的文件或目录
ls *e*               # 列出名字中包含e的文件或目录
ls *[123]            # 列出名字以1或2或3结尾的文件或目录
ls *[0-9]*           # 列出名字中包含数字的文件或目录
ls [a-z]*[xyz]       # 列出名字以小写字母开头且以x或y或z结尾的文件或目录
ls *[!0-9]           # 列出名字不以数字结尾的文件或目录
ls [a-z0-9]*[!0-9]   # 列出名字以小写字母和数字开头且不以数字结尾的文件或目录

mv *[0-9] files
cp [A-Za-z0-9]*[a-z] files
rm *[0-9]* 
rm $fruits
rm -rf *\$* *\&* *\** ./-*
```

>**使用字符类型进行匹配**
>
>* [[:lower:]] 等价于 [a-z]
>* [[:upper:]] 等价于 [A-Z]
>* [[:alpha:]] 等价于 [a-zA-Z]
>* [[:digit:]] 等价于 [0-9]
>* [[:alnum:]] 等价于 [a-zA-Z0-9]
>* [[:cntrl:]] 任何一个控制字符
>* [[:blank:]] 任何一个 空格符 或 制表符（呈水平排列的空白字符）
>* [[:space:]] 任何一个 空格符 或 制表符 或 换行符 或 换页符 或 回车符（呈水平或垂直排列的空白字符）
>* [[:print:]] 任何一个可打印字符，包括空格
>* [[:graph:]] 任何一个可打印字符，不包括空格
>* [[:punct:]] 除了空格和字母数字之外的任何一个可打印字符（标点符号）

----

>**参考**
>
>* $ man 7 glob

## 任务11：大括号扩展

```
ll *PI
rm {apple,banana}PI      # 等效于 rm applePI bananaPI
mv raspberry{PI,}        # 等效于 mv raspberryPI raspberry
cp orangePI{,.bak}       # 等效于 cp orangePI orangePI.bak
ll *PI*
rm *PI*

touch {a..e}${RANDOM}        # 等效于 touch a${RANDOM} b${RANDOM} c${RANDOM} d${RANDOM} e${RANDOM}
ls [a-e]*
touch {m,n}{1,2,3}           # 扩展方式类似于离散数学中集合的笛卡尔积运算
ls [mn]*
touch {p,q}{1{a,b,c},2,3}    # {}可以嵌套
ls [pq][123]*
rm [a-e]* [mn]* [pq][123]*

cd
touch FRIENDS-season{1..10}-episode{1..24}.mp4  # 模拟下载了一部10季每季24集的电视剧
ls FRIENDS*
mkdir -p TVseries/FRIENDS/season{01..10}        # 创建并按照季目录进行整理
tree TVseries
mv FRIENDS-season1* TVseries/FRIENDS/season01
cd TVseries
mv ../FRIENDS-season2* FRIENDS/season02
cd FRIENDS/season03 
mv ~/FRIENDS-season3* .
cd ..
mkdir todo
mv ~/FRIENDS* todo
tree
cd
```

## 任务12：文件类型

```
ll -d /bin /var /etc/passwd /usr/bin/passwd /bin/zcat # 注意输出各行的第一个字符
ll /dev/sda{,1}  /dev/{console,tty0,ttyS0,null,zero,urandom}
```

```
file /bin /var /etc/passwd /usr/bin/passwd /bin/zcat 
file /dev/sda{,1}  /dev/{console,tty0,ttyS0,null,zero,urandom}
file *
```

>**参考**
>
>* [文件类型与其特征码](http://www.garykessler.net/library/file_sigs.html)


## 任务13： 链接文件

```
touch hello 
ll hello
ln hello bonjour          # 创建名为 bonjour 的硬链接
ll hello bonjour          # 注意输出第二列（以空格为间隔）数字的变化
ln bonjour ciao           # 创建名为 ciao 的硬链接        
ll hello bonjour ciao     # 注意输出第二列（以空格为间隔）数字的变化

rm hello
ll hello bonjour ciao     # 注意输出第二列（以空格为间隔）数字的变化
rm bonjour
ll hello bonjour ciao     # 注意输出第二列（以空格为间隔）数字的变化
rm ciao
ll hello bonjour ciao

touch hi
ln -s hi salut            # 创建名为 salut 的符号链接 
ln -s hi ciao             # 创建名为 ciao 的符号链接
ll hi salut ciao          # 注意输出中第一个文件类型字符
rm salut                  # 删除符号 salut 链接文件
ll hi salut ciao
rm hi                     # 删除被符号链接的文件 hi
ll hi salut ciao          # 符号链接文件 ciao 将成为死链

ll -d doc
mv doc mydoc
ln -s /usr/share/doc doc  # 对目录创建符号链接
cd doc
ll
cd
```

## 任务14：命令替换

```
echo "This system's name is $(hostname)."
echo "I am `whoami`"

# 防止命令替换被扩展
echo 'This system's name is $(hostname).'
echo "This system's name is \$(hostname)."
echo This system's name is \$(hostname).

touch backup_$(date +"%F")
rpm -ql $(rpm -qf $(which cp))         # $() 形式的命令替换可以嵌套
```

## 任务15： bash 整数运算

```
echo 10*2*5                          # shell 默认将字面常量视为字符串而非数字

echo $[10*2*5]                       # 使用 $[] 进行整数运算
echo $((10*2*5))                     # 使用 $(()) 进行整数运算

length=10
width=2
height=5

volume=$length*$width*$height        # shell 默认将变量视为字符串而非数字
echo $volume

volume=$[$length*$width*$height]
echo $volume
volume=$[length*width*height]        # 在 $[] 中的变量引用可以省略 $前缀
echo $volume
volume=$(($length*$width*$height))
echo $volume
volume=$((length*width*height))      # 在 $(()) 中的变量引用可以省略 $前缀
echo $volume

((volume=length*width*height))       # 可直接在 (()) 中进行赋值【c语言中的表达式都可以放在(())中】
echo $volume
```

## 任务16： 文本显示

```
cat /etc/passwd                      # 滚屏显示文本
nl /etc/passwd                       # 滚屏显示文本并显示行号，等同于 cat -n /etc/passwd

tac /etc/passwd                      # 纵向反转文本并显示
rev /etc/passwd                      # 横向反转文本并显示

more /etc/passwd                     # 分屏显示文本（不可回翻）【回车向下滚动一行，空格向下滚动一屏】
less /etc/passwd                     # 分屏显示文本（可回翻）【回车向下滚动一行，空格向下滚动一屏】

head /etc/passwd                     # 显示前10行
head -n 5 /etc/passwd                # 显示前5行，可简写为 head -5 /etc/passwd
head -c 5 /etc/passwd                # 显示前5个字符

tail /etc/passwd                     # 显示最后10行
tail -n 5 /etc/passwd                # 显示最后5行，可简写为 tail -5 /etc/passwd
tail -n +5 /etc/passwd               # 显示从第5行到文件尾
tail -c 5 /etc/passwd                # 显示最后5个字符
```

## 任务17：管道

```
ls -Rl /etc | less
ls -t | head -5 
tac /etc/passwd | head               # tail /etc/passwd | tac
tail -n +5 /etc/passwd | head        # 显示第5~15行

echo 'abcd 1234'|rev
echo '上海'|rev
echo '上海自来水来自海上'|rev

date +%s
date +%s | sha256sum
date +%s | sha256sum | base64        # base64 --help
date +%s | sha256sum | base64 | head -c 32   # 生成一个32位的随机口令

# 显示当前目录列表的同时将输出结果保存于文件 saved-output
ll | tee /tmp/saved-output
# 显示当前目录列表的同时将输出结果追加保存于文件saved-output并将ll的输出结果以邮件方式发送给 root，邮件标题为ll
ll | tee -a /tmp/saved-output | mail -s ll root
more /tmp/saved-output
```

## 任务18：使用 bc 进行数值运算

```
echo "1.23+4.5/6.7*8.9-10^2" | bc

echo "obase=2; 30" | bc             # obase=2 将输出基数设置为2（默认为10）；计算十进制数 30 的二进制数
echo "ibase=8; 30" | bc             # ibase=8 将输入基数设置为8（默认为10）；计算八进制数 30 的十进制数
echo "ibase=8; obase=16; 30" | bc   # 计算八进制数 30 的十六进制数

pi=3.14
r=1.23
area=$pi*$r*$r
echo "pi=$pi   --   r=$r   --   area=$area"

pi=$(echo "scale=10; 4*a(1)" | bc -l)  # scale=10设置输出的小数点后的保留位数；-l 启用算数函数库；pi=4*atan(1)
echo "$pi*$r*$r" | bc
area=$(echo "$pi*$r*$r" | bc)
echo "pi=$pi   --   r=$r   --   area=$area"
```

## 任务19：输出重定向

```
## 覆盖式
ls -Rl /etc  > /tmp/saved-output        # 标准输出重定向
less /tmp/saved-output
ls -Rl /etc 2> /tmp/saved-outerr        # 标准错误输出重定向
cat /tmp/saved-outerr
ls -Rl /etc  > /tmp/saved-output 2> /dev/null ; less /tmp/saved-output   # 多个命令放在一行上顺序执行用;间隔
ls -Rl /etc &> /tmp/saved-outputanderr ; less /tmp/saved-outputanderr    # 标准输出和错误输出同时重定向

## 追加式
echo "****************" >> /tmp/saved-output
ll >> /tmp/saved-output
echo "****************" >> /tmp/saved-outerr
ls -Rl /etc 2>> /tmp/saved-outerr ; cat /tmp/saved-outerr
echo "****************" >> /tmp/saved-outputanderr
ls -Rl /etc &>> /tmp/saved-outputanderr
ls -Rl /etc >> /tmp/saved-outputanderr 2>&1
```

## 任务20：输入重定向

```
cat < /etc/passwd

echo "This system's name is $(hostname)." > /tmp/mymail
echo "I am `whoami`" >> /tmp/mymail
echo >> /tmp/mymail    # 在 /tmp/mymail 尾部加添空行
ll  >> /tmp/mymail
mail -s test $USER < /tmp/mymail

tr -dc [:print:] < /dev/urandom | head -c 32  # 以系统随机字符设备作为tr命令的输入，生成一个32位的随机口令

cat <<END   # 将 END 之间的内容作为 cat 命令的输入
aimer
love
END
<Ctrl+D>

su -
cat >> /etc/hosts <<_END # 将 _END 之间的内容作为 cat 命令的输入，并以追加方式输出重定向到文件 /etc/hosts
192.168.0.77   web1
192.168.0.88   db1
192.168.0.99   win1
_END
exit

line=$(ls)
cat <<< $line              # 变量值做输入重定向
```

## 任务21： Shell变量作用域

```
## 1-为 var1 赋值
$ var1=UNIX
## 1-为 var2 赋值
$ var2=Linux
## 1-将变量 var2 的作用范围设置为全局
$ export var2
## 1-直接为全局变量 var3、var4 赋值
$ export var3=centos var4=ubuntu
## 1-在当前Shell中显示四个变量的值
$ echo $var1 $var2 $var3 $var4
UNIX Linux centos ubuntu
## 1-进入子Shell
$ bash
## 2-显示 var1 的值
## 2-由于var1在上一级Shell中没有被声明为全局，所以在子Shell里没有值
$ echo $var1
 
## 2-显示 var2、var3、var4 的值
## 2-由于这三个变量在上一级Shell中被声明为全局变量，所以在子Shell里仍有值
$ echo $var2 $var3 $var4
Linux centos ubuntu
## 2-在当前Shell中将 var2 设置为局部变量
$ export -n var2
## 2-在当前Shell中 var2 仍有值
$ echo $var2
Linux
## 2-进入孙子Shell
$ bash
## 3-由于 var2 在当前Shell的父Shell中已经设置为局部变量，所以在孙子Shell里没有值
## 3-当然，var1 在当前Shell的祖父Shell中就是局部变量，所以在当前Shell里没有值
$ echo $var1 $var2
 
## 3-由于var3和var4 在当前Shell的祖父Shell中设置为全局变量，
## 3-在当前Shell的父Shell中又没有变更，所以在当前Shell里仍有值
$ echo $var3 $var4
centos ubuntu
## 3-返回父Shell
$ exit
## 2-显示当前Shell中变量的值
$ echo $var2 $var3 $var4
Linux centos ubuntu
## 2-修改变量 var3 的值
$ var3=centos7.1
## 2-显示变量 var3 的值
$ echo $var3
centos7.1
## 2-返回父Shell
$ exit
## 1-已在父Shell中
$ echo $var1 $var2 $var3 $var4
UNIX Linux centos ubuntu
```

## 任务22：环境变量使用

```
echo $HISTIGNORE
export HISTIGNORE='pwd:ls:ll'         # 不将 pwd和ls和ll 记入命令历史
echo $HISTCONTROL
export HISTCONTROL='ignorespace:ignoredups'  # ignorespace 表示不将以空格开头的行记入命令历史
                                             # ignoredups 表示不将连续的重复行记入命令历史
											 # erasedups  表示剔除整个命令历史中的重复条目
echo $HISTSIZE $HISTFILESIZE
export HISTSIZE=10000              # 设置内存命令历史的行数
export HISTFILESIZE=10000          # 设置命令历史文件（$HOME/.bash_history）的行数
```

```
$ date
2016年 09月 27日 星期二 19:20:25 CST
$ LANG=C date                           # 使用通用语言（英语）显示命令输出结果，或 LANG=en_US.utf8 date
Tue Sep 27 19:20:29 CST 2016
$ TZ=Europe/Paris date                  # 显示巴黎的当前时间
2016年 09月 27日 星期二 13:20:48 CEST
$ LANG=C TZ=Europe/Paris date           # 使用英语显示命令输出结果
Tue Sep 27 13:20:57 CEST 2016	
$ LANG=fr_FR TZ=Europe/Paris date       # 使用法语显示命令输出结果
mar. sept. 27 13:21:06 CEST 2016
```

## 任务23：设置用户自己的工作环境

```
echo "export HISTIGNORE='pwd:ls:ll'" >> ~/.bash_profile
echo "export HISTCONTROL='ignorespace:ignoredups'" >> ~/.bash_profile
echo "export HISTSIZE=10000" >> ~/.bash_profile
echo "export HISTFILESIZE=10000" >> ~/.bash_profile

echo '
alias cp="cp -i"
alias rm="rm -i"
alias mv="mv -i"
alias cd..="cd .."
alias cd...="cd ../.."
' >> ~/.bashrc
```
