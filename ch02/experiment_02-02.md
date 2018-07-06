# 实验指导 2.2 - 文本编辑与处理

>#### 学习目标
> * 熟悉 正则表达式 的使用
> * 进一步熟悉 管道 的使用
> * 掌握整行横向截取：`head` 和 `tail` 命令
> * 掌握按关键字横向截取：`grep` 命令
> * 掌握按列纵向截取：`cut` 命令
> * 掌握纵向和横向合并：`cat` 和 `paste` 命令
> * 掌握文本统计：`wc` 命令
> * 掌握文本比较：`diff` 命令
> * 掌握文本排序：`sort` 命令
> * 掌握随机排列：`sort -R` 和 `shuf` 命令
> * 掌握剔除重复行： `sort -u` 和 `uniq` 命令
> * 掌握文本替换和删除：`tr` 和 `sed` 命令
> * 熟悉文本格式化：`fmt`、`pr`、`column` 和 `fold` 命令
> * 熟悉文本编码转换：`iconv`、`enca`、`convmv` 命令
> * 掌握 `vim` 文件编辑器的使用
> * 掌握 `sed`、`awk` 工具的使用

----

> **提示**： 请以普通用户 student 登录完成下面的操作
>
> **提示**： 所有的文本显示、截取、排序等处理命令默认将处理结果显示在标准输出（屏幕）上，使用输出重定向可将结果保存为文件

----

>**参考**
>
>* 各个命令的手册
>* **正则表达式手册**  man 7 regex
>* <https://www.gnu.org/software/coreutils/manual/coreutils.html> 的 ch3～ch9


## 任务1：按关键字横向截取：`grep` 命令

