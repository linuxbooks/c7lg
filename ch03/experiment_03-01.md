# 实验指导 3.1 - 账户管理与口令管理

>#### 学习目标
> * 使用 `useradd`/`usermod`/`userdel` 命令 添加/修改/删除 用户
> * 使用 `groupadd`/`groupmod`/`groupdel` 命令 添加/修改/删除 组
> * 使用 `id` / `group`命令显示 用户/组 信息
> * 使用 `su` / `sg` 或`newgrp` 命令切换 用户/组
> * 使用 `passwd` 命令管理用户口令
> * 使用 `gpasswd` 命令管理组口令和组成员
> * 使用 `chage` 命令设置已存在用户的口令时效策略
> * 修改 `/etc/login.defs` 文件为新建用户设置口令时效策略


## 任务1：显示用户和组管理的相关信息

* 显示当前用户的用户和组信息
* 查看添加用户时读取的默认（范围）值
* 查看使用 useradd 命令添加用户时的默认值
* 列表显示默认系统账户数据库文件及其权限
* 查看 shadows 手册明确每一列的含义

## 任务2：创建用户并为其设置登录口令

* 若当前不是 root 用户，请切换到 root 用户环境
* 查看 useradd 的命令帮助
* 添加名为 toni 的用户并为其设置口令
* 查看 /home/toni 目录自身的权限
* 显示 /home/toni 目录下的所有文件（包括隐含文件）
* 显示指定用户 toni 的用户和组信息
* 显示4个账户文件最后一行的内容，熟悉各个字段的含义

## 任务3：修改用户名和组名

* 将 toni 用户的名字改为 tony，同时将其主目录移动到 /home/tony
* 将 toni 组的名字改为 tony
* 检验更改结果

## 任务4：组成员管理

* 添加名为 leader 的组
* 添加用户 emily（同时会创建同名主组），并指定其附加组为 leader
* 添加用户 jacob，并指定其主组为 leader
* 将用户 tony 的附加组设置为 leader
* 查看 leader 组中的成员
* 添加名为 designer 的组
* 将 tony 用户加入 designer 组，并确保其还是 leader 的组成员 


* 创建 assistant 组
* 创建 5 个用户
* 设置 5 个均为 assistant 组的成员
* 查看 assistant 组中的成员
* 为 assistant 组添加1个新成员
* 从 assistant 组剔除1个成员


>**选择你喜欢的用户名**
>* **!m!** austin victor charles richard alexander jacob michael matthew
>* **!m!** nicholas christopher joshua jason tyler joseph
>* **!f!** alexis amanda tina stella christina hannah alina gloria bella emily 
>* **!f!** brianna samantha hailey ashley kaitlyn madison brandon sarah 


## 任务5： 删除用户和组

* 删除所有你新创建的用户和组（除了 tony）

## 任务6： 口令管理与口令时效

* 以 tony 用户登录并重新设置其口令
* 使用非交互模式将 student 用户的口令设置为 5iCent0S （使用 su - -c）
* 锁定用户 student，显示其口令状态，并尝试以 student 用户身份登录
* 解除对 student 用户的锁定，并尝试以 student 用户身份登录
* 设置新建用户的口令策略，至少每隔90天修改一次自己的口令
* 设置对 student 用户的口令策略，至少每隔60天修改一次自己的口令
* 设置 tony 用户 180 天后到期，并提前7天预警
* 强制用户 student 在首次登录时修改其口令
* 以 student 用户身份登录，并修改其口令

