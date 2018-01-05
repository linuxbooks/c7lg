# 实验指导 15.2 - Tomcat & Apache

>#### 学习目标
* 安装配置 OpenJDK 或 Java SE Development Kit(Oracle) 
* 安装配置独立运行的 Tomcat
* 配置 Tomcat 第二实例
* 配置 Apache 反向代理 Tomcat 
* 配置 Apache 反向代理 usermin 

## 任务1：安装 OpenJDK 和 Tomcat

**要求**
* 安装 java-1.8.0-openjdk 和 tomcat
* 配置独立运行的 Tomcat
* 测试独立运行的 Tomcat
* 安装 Tomcat 的默认 Web应用、管理应用和文档
* 配置 Tomcat 的管理应用
  * 用户 fanny 只能访问 manager 界面
  * 用户 tonny 既可以访问 manager 也可以访问 admin 界面
* 分别以不同用户测试管理界面访问

>**参考**
>* [Install JDK 9](https://www.server-world.info/en/note?os=CentOS_7&p=jdk9&f=1)
>* [Install JDK 8](https://www.server-world.info/en/note?os=CentOS_7&p=jdk8&f=1)
>* [Install OpenJDK 8](https://www.server-world.info/en/note?os=CentOS_7&p=jdk8&f=2)


## 任务2：配置 Tomcat 第二个实例

**要求**
* 配置可由 systemd 管理的第二个 Tomcat 实例


## 任务3：Apache 反向代理

**要求**
* 配置 Apache 反向代理 Tomcat 默认实例
  * 不对 /docs 的URI访问进行反向代理
  * 使用 AJP 协议反向代理 Tomcat 的默认实例
* 配置 Apache 反向代理 Tomcat 第二个实例
* 配置 Apache 反向代理 usermin （https://localhost:20000）