```
grep root /etc/passwd            ## 显示 /etc/passwd 文件中包含 root 的行
grep root /etc/{passwd,group,crontab,fstab}  ## 显示多个文件中包含 root 的行
grep -n root /etc/passwd         ## 显示 /etc/passwd 文件中包含 root 的行，同时显示 root 出现的行号
grep -c root /etc/passwd         ## 显示 /etc/passwd 文件中包含 root 的行数

grep -i kernel /etc/issue        ## 显示 /etc/issue 文件中包含 kernel 的行，-i 忽略大小写 
grep 'FTP User' /etc/passwd      ## 当匹配字符串包含空格时需用引号括起来
grep -n '(C)' /bin/zcat          ## 当匹配字符串包含括号时需用引号括起来

echo 'echo "scale=10; 4*a(1)" | bc -l' > pi     ## 生成名为 pi 的文件
grep '*'  pi                     ## 在文件 pi 中查找包含字符 * 的行
grep '*' *                       ## 在当前目录的所有文件中查找包含字符 * 的行
grep '\r' /etc/issue             ## 在 grep 中，\ 视为 shell 的转义字符
grep '\r' /etc/issue -o          ## -o 仅显示匹配的字符串而非匹配的行
fgrep '\r' /etc/issue            ## 在 fgrep 中，所有匹配字符串均视为原始字符
fgrep '\r' /etc/issue -o

grep -2 ftp /etc/passwd          ## 显示匹配 ftp 的行，同时显示匹配行的前2行和后2行（-2 等价于 -C 2）
grep -B 2 ftp /etc/passwd        ## 显示匹配 ftp 的行，同时显示匹配行的前（Before）2行
grep -A 2 ftp /etc/passwd        ## 显示匹配 ftp 的行，同时显示匹配行的后（After）2行

grep ^root /etc/passwd           ## 显示 /etc/passwd 文件中以 root 开始的行
grep -c nologin$ /etc/passwd     ## 显示 /etc/passwd 文件中以 nologin 结尾的行数
grep -n '^[a-zA-Z]' /bin/zcat    ## 显示 /bin/zcat 文件中以字母开头的行并显示行号
grep -n ^$ /bin/zcat             ## 显示 /bin/zcat 文件中的所有空行并显示行号
grep -n $ /bin/zcat              ## $是RE，因为每行都有结尾，所以显示了全部文件

grep '\$' /bin/zcat              ## 取消$的RE含义，恢复$字符本身含义
grep \\$ /bin/zcat               ## 取消$的RE含义，恢复$字符本身含义
grep '\[' /bin/zcat              ## 所有RE具有特殊含义的字符均需类似地处理
grep \\[ /bin/zcat
fgrep $ /bin/zcat                ## 在 fgrep 中，所有匹配字符串均视为原始字符
fgrep [ /bin/zcat

grep -v ^# /bin/zcat             ## 显示 /bin/zcat 文件中 不以 # 开始的行
egrep -v '^#|^$' /bin/zcat       ## 显示 /bin/zcat 文件中 不以 # 开始的行且不显示空行
                                 ## egrep 中 可用 ERE（`|`属于ERE）
egrep 'root|student' /etc/passwd    ## 显示 /etc/passwd 文件中包含 root 或 student 的行
egrep '^(root|student)' /etc/passwd ## 显示 /etc/passwd 文件中以 root 或 student 开始的行

strings /bin/ls                  ## 在二进制文件中 查找可打印的字符串
strings /bin/zcat                ## 在文本文件中 查找可打印的字符串
## 使用 grep 过滤出用随机设备生成的字符串中的字母数字，截取20个字符（可作为随机口令）
strings /dev/urandom | grep -o [[:alnum:]] | head -n 20 | tr -d '\n'
## 使用 grep 过滤出用随机设备生成的字符串中的字母数字和除空白之外的特殊字符，截取20个字符（可作为随机口令）
strings /dev/urandom | grep -o [[:graph:]] | head -n 20 | tr -d '\n'

# 避免将查找对象被 bash 视为 grep 的选项
ls --help |grep -l
ls --help |grep '\-l'
ls --help |grep --author
ls --help |grep '\--author'
## 只列当前目录下的子目录 
ls -F | grep /$                  ## 或者 ls -l | grep ^d
## 计算当前目录下的文件数和目录数
ls -l * | grep ^- | wc -l 
ls -l * | grep ^d | wc -l  
## 查看引导信息中关于网卡的信息 
dmesg | grep eth
## 下面的四个目录是伪系统系统，是内存的一部分，每次启动机器会自动构建其数据，且会随系统的运行而变化
$ findmnt |egrep '/(proc|sys|run|dev) '
├─/sys             sysfs         sysfs      rw,nosuid,nodev,noexec,relatime
├─/proc            proc          proc       rw,nosuid,nodev,noexec,relatime
├─/dev             devtmpfs      devtmpfs   rw,nosuid,size=498172k,nr_inodes=124543,mode=755
├─/run             tmpfs         tmpfs      rw,nosuid,nodev,mode=755
```

```
grep -l root /etc/*                       ## 显示 /etc/ 下的哪些文件包含 root
grep -l root /etc/* 2> /dev/null |wc -l
grep -L root /etc/*                       ## 显示 /etc/ 下的哪些文件 不包含 root
grep -lr root /etc/* 2> /dev/null  ## 显示 /etc/ 下的哪些文件包含 root（`-r` 递归参数，即包含所有子目录中的文件）
grep -Lr root /etc/* 2> /dev/null |wc -l  ## （-r 递归参数，即包含所有子目录中的文件）
```


## 任务2：文本替换和删除：`tr` 命令

