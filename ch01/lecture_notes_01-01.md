# CH01U01 - Linux 简介与理念

## 四种软件模式

* 商业软件（Commercial Software）
由开发者出售拷贝并提供软件技术服务，用户只有使用权，但不得进行非法拷贝、扩散、反编译和修改
* 共享软件（Shareware）
由开发者提供软件试用程序拷贝授权，用户在使用该程序拷贝一段时间之后，必须向开发者缴纳使用费，开发者则提供相应的升级和技术服务
* **自由软件**（Freeware/Free Software/Libre Software）
使用者有使用、复制、散布、研究、改写、再利用该软件的自由
* **开源软件**（**OSS**，Open Source Software）
软件的源代码向所有人公开的软件

## 自由软件的四项自由条款

* 软件必须自由用于任何目的
* 源代码必须公开，他人可以研究其工作原理
* 软件必须能够被自由再发行
* 任何人都可以自由修改软件

## 开源软件的特点

* 开放源代码软件一般是免费发布的，可以自由下载，无需缴纳 License 费用
* 使用 “集市”式的开发模式使得其通常有着比封闭源代码软件更高的质量
* 用户可以得到软件的源代码，更容易根据自己的特殊要求，进行定制
* 开放源代码软件的生命周期不依附于某个公司，因此有更强的生命力
* 授权条款必须被继承，获得授权的发行商也需要遵守同样条款

