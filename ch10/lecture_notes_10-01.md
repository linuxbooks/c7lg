# CH10 - bash 脚本编程

## 条件测试1 - test 或 `[]`

```
[ ]                 test
[ 0 ]               test 0      
[ 1 ]               test 1
[ string ]          test string

[ $UID == 0 ]         比较    [ $UID==0 ]
[ $(id -u) == 0 ]     比较    [ $(id -u)==0 ] 
```

## 使用命令列表替换 if 语句

```
if [ ];   then echo T; fi 
if [ 0 ]; then echo T; fi 
if [ 1 ]; then echo T; fi 
if [ string ]; then echo T; fi 

[ ]   && echo T
[ 0 ] && echo T
[ 1 ] && echo T
[ string ] && echo T
```

```
if [ ];   then echo T; else echo F; fi 
if [ 0 ]; then echo T; else echo F; fi 
if [ 1 ]; then echo T; else echo F; fi 
if [ string ]; then echo T; else echo F; fi 

[ ]   && echo T || echo F
[ 0 ] && echo T || echo F
[ 1 ] && echo T || echo F
[ string ] && echo T || echo F

```

## 使用命令列表替换 if 语句 （续）

```
[ ]   && echo T
[ 0 ] && echo T
[ 1 ] && echo T
[ string ] && echo T

! [ ]   && echo F
! [ 0 ] && echo F
! [ 1 ] && echo F
! [ string ] && echo F

[ ]   && : || echo F
[ 0 ] && : || echo F
[ 1 ] && : || echo F
[ string ] && : || echo F
```


```
~]# help :
:: :
    Null command.

    No effect; the command does nothing.

    Exit Status:
    Always succeeds.
```


```
~]# help true false
true: true
    Return a successful result.

    Exit Status:
    Always succeeds.
false: false
    Return an unsuccessful result.

    Exit Status:
    Always fails.
```



## 条件测试2 - `(())`

```
(( ))                 比较    [ ]
(( 0 ))               比较    [ 0 ]
(( 1 ))               比较    [ 1 ]
(( string ))          比较    [ string ]
```

## 条件测试3 - 根据命令结果状态码测试

```
id -u > /dev/null
echo $?

grep -q '^osmond\>' /etc/passwd || useradd osmond
ping -c1 -W1 8.8.8.8 > /dev/null && elinks --dump http://whatismyip.org || ip r s
```

## 检查字符串变量空值与非空值

*  检查非空
       [ "$name" = "" ]
       [ -z "$name" ]
       [ ! "$name" ]
       [ "X${name}" = "X" ]
*  检查非空
       [ "$name" != "" ]
       [ -n "$name" ]
       [ "$name" ]
       [ "X${name}" != "X" ]

## 检查字符串变量是否为纯数字的方法

```
((n)) 2> /dev/null 
```

```
[ -n "$n"  -a  -z "$(sed 's/[0-9]//g' <<< "$n")" ]
[ -n "$n"  -a  -z "$(egrep -o '[^0-9]+' <<< "$n")" ]
[ -n "$n"  -a  -z "${n//[0-9]/}" ]
[ -n "$n"  -a  "$n" == "${n//[0-9]/}" ]

[[ -n "$n"  &&  -z "$(sed 's/[0-9]//g' <<< "$n")" ]]
[[ -n "$n"  &&  -z "$(egrep -o '[^0-9]+' <<< "$n")" ]]
[[ -n "$n"  &&  -z "${n//[0-9]/}" ]]
[[ -n "$n"  &&  "$n" == "${n//[0-9]/}" ]]
```

## 在 if 、while、until 中使用条件测试

```
~]# help if while until
if: if COMMANDS; then COMMANDS; [ elif COMMANDS; then COMMANDS; ]... [ else COMMANDS; ] fi
    Execute commands based on conditional.

    Exit Status:
    Returns the status of the last command executed.

while: while COMMANDS; do COMMANDS; done
    Execute commands as long as a test succeeds.

    Exit Status:
    Returns the status of the last command executed.

until: until COMMANDS; do COMMANDS; done
    Execute commands as long as a test does not succeed.

    Exit Status:
    Returns the status of the last command executed.
```

举例：从标准输入读取n的值，直至为全数字的整数为止

```
n=
until ((n)) 2>/dev/null
do
  read -p "Pls input a number: "  n
done
###
n=
while ! ((n)) 2>/dev/null
do
  read -p "Pls input a number: "  n
done
```


```
n=
while true
do
  read -p "Pls input a number: "  n
  ((n)) 2>/dev/null && break
done
###
n=
until false
do
  read -p "Pls input a number: "  n
  ((n)) 2>/dev/null && break
done
```

## 循环控制语句与 Shell 特性

```
|while
|until
|for

done|

done<
done<<<
done<<END

done>
done>>
```


## 函数

* 定义
  * 是被命名的的 shell 脚本片段
* 显示
  * declare -F
  * declare -f
  * declare -f funName
* 执行
  * 函数与主程序在一个 shell 内执行
  * 主程序与函数中同名变量是一个变量
  * 在函数中使用 local 定义的变量只在此函数及其调用的函数中起作用
* 返回值
  * 状态返回值  exit N
  * 结果返回值  可通过标准输出传递

```
a=100; b=200

mytest1 () {
  local a
  echo -e "($BASHPID) \t $[a=a+b] \t $a$b"
  mytest2
}
mytest2 () {
  echo -e "($BASHPID) \t $[++a]"
}
declare -f mytest{1,2}

echo $a $b
mytest1
echo $?
echo $a $b
echo $BASHPID
```