```
tr 'a-z' 'A-Z' < /etc/passwd            # 将文件中的小写字母转换成与之对应的大写字母
echo "HELLO WORLD" | tr 'A-Z' 'a-z'     # 将通过管道传递来的输入中的大写字母转换成与之对应的小写字母

grep '[()]' /bin/zcat
tr '()' '{}' < /bin/zcat                # 将文件中的 (转换成{； )转换成}
tr '()' '{}' < /bin/zcat |grep [{}]
tr '()' '[]' < /bin/zcat                # 将文件中的 (转换成[； )转换成]
tr '()' '[]' < /bin/zcat |egrep '\[|\]'

grep '[{}]' /etc/rc.local
tr '{}' '()' < /etc/rc.local
tr '{}' '()' < /etc/rc.local |grep '[()]'
tr '{}' '[]' < /etc/rc.local
tr '{}' '[]' < /etc/rc.local |egrep '\[|\]' 
tr '{}' '[]' < /etc/rc.local |grep -v if |egrep '\[|\]'

tr -s ' \n' < /bin/zcat                # 压缩文件中重复字符（空格、换行）为单个字符
echo "Thissss is     a text linnnnnnne." | tr -s ' sn'  # 压缩输入中的重复字符（空格、s、n）为单个字符

## 将文件中的空格和制表符替换成#
## *（星号）可以使 tr 命令重复#足够多次，以使置换字符集的字符个数与被置换字符集的字符个数一致。
tr -s '[:blank:]' '[#*]' < /usr/lib64/python2.7/colorsys.py        # 通过输入重定向为 tr 传递输入
cat /usr/lib64/python2.7/colorsys.py | tr -s '[:blank:]' '[#*]'    # 通过输入管道为 tr 传递输入

## 创建文件的单词列表
## 将文件中 除大小写字母外的字符（-c '[:alpha:]' 表示 '[:alpha:]' 的补集） 都转换成单个换行符。
## *（星号）可以使 tr 命令重复换行符足够多次，以使置换字符集的字符个数与被置换字符集的字符个数一致。
tr -sc '[:alpha:]' '[\n*]' < /bin/zcat
cat /usr/share/doc/nano-2.3.1/faq.html | tr -sc '[:alpha:]' '[\n*]' 
## 将处理结果中的大写字母替换为小写字母，之后再剔除重复的行
tr -sc '[:alpha:]' '[\n*]' < /bin/zcat | tr 'A-Z' 'a-z' |sort -u > wordlist
## 将多个文件纵向合并为一个文件
cat /bin/zcat /usr/share/doc/nano*/*.html > myfile
cat myfile | tr -sc '[:alpha:]' '[\n*]' | tr 'A-Z' 'a-z' |sort -u > wordlist
## 省去中间文件 myfile，通过管道将 cat 命令的输出直接传递给 tr 命令作为其输入
cat /bin/zcat /usr/share/doc/nano*/*.html | tr -sc '[:alpha:]' '[\n*]' | tr 'A-Z' 'a-z' |sort -u > wordlist

## 将 /dev/urandom 作为输入文件生成一个 20*512B （默认1块为512字节） 的输出文件 /tmp/random-file
dd if=/dev/urandom count=20 of=/tmp/random-file
ll /tmp/random-file
## 将输入文件中的所有非打印字符（有效控制字符除外）替换为?（问号），并将结果保存为 /tmp/random-file2
## *（星号）可以使 tr 命令重复?足够多次，以使置换字符集的字符个数与被置换字符集的字符个数一致。
tr -c '[:print:][:cntrl:]' '[?*]' < /tmp/random-file > /tmp/random-file2
## 省去中间临时文件，通过管道将 dd 命令的输出直接传递给 tr 命令作为其输入
dd if=/dev/urandom count=20 2> /dev/null | tr -c '[:print:][:cntrl:]' '[?*]' > /tmp/random-file2
## 将输入文件中的所有非打印字符删除，并将结果保存为 /tmp/random-file3
tr -dc '[:print:]' < /tmp/random-file > /tmp/random-file3
## 省略中间临时文件，通过管道将 dd 命令的输出直接传递给 tr 命令作为其输入
dd if=/dev/urandom count=20 2> /dev/null | tr -dc '[:print:]' > /tmp/random-file3
ll /tmp/random-file*

tr -d [:punct:] < /bin/zcat                  # 输出文件中的除了标点符号（包括一般的标点、所有括号等）之外的内容
echo "hello 1234 world 56" | tr -d '0-9'     # 将通过管道传递来的输入中的数字删除
tr -dc [:alnum:] < /dev/urandom | head -c 20 # 将随机设备生成序列中所有除了字母数值之外的字符删除并截取前20个字符

## 计算1到100之和
echo {1..100} | echo $[ $(tr ' ' '+') ]
echo {1..100} | tr ' ' '\n' | echo $[ $(tr '\n' '+') 0 ] 
echo {1..100} | xargs -n1 | echo $[ $(tr '\n' '+') 0 ]

```