>* [《大教堂与市集》（The Cathedral and the Bazaar）](https://book.douban.com/subject/3709579/)
>* [《大教堂与市集》-- 维基语录](https://zh.wikiquote.org/wiki/大教堂和市集)

## 自由软件与开源软件的区别

* 开源软件未必都是自由软件(取决于其授权协议)，自由软件必定满足开源软件
* 绝大多数开源软件也匹配自由软件的定义。比如，遵守GPL和BSD许可协议的软件都是开放的并且是自由的（FOSS/FLOSS）
* 开源是一种方法，自由是一种精神

>* **FOSS** （Free Open Source Software）
>* **FLOSS** （Free-Libre Open Source Software）

>* **自由软件运动**是基于哲学思想（有时被称为所谓黑客文化）的理想主义运动
>* **开放源代码运动**是由程序工程师及其它电脑用户参与的，主要注重程序本身的质量提升。


## 自由软件基金会（Free Software Foundation，FSF）

* 是倡导自由软件和开源软件的国际性非盈利组织
* 是一个免税的为自由软件发展的慈善团体
* 接受捐款，但其大部分收入常常来自销售自由软件的拷贝，和其它相关的服务
* 对于国际开源社区的形成和发展起到了重要的推动作用
* 创始人是 **Richard M. Stallman**
* FSF 开展的 “GNU Project” 催生出数量众多的自由软件，过去30年间在计算机领域影响巨大
* 网址为 http://www.fsf.org

## GNU 和 GNU Project

* **GNU**（GNU is Not Unix） 
* GNU Project
  * 1984 年由 **Richard M. Stallman** 发起并创建
  * 目标是编写大量兼容于 Unix 系统的自由软件
  * 是 FSF 支持的最著名的开源软件项目
    * GNU 基础工具： 程序的编辑器、编译器、调试器
    * GNU 操作系统内核：[The Hurd](http://www.gnu.org/software/hurd/hurd.html)，始于 1990 年
    * GNU 应用软件 
  * 其 “角马” 形象和 “Free as in Freedom” 的哲学理念早已在国际开源社区中广为流传
  * 官方网站：http://www.gnu.org 

## 理查德·斯托曼

* 理查德·马修·斯托曼（[Richard Matthew Stallman](http://www.stallman.org/)，简称 **RMS**，1953年3月16日至今
* 自由软件运动的精神领袖、GNU项目以及自由软件基金会（Free Software Foundation）的创立者
* 主要成就 Emacs，GNU Emacs，GNU C 编译器 及 GNU debugger
* 他所写作的GNU通用公共许可证（GNU GPL）是最广为采用的自由软件许可证，为copyleft 观念开拓出一条崭新的道路

>[自由软件之父 Richard Matthew Stallman 经典语录集锦](http://www.linuxidc.com/Linux/2016-01/128016.htm)

## 自由软件协议

* 在 GNU 项目中，通常使用 copyleft 授权
  * http://www.gnu.org/copyleft/copyleft.html
* GPL（GNU General Public License） 
  * GNU 自由软件的通用许可协议
  * 允许用户任意复制、传递、修改及再发布
  * 基于自由软件修改再次发布的软件，仍需遵守GPL
  * http://www.gnu.org/licenses/gpl.html
* LGPL（Lesser General Public License）
  * LGPL相对于GPL较为宽松，允许不公开全部源代码
  * 为基于Linux平台开发商业软件提供了更多空间
  * http://www.gnu.org/licenses/lgpl.html	

>**其他常见的开源软件协议:** BSD、MIT、Apache
>**尊重开源软件作者** -- [从FFmpeg耻辱榜看开源软件的“潜规则”](http://www.kuqin.com/opensource/20100916/88066.html)
>**使用双重授权协议**

## 开源硬件+开源软件

* [Arduino](https://www.arduino.cc/) 不仅仅是全球最流行的开源硬件，也是一个优秀的硬件开发平台，更是硬件开发的趋势
* 包含：
  * 开放的硬件电路原理图和PCB设计图 （各种型号的 [Arduino 板卡](https://www.arduino.cc/en/Main/Products)） 
  * 程序开发接口软件（[Arduino IDE](https://www.arduino.cc/en/Main/Software)）
* 简单的开发方式使得开发者更关注创意与实现，更快的完成自己的项目开发，大大节约了学习的成本，缩短了开发的周期
* 适用于电子爱好者、艺术家、设计师以及对于"互动"有兴趣的朋友
  * 专业硬件开发者使用 Arduino 开发他们的项目和产品
  * 软件开发者使用 Arduino 进入硬件、物联网等开发领域
  * 许多院校的自动化、软件、甚至艺术专业，也纷纷开设了 Arduino 的相关课程
  * 许多青少年科技小组也相继开设了 Arduino 的相关课程
* 中文社区： http://www.arduino.cn/

>### [Fritzing](http://fritzing.org) 是一款制作 PCB 布线设计的开源工具
>* Fritzing 为用户实现基于 Arduino 的设计并创造能用于生产的 PCB 布线工具，使创客和骇客真正能够实际创造出自己的设计。
>* Fritzing 的三种视图
>  * 面包板视图：允许用户在虚拟的面包板上拖拉安置虚拟的电子组件。
>  * 原理图视图：原理图的正式表达形式，是虚拟面包板上电路的对应，用户也可以根据需要进行编辑。
>  * PCB 视图：允许用户将组件放置在虚拟的印刷电路板上，然后就可以用于生产了。


## Linux 起源和发展

* 1984：GNU项目和自由软件基金会（1985）
  * 创建 UNIX 工具的开源版本
  * 创建通用公共许可证(General Public License，简称为GPL)
    * 软件授权许可实施开源理念
* 1991：Linus Torvalds
  * 创建了开源的、类似UNIX的内核，基于GPL授权协议发布
  * 移植某些 GNU工具及其在线帮助
* 今天：
  * Linux内核＋GNU工具 ＝ 完整的、开源的、类似UNIX的操作系统
    * 针对所面向的用户群而打包发行版本

>* [Linux 历史小测验](http://fossforce.com/2016/01/how-well-do-you-know-your-linux-history/)

## 什么是 Linux

* 狭义： 由 Linus 领导开发的操作系统内核
* 广义： 是一个功能强大的开源操作系统软件
  * 编制的目的是建立不受任何商品化软件版权制约的、全世界都能自由使用的UNIX兼容产品
  * 使用 Linux 作为内核的 GNU 操作系统应该更精确地被称为 **GNU/Linux 系统** 

## 林纳斯·托瓦兹

* 林纳斯·本纳第克特·托瓦兹（Linus Benedict Torvalds, 1969年12月28日至今）
* 当今世界最著名的IT人士之一，Linux 内核的发明人及该计划的合作者
* 林纳斯出生于芬兰赫尔辛基市。其父亲尼尔斯·托瓦兹（Nils Torvalds）是一名活跃的共产主义者及电台记者。托瓦兹家族属于在芬兰占 6%的少数民族芬兰瑞典人。
* 1997年至2003年 在美国加州硅谷任职于全美达公司（Transmeta Corporation）参与该公司晶片的code morph 技术研发
* 现受聘于开放源代码开发实验室（[OSDL : Open Source Development Labs](https://en.wikipedia.org/wiki/Open_Source_Development_Labs)），全力开发 Linux 内核

## 操作系统的功能

* 进程管理
* 内存管理
* 文件系统管理
* I/O 设备管理
  * 磁盘
  * 键盘、鼠标和监视器
* 网络管理
* 安全管理

>####推荐阅读
>* [操作系统――精髓与设计原理（第八版）](https://item.jd.com/12140626.html) -- [美] William，Stallings（威廉.斯托林斯） 著；陈向群，陈渝 等 译
>  * http://williamstallings.com/
>  * http://www.computersciencestudent.com/

## Linux 系统的特点

* 开放性的系统
* 多用户多任务的系统
* 具有出色的稳定性和速度性能
* 具有可靠的系统安全性
* 提供了丰富的网络功能
* 标准兼容性和可移植性
  *  可移植操作系统接口（Portable Operating System Interface，POSIX）
* 提供了良好的用户界面
  *  CLI / GUI / API

## Linux 系统的组成

* **Linux 内核**：内核（Kernel）是系统的心脏，实现操作系统的基本功能。
* **Linux Shell**：Shell是系统的用户界面，提供了用户与内核进行交互操作的一种接口。
* **Linux 应用程序**：标准的Linux系统都有一套称为应用程序的程序集，包括文本编辑器、
  编程语言、XWindow、办公套件、Internet工具、数据库等。

>#### Linux 文件系统
>* 文件系统是文件存放在磁盘等存储设备上的组织方法。
>* 通常是按照目录层次的方式进行组织。
>* 每个目录可以包括多个子目录以及文件，系统以 / 为根目录。

## Linux 内核

* Linux 内核项目
  * 主要作者：芬兰赫尔辛基大学的 Linus Torvalds
  * 1994年3月，Linux 1.0 版发布
  * Linux 内核的标志为企鹅Tux，取自芬兰的吉祥物
  * 官方网站：http://www.kernel.org 
* Linux 内核实现了操作系统的基本功能
  * 控制硬件设备，内存管理，硬件接口，基本I/O等
  * 管理文件系统，为程序分配内存和CPU时间，网络协议栈的实现等

## Linux 内核版本

* 内核版本号由3个数字组成：r.x.y
  * r：目前发布的Kernel主版本。
  * x：偶数：稳定版本；奇数：开发中版本。
  * y：错误修补的次数。
* 不同发行版可能使用不同的 Linux 内核
  * RHEL/CentOS 7 使用的内核版本是 3.10.0
  * Ubuntu 16.04 LTS 使用的内核版本是 4.4.0
  * Debian 9 使用的内核版本是 4.9.30

> 自 Linux 内核使用 Git 版本控制之后，即 Linux 内核 3.x/4.0 版本时代
> 也存在基于奇数次版本号的稳定版。例如: Linux Mint 17.1 使用的内核版本是 3.13.0。

## Linux 的发行版本（Distribution） 

* Linux内核 ＋ GNU软件 + 各种自由软件（应用程序和工具软件）
* 发行厂商可以自由选择使用某个版本的 Linux 内核
* 发行版的名称、版本由发行厂商决定
* 厂商/社区提供 **辅助安装**、**软件包管理** 等程序
* 目前已经有了几百余种发行版本，而且还在不断地增加
* 发行套件的版本号随不同发布者的而不同，与系统内核的版本号是相对独立的

> 有关更多的Linux发行版本的信息，请访问：http://www.distrowatch.com

## 常见的 Linux 发行套件

* 商业版本
  * Red Hat Enterprise Linux：http://www.redhat.com/
  * SUSE Linux Enterprise Server：https://www.suse.com/products/server/
* 社区版本
  * Debian：http://www.debian.org/
  * Ubuntu：http://www.ubuntu.com/
  * openSUSE：http://www.opensuse.org/
  * CentOS：http://www.centos.org/
  * Fedora：https://getfedora.org/
  * Gentoo：http://www.gentoo.org/
  * Arch：http://www.archlinux.org/
  * Alpine：https://alpinelinux.org/

## 常见的 Linux 发行套件 —— DEB/RPM

* 基于 DEB
  * Debian -> Ubuntu -> LinuxMint
* 基于 RPM
  * Fedara -> RHEL/CentOS
  * openSUSE

## Red Hat 发行版本

* Red Hat Linux （终止于 v9）
* Red Hat Enterprise Linux
  * 性能稳定、经过全面测试的软件
  * Red Hat 公司提供专业的支持服务
  * 对大型网络进行集中管理的工具
* Fedora
  * 更多、更新的应用程序
  * 社区支持（非红帽官方支持）

## CentOS （Community ENTerprise OS）

* CentOS 是一个开源软件贡献者和用户的社区
  * CentOS 社区对 RHEL 源代码进行重新编译
  * CentOS 社区不断与其他的同类社区合并
* CentOS Linux 是当前使用最广泛的 RHEL 兼容版本
  * CentOS Linux 的稳定性不会比 RHEL 差，唯一不足的就是缺乏技术支持，因为它是由社区发布的免费版
  * CentOS Linux 由于同时具有与 RHEL 的兼容性和企业级应用的稳定性，又允许用户自由使用，因此得到了越来越广泛的应用
  * CentOS Linux 与 RHEL 产品有着严格的版本对应关系

## Red Hat 的培训及认证

* Red Hat Certified System Administrator (RHCSA®)
* Red Hat Certified Engineer (RHCE®) 
* Red Hat Certified Architect (RHCA®)

>* https://www.redhat.com/courses/
>  * https://www.redhat.com/zh/services/training/all-courses-exams
>* http://www.redhat.com/certification/
>  * https://www.redhat.com/zh/services/all-certifications-exams

## Linux 深受喜爱的原因

* Linux 是自由软件，用户不用支付任何费用就可以获得它和它的源代码
* Linux 具有Unix的全部功能，任何使用 Unix 操作系统或想要学习 Unix 操作系统的人都可以从 Linux 中获益
* Linux不仅为用户提供了强大的操作系统功能，而且还提供了丰富的应用软件

## Linux 的应用领域

* 教育领域
  * **操作系统原理**课程的好教材
  * 卡片式电脑 —— [树莓派（Raspberry Pi）](https://www.raspberrypi.org/)
* 服务器领域
  * Internet 服务器操作系统的首选
  * 50% 以上的服务器市场占有率
  * U2L(UNIX to Linux) 计划正在广泛开展
* 云计算领域
  * 开源是云计算的灵魂
  * 云基础设施平台首选操作系统，如 [OpenStack](https://www.openstack.org/)、[Cloudstack](https://cloudstack.apache.org/)
* 嵌入式领域
  * 移动通讯终端 -- 如： Android 手机（Linux内核 + jvm + java程序）
  * 移动计算设备 -- 如： Android 平板电脑
  * 网络通讯设备 -- 如： 网络接入盒、路由器（[LEDE Project](https://lede-project.org/)）
  * 智能家电设备 -- 如： 基于 Ubuntu/Android 的网络视频播放设备 
* 多媒体与电影制作
* 桌面应用

>#### 卡片电脑
>* [friendlyarm](http://wiki.friendlyarm.com/)
>  * https://arm9.taobao.com/category-178581831.htm 
>* [pine64](https://www.pine64.org/)
>  * https://shop122470551.taobao.com/category-1205316626.htm
>* [orangepi](http://www.orangepi.cn/)
>  * https://idroid.taobao.com/ 

## UNIX/Linux 理念

* 一切即文件（包括硬件）
* 小型、目的单一的程序
* 多个程序链接在一起来执行复杂任务的能力
* 避免令人困惑的用户界面
* 以文本格式保存配置数据
* 脚本编程自动完成特定任务功能
