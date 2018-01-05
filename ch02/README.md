# CH02 Linux 操作基础

本章通过基本概念、Shell 功能操作和常用命令三方面学习 Linux 的基础操作。

* 基本概念
  * bash 的功能
  * Linux 目录层次结构标准
  * 文件命名规则
  * “一切皆文件”、设备文件的使用
  * 文件内容类型（`file`）
  * 文件属性（`stat`）
  * 硬链接与符号链接
  * 正则表达式（BRE、ERE）
* Bash 特性/功能
  * 通配符
  * 命令行补全、命令别名
  * 命令历史、命令行编辑
  * `~` 扩展、`{}` 扩展、命令替换
  * 重定向、管道
  * Shell 变量的定义和变量命名规则
  * 变量替换、强引用和弱引用、避免扩展
  * 命令执行状态、命令组合
  * 当前Shell和子Shell
  * Shell 环境变量与变量作用域
  * 登录 Shell 和 非登录 Shell
  * Shell 环境配置文件
  * bash 的算数运算符
* 常用命令
  * 文件/目录操作命令
    * `ls`、`cd`、`pwd`、`tree`、`mkdir`、`rmdir`
	* `touch`、`cp`、`mv`、`rm`、`ln`
  * 文本显示命令
    * `cat`、`tac/rev`、`more/less`
  * 文本处理命令
	* 文本截取 ：`head/tail`、`cut`、`grep`、`awk`
    * 文本合并 ：`cat`、`paste`
	* 文本替换 ：`tr`、`sed`
	* 文本统计 ：`wc`
	* 文本排序 ：`sort`、`uniq`、`shuf`
    * “三剑客” ：`grep`、`sed`、`awk` 
  * 信息显示命令
  * 文本编辑器 vim


>* [CH02 - 教学指导](guidelines.md)
>* [CH02 - 课堂笔记 2.1](lecture_notes_02-01.md)
>* [CH02 - 课堂笔记 2.2](lecture_notes_02-02.md)
>* [CH02 - 实验指导 2.1](experiment_02-01.md)
>* [CH02 - 实验指导 2.2](experiment_02-02.md)
>* [CH02 - 家庭作业](assignments.md)