## 任务3：随机排列（“洗牌”）： shuf 

```
cat /etc/passwd
shuf /etc/passwd   ## 以行为单位打乱文件内容的顺序，并在标准输出上显示

shuf -e apple banana cherry lemon orange pear raspberry  ## 将命令参数作为输入
shuf -e apple banana cherry lemon orange pear raspberry -n10 ## `-n` 参数用于指定输出的行数
shuf -e apple banana cherry lemon orange pear raspberry -n10 -r ## `-r` 参数指定输出可以包含重复的行
shuf -i 1-10                ## 将一个数值范围作为输入
shuf -i 1-20 -n10|xargs     ## 此处 xargs 的作用是将以换行为间隔符的输出转换成以空格为间隔符
shuf -i 1-10 -n20 -r|xargs

## 随机生成彩票
shuf -i 0-9 -n7 -r|xargs
echo "七星彩：$(shuf -i 0-9 -n7 -r|xargs)"
echo "排列五：$(shuf -i 0-9 -n5 -r|xargs)"
echo "排列三：$(shuf -i 0-9 -n3 -r|xargs)"

shuf -i 1-33 -n6 |tr '\n' ' ' ; shuf -i 1-16 -n1
shuf -i 1-35 -n5 ; shuf -i 1-12 -n2 |xargs
## 用()将一组命令的输出通过管道同时传递给下个命令(此处为xargs)做其输入
(shuf -i 1-35 -n5 ; shuf -i 1-12 -n2)|xargs 

echo "双色球：$(shuf -i 1-33 -n6|tr '\n' ' ')| $(shuf -i 1-16 -n1)"
echo "大乐透：$(shuf -i 1-35 -n5|tr '\n' ' ')| $(shuf -i 1-12 -n2|xargs)" 

echo "双色球：$(shuf -i 1-33 -n6| sort -n |tr '\n' ' ')| $(shuf -i 1-16 -n1)"      ## 对红球以数字方式排序
echo "大乐透：$(shuf -i 1-35 -n5| sort -n |tr '\n' ' ')| $(shuf -i 1-12 -n2| sort -n|xargs)" 

## 用随机数据填充表格，生成20行表格数据
echo st{01..20} | tr ' ' '\n' > /tmp/tpm-name
shuf -n 20 -e $(echo {A..Z}{a..z}{a..z}) > /tmp/tpm-nick
tr -dc [:alnum:] < /dev/urandom | head -c 200 |fold -w 10 > /tmp/tpm-pass # fold -w 10 表示每行宽度为10个字符
shuf -e male famale -n 20 -r > /tmp/tpm-gender
shuf -i 18-30 -n 20 -r > /tmp/tpm-age
eval echo 13{$(tr -dc 0-9 < /dev/urandom | head -c 180 |fold -w 9|tr '\n' ',')} |xargs -n1 > /tmp/tpm-tel
# tr -dc 0-9 < /dev/urandom | head -c 180 |fold -w 9|tr '\n' ',' 
# 从随机设备删除除数字之外的所有字符|截取前180个字符|以每行9个字符进行换行|将所有换行符替换为逗号
# $(tr -dc 0-9 < /dev/urandom | head -c 180 |fold -w 9|tr '\n' ',')    # 执行命令替换
# echo 13{$(tr -dc 0-9 < /dev/urandom | head -c 180 |fold -w 9|tr '\n' ',')}
# 试图执行大括号扩展，由于｛｝内有命令替换 $()，输出结果仅执行了命令替换，未对大括号进行扩展
# eval echo 13{$(tr -dc 0-9 < /dev/urandom | head -c 180 |fold -w 9|tr '\n' ',')}
# evel 命令首先扫描命令行进行所有的替换（变量替换、命令替换），然后再执行命令，从而扩展了大括号表达式
# |xargs -n1 类似于 |tr ' ' '\n'
# 或 eval echo 13{$(shuf -i 0-9 -n180 -r | tr -d '\n'   |fold -9| tr '\n' ',')} |xargs -n1 > /tmp/tpm-tel
# 或 eval echo 13{$(shuf -i 0-9 -n180 -rz| tr -d '\000' |fold -9| tr '\n' ',')} |xargs -n1 > /tmp/tpm-tel

#echo -e "Name\tNick\tPassword\tGender\tAge\tTel" > usertable
paste /tmp/tpm-{name,nick,pass,gender,age,tel} >> usertable # 将多个文件横向合并（以制表符为列间隔符）
rm /tmp/tpm-{name,nick,pass,gender,age,tel}
cat usertable                  # （因为数据随机产生，所以您的数据与列出的不一致，但数据格式一致）

st01    Syu     LeLJpG9KTU      famale  28      13342675170
st02    Ohn     N30uLpQYh1      famale  19      13332881942
st03    Rmo     fZZHqVMfae      famale  25      13347745308
st04    Mju     CioZLy4Pt0      male    22      13459810354
st05    Biu     aAyFvdSeTu      male    22      13673659969
st06    Psk     EGaJ5OLLzU      male    27      13988407444
st07    Tln     JPNxVoRUmr      male    18      13770716174
st08    Ptu     ve39zRTmiL      male    21      13823448278
st09    Xaw     jW9gIOf1xr      famale  29      13195204321
st10    Ibo     5oskpYfdeY      famale  28      13716142384
st11    Qbx     WKH38Remu8      famale  18      13988542041
st12    Bdj     EhTujFPuaV      famale  28      13364446233
st13    Vel     i5BAGUvFGL      male    21      13557400946
st14    Gdb     xOUc2ArRvd      male    19      13657805803
st15    Nzn     sRcLxaAGMJ      famale  30      13105101475
st16    Jka     RFNSBwG8P8      famale  18      13807347024
st17    Mmt     GbP1yCXdKA      male    20      13253259923
st18    Hli     P4N6MZFhAR      male    18      13282951065
st19    But     GK3Ckrduil      famale  18      13747153535
st20    Nta     laYnn9puAO      famale  24      13935185913


## 用随机数据生成一个简易版的 Apache 访问日志文件
## 随机生成25个IPv4地址
shuf -i 1-254 -n100|sed 'N;N;N;s/\n/./g' > /tmp/tpm-ip
## 随机生成25个日期时间（格式与 Apache 访问日志文件中的日期字段一致）
for d in $(shuf -i $(date +%s -d '-180 days')-$(date +%s -d '+180 days') -n 25) 
 do echo "- - [$(LANG=C date -d "@$d" +'%d/%h/%Y:%T %z')]" ; done > /tmp/tpm-date
paste -d ' ' /tmp/tpm-{ip,date} > logfile # 将多个文件横向合并（-d ' ' 指定以空格为列间隔符）
rm /tmp/tpm-{ip,date} 
cat logfile                   # （因为数据随机产生，所以您的数据与列出的不一致，但数据格式一致）

68.39.177.6 - - [08/Aug/2016:02:00:46 +0800]
225.189.211.29 - - [18/Aug/2016:17:11:31 +0800]
50.155.240.250 - - [30/Jul/2016:01:36:16 +0800]
121.226.58.74 - - [28/Jan/2017:14:47:45 +0800]
107.17.243.35 - - [19/Aug/2016:11:56:29 +0800]
………………

```

