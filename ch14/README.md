# CH14 Apache 基础

本章讲解基于 Apache 的 Web 服务配置。

* Web 相关组件
  * 统一资源标识符 URI
  * Web 客户和 Web 服务器
  * 超文本传输协议 HTTP
  * Web 缓存和 Web代理
  * Cookie 和 Session 机制
  * Web 内容的构建组件
* HTTP 协议
  * HTTP 协议特点
  * HTTP 协议版本
  * HTTP 的连接方式
  * HTTP 的请求方法
  * HTTP 的协议头
  * HTTP 的响应代码
* Apache 简介
  * Apache 的特性
  * Apache 的结构
  * Apache 的运行模式
    * 多进程模型 **Profork MPM**
    * 多进程多线程混合模型 **Worker MPM** 和 **Event MPM**
* 管理 Apache
  * 安装和启动 Apache 2.4
  * 使用 `apachectl` 管理 Apache 服务
  * 使用 `Include` 指令分割配置
  * 使用基于目录的 `.htaccess` 文件分割配置
  * 使用 `ab` 工具实现 Web 性能测试
* Apache 的基本配置
  * 使用 `Alias` 指令设置“虚拟目录”
  * 配置基于主机的访问控制
  * 配置基于用户的认证和授权
  * 管理认证口令文件/认证组文件
  * 配置每个用户的 Web 站点
  * 重定向和重写
* Apache 虚拟主机
  * 配置基于 IP 和/或 端口的虚拟主机
  * 配置基于域名的虚拟主机
  * 配置虚拟主机的分离日志及其日志滚动
* Apache 的安全配置
  * 安装配置 `mod-ssl` 模块实现 HTTPS 协议的 Apache 虚拟主机
  * 安装配置 `mod-evasive` 模块防止 DoS 攻击


>* [CH14 - 教学指导](guidelines.md)
>* [CH14 - 实验指导](experiment_14-01.md)
>* [CH14 - 家庭作业](assignments.md)