## 任务4：sort 命令

```
shuf -e software-v{1,3,10}.{0,1,12} > /tmp/tosort1
# 对文件 /tmp/tosort1 进行排序（依次比较每行的每个字符，默认按ASCII码升序排列）
sort /tmp/tosort1
sort -r /tmp/tosort1   （-r 按降序排列）
# 将包含小数点的数字视为版本号排序，将排序结果使用输出重定向保存为 /tmp/tosort2
sort -V /tmp/tosort1 > /tmp/tosort2
# 若将排序结果重新写回输入文件，可使用 -o 选项指定文件名
sort -V /tmp/tosort1 -o /tmp/tosort1

# 对 usertable 的第5列排序
sort -k5 usertable             # 将从第5列开始到最后一列的内容视为排序对象
sort -k5,5 usertable           # 严格按照第5列排序
sort -k5n usertable            # 对第5列以数字排序（以数字方式排序不会跨列，即 -k5,5n可简作 -k5n）
# 对 usertable 的第5列排序，并剔除重复
sort -k5,5 -u usertable 
# 对 usertable 的第5列排序，若排序结果相同再按第4列排序，并剔除重复
sort -k5,5 -k4,4 -u usertable 
# 对 usertable 的第5列排序，若排序结果相同再按第1列排序
sort -k5,5 -k1,1 usertable
# 对 usertable 的第5列排序，若排序结果相同再按第1列的第3~4字符按数字排序
sort -k5,5 -k1.3,1.5n usertable
# 对 usertable 的第4列以逆序排序，若排序结果相同再按第5列以数字排序
sort -k4,4r -k5n usertable
# 对 /etc/passwd 的第3列以数字方式排序（以:作为列间隔符）
sort -t ':' -n -k3  /etc/passwd
# 对 /etc/passwd 的第5列排序（b用于忽略前导空格或制表符），若排序结果相同再对第3列以数字方式排序
sort -t ':' -k 5b,5 -k 3,3n /etc/passwd
sort -t ':' -n -k 5b,5 -k 3,3 /etc/passwd
sort -t ':' -b -k 5,5 -k 3,3n /etc/passwd

# 对 logfile 按IP地址排序（对以.间隔的四个数字分别以数字方式排序）
sort -t '.' -k 1,1n -k 2,2n -k 3,3n -k 4,4n logfile
# 对 logfile 按日期和时间排序
sort -t ' ' -k 4.9n -k 4.5M -k 4.2n -k 4.14,4.21 logfile
# -k 4.9n 对第4列第9个字符开始（终结于:，以为:不是合法数字字符）的内容以数字方式排序 （年份）
# -k 4.5M 对第4列第5个字符开始（终结于/，以为/不是合法月份字符）的内容以月份方式排序 （月份）
# -k 4.2n 对第4列第2个字符开始（终结于/，以为/不是合法数字字符）的内容以数字方式排序 （日）
# -k 4.14,4.21 对第4列第14个字符开始到第21个字符以ASCII码排序（时间）

# 以降序方式显示使用磁盘空间最多的普通用户的前十名
$ su -
# du -cks /home/*|sort -rn |head -11
# exit
$
# 按内存使用从大到小排列输出进程。
ps -e -o "%C : %p : %z : %a"|sort -k5 -nr
# 按CPU使用从大到小排列输出进程。
ps -e -o "%C : %p : %z : %a"|sort –nr
```

> **参考**： <http://www.cnblogs.com/51linux/archive/2012/05/23/2515299.html>

## 任务5：cut、wc、uniq 命令

```
cat usertable logfile > newfile   # 纵向合并多个文件

cut -f 1,3-5 usertable         # 截取出第1,3,4,5列（默认以tab为列间隔符）
cut -d' ' -f 1,4 logfile       # 以空格为列间隔符截取出第1,4列
cut -d':' -f1,3,6 /etc/passwd  # 以冒号为列间隔符截取出第1,3,6列

cut -d' ' -f4,5 logfile| cut -c14-21 | 截取 logfile 文件中的时间（cut -c14-21截取第14~21个字符）

cut -f5 usertable | sort -n |uniq     # uniq 只剔除连续的重复行，所以使用 uniq 之前应先排序
cut -f5 usertable | sort -n |uniq -c  # uniq -c 计算重复行的个数
cut -f4 usertable | sort -r |uniq -c  # 计算 男女 （第4列为性别）各多少人

wc usertable                   # 显示文件的行数（l）、字数（w）、字符数（c）
wc -l usertable                # 显示文件的行数（l）
wc -L /etc/passwd              # 显示文件最长行的字符数

ifconfig |grep -v ^' '|grep -v ^$| cut -d: -f1  # 显示所有网络接口设备名称
ip a | grep '^[0-9]' | cut -d: -f2              # 显示所有网络接口设备名称
ip a | grep '^[0-9]' | cut -d: -f2 | wc -l      # 显示所有网络接口设备的个数
ip a | grep '^[0-9]' | grep -v lo | cut -d: -f2 | wc -l  # 显示除了 lo 的所有网络接口设备的个数

# 显示 enp0s3 的 IPv4 地址
ifconfig enp0s3 | grep 'inet ' | tr -s ' '| cut -d' ' -f3
ifconfig enp0s3 | grep 'inet ' | tr -dc '[0-9. ]' | tr -s ' ' | cut -d' ' -f2
ifconfig enp0s3 | grep 'inet ' | cut -d: -f2 | tr -s ' ' | cut -d' ' -f1
ifconfig enp0s3 | grep 'inet ' | cut -d: -f2 | awk '{print $1}'

ip addr show enp0s3 | grep 'inet '| cut -d'/' -f1 | tr -s ' ' | cut -d' ' -f3
ip addr show enp0s3 | grep 'inet '| tr -dc '[0-9./]'|cut -d'/' -f1
```

## 任务6：行编辑器：sed

```
# 将每行开始的 st 替换为 ST，并在屏幕显示
sed 's/^st/ST/' usertable
# 将每行开始的 st 替换为 ST，并将替换结果写入文件（-i）
sed -i 's/^st/ST/' usertable
# 将13替换为ac，若一行上有多个13，则全部（g）替换为ac，并在屏幕显示
sed 's/13/ac/g' usertable

# 显示 enp0s3 的 IPv4 地址
ifconfig enp0s3 | grep 'inet ' | sed -e 's/[a-z]//g' -e 's/^[ \t]*//' -e 's/  */ /g' |cut -d' ' -f1
#ifconfig enp0s3|取出包含inet的行|删除所有小写字母、删除所有前导空格或制表符并将多个空格替换成一个|截取第一列

ifconfig enp0s3 | grep 'inet ' | sed 's/[^0-9.:]//g' | cut -d: -f2


## 将文本的奇数行和偶数行合并 
sed '$!N;s/\n/ /'  logfile   # 若不是末行（$!）就将下一行追加读入到缓冲区，并将缓冲区中的换行符替换为空格符
## 生成25个随机IPv4地址 
shuf -i 1-254 -n100 | sed 'N;N;N;s/\n/./g'
## 将文本的第2行和第3行合并 
sed '2,3 N; s/\n/ /' logfile
sed -n '2,3 N; s/\n/ /p' logfile            # 只输出合并的行


## 计算当前用户使用最频繁的10个命令（包括通过管道传递的命令）
## 参考： https://github.com/logotype/useful-unix-stuff
history | sed "s/^[0-9 ]*//" | sed "s/ *| */\n/g" | awk '{print $1}' | sort | uniq -c | sort -rn | head -n 10

```

>#### 参考
> * https://www.gnu.org/software/sed/manual/sed.html
> * [SED 简明教程](http://coolshell.cn/articles/9104.html)
>#### 练习
> 使用 `sed` 命令将 [DevOps实践指南.txt](/assets/exercises/The-DevOps-Handbook.txt) 格式化成 [DevOps实践指南.md](/assets/exercises/The-DevOps-Handbook.md) 。 


## 任务7：awk

```
## 打印所有行（即省略匹配筛选部分）
awk '{print}' usertable                     # 等效于 cat usertable
awk '{print NR,$0}' usertable               # 为每行前添加行号，类似于 cat -n usertable
awk '{print NR "\t" $0}' usertable          # 为每行前添加行号和制表符
awk '{print NR "\t" $1,$3,$6}' usertable 
awk '{print NR "\t" substr($4,2,11),substr($4,11,8)}' logfile   # 使用函数substr取子串
awk -F':' '{print $1,$3}' /etc/passwd       # 指定以冒号作列间隔符，默认的列间隔符为空格或制表符
## 使用正则表达式书写 pattern
awk '/ST[12].*/' usertable                  # 打印正则表达式匹配的行
awk '/ST[12].*/ {print $1,$3,$6}' usertable # 打印正则表达式匹配行的第1,5,6列
awk '/ST[12].*/ {print $1,substr($3,5,4),$6}' usertable # 使用函数substr取子串
awk '/^1.*/ {print NR "\t" $1 "\t" substr($4,2,11),substr($4,11,8)}' logfile
awk -F':' '/^r.*/ {print $1,$4}' /etc/passwd
## 使用关系表达式书写模式
awk 'NR % 2 == 1' usertable                 # 打印所有奇数行
awk 'NR % 2 == 1 {print $1,$3,$6}' usertable
awk 'NR % 2 == 1 {print $1,substr($3,5,4),$6}' usertable 
awk 'NR % 2 == 1 && substr($6,1,3) == '131' {print $1,$3,$6}' usertable
awk 'NR%2==1 && ($5<25 || $4=='male')' usertable
## 使用范围匹配
awk '/ST05/,/[MN].*male/' usertable
awk '/ST05/,NR==10 {print $1,$2,$3,$5}' usertable

# 从 uptime 的输出过滤出时间和三个平均负载字段
uptime |awk -F '[ ,]+' '{print $2" - "$11,$12,$13}'     # 将一个或多个空格或逗号视为列间隔符
# 过滤出 enp0s3 网络接口当前的IPv4地址
ip a s enp0s3|grep 'inet '| awk -F '[ /]+' '{print $3}' # 将一个或多个空格或/视为列间隔符
ifconfig enp0s3|grep 'inet '| awk -F ' +' '{print $3}'  # 将一个或多个空格视为列间隔符
# 显示除了 lo 之外的所有网络接口
ifconfig -a |grep '^\w'|awk '!/lo/{print $1}'           # grep '^\w' 过滤出以字母数字下划线开头的行
ip a|grep '^[0-9]' | awk -F '[ :]' '!/lo/{print $3}'    # 将一个或:视为列间隔符


# 统计 /etc/passwd 的账户数
awk '{count++;print $0;} END{print "user count is ", count}' /etc/passwd  # count未赋初值，默认为0
awk 'BEGIN {c=0;print "[start] count=" c} {c++;print $0;} END{print "[end]user count is", c}' /etc/passwd
# 统计当前目录下的文件占用的字节数
ls -l|grep -v ^d|awk 'BEGIN {size=0} {size+=$5} END{print "[end]size is", size}'
ls -l|grep -v ^d|awk 'BEGIN {size=0} {size+=$5} END{print "[end]size is", size/1024/1024,"M"}' # 以MB为单位
# 统计当前目录下所有12月份文件的字节数
$ LANG=C ls -l /etc | grep -v ^d| awk '$6 == "Dec" { sum += $5 } ; END { print sum }'

## 使用 awk 的数组
# 统计  usertable 文件中各个年龄的人数
# 以年龄为数组下标，对应下标的数组元素值为年龄的个数
awk '{++age[$5]}; END{for (i in age) print i, age[i]}' usertable  
# 查看TCP连接的各种连接状态的连接数
# 以TCP状态为数组下标，对应下标的数组元素值为TCP状态的个数（netstat -nt输出的最后一列$NF为状态）
netstat -n | awk '/^tcp/ {++S[$NF]} END {for(a in S) print a, S[a]}'
netstat -nt| awk '{++S[$NF]} END {for(a in S) print a, S[a]}'
```

> **参考**
>
>* https://www.gnu.org/software/gawk/manual/gawk.html
>* [AWK 简明教程](http://coolshell.cn/articles/9070.html)


## 任务8：文本编辑器 vim

```
vimtutor             # 通过 vimtutor 学习 vim 的使用
```

> **参考**： 
>
>* [Vim Tutorial](https://linuxconfig.org/vim-tutorial)
>* [Learn Vim Progressively](http://yannesposito.com/Scratch/en/blog/Learn-Vim-Progressively/) -- [简明 Vim 练级攻略](http://coolshell.cn/articles/5426.html)
>* [Vim Adventures](http://vim-adventures.com/) -- [VIM大冒险](http://coolshell.cn/articles/7166.html)
>* https://www.linuxtrainingacademy.com/vim-cheat-sheet/
>* https://www.linuxtrainingacademy.com/linux-text-editors-tutorials/





