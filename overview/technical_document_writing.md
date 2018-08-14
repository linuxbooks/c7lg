# 技术文档写作

## 技术文档的特点

* 结构清晰
* 多人协作 （版本控制系统/WIKI）
* 利于回溯 （版本控制系统）
* 程序/脚本 语法加亮显示
* 程序/脚本 可直接 复制粘贴 用于生产环境
* 提供多种格式的文档 （**.html**, .pdf, .epub, .docx/.odt）

## 使用排版工具（如：M$ Word）的劣势

* 不利于回溯
* 不利于多文档搜索
* 不利于 程序/脚本 的语法加亮显示
* 不利于直接复制内容用于生产
  * Word 会自以为是的替换许多符号
  * Word 会包含许多不可见的控制字符

>* [LaTex](http://www.latex-project.org/) -- [如何使用 LaTeX 排版论文](https://github.com/tuna/thulib-latex-talk)

## 结构化文档的格式

* [DocBook](http://docbook.org/)
* XHTML/HTML5（CSS）

* WIKI 标记语言
* 轻量级的文本标记语言

>#### 结构化数据格式
>* XML
>* JSON
>* YAML

## DocBook

* 使用**语义化标签**的 XML 文档
* 写作和发行过程
  * 使用 XML 书写图书源码
  * 使用 XSLT 读取 DocBook 的 XSL 文件将 XML 转换成 HTML
  * 生成 pdf 等格式

* 在 Linux 世界里广泛使用
  * [The Linux Documentation Project](http://www.tldp.org/)

>* [DocBook 5: The Definitive Guide](http://tdg.docbook.org/) -- By Norman Walsh , O'Reilly Media

## Wiki

* Wiki 系统 
  * 将 Wiki 标记语言 转换成 HTML 页面
  * 利于**多人协作**，提供**版本控制**
  * 如： Dokuwiki, MoinMoin, Mediawiki
* Wiki 标记语言 （[Creole](http://www.wikicreole.org/)）
* [各种 Wiki 系统（包括标记语言）的比较](http://www.wikimatrix.org/)

## 轻量级的文本标记语言

* [MarkDown](http://commonmark.org/help/) -- 使用广泛
  * 方言：[GFM](https://help.github.com/articles/github-flavored-markdown)
* [reStructuredText](http://docutils.sourceforge.net/rst.html)  -- Pythoner 的钟爱
* [AsciiDoc](http://www.methods.co.nz/asciidoc/) -- 基于文本标记语言的 DocBook 实现，基本实现了 DocBook 的语义表达
  * [AsciiDoc cheatsheet](http://powerman.name/doc/asciidoc)
  * 方言：[asciidoctor](http://asciidoctor.org)
	  * [AsciiDoc Syntax Quick Reference](http://asciidoctor.org/docs/asciidoc-syntax-quick-reference/)
* 各种标记语言格式之间的转换工具
  * http://pandoc.org/
  * 在线转换：http://pandoc.org/try/

## 技术文档的写作方式

>**像写代码一样的方式写文档**

* 使用文本标记语言书写文档内容
  * 使用**纯文本编辑器** -- 如：Nodepad++， Editplus，Vim 等
  * 使用程序员偏爱的代码编辑器及其标记语言插件 -- 如：[Atom](https://atom.io/)，[Sublime Text](https//www.sublimetext.com) 等
  * MarkDown 专用编辑器 -- 如： [MarkdownPad2](http://markdownpad.com/)、[Typora](https://typora.io/)
    * [14 Best Markdown Editors for Linux](https://itsfoss.com/best-markdown-editors-linux/)
  * AsciiDoc 专用编辑器 -- 如： [AsciiDocFX](http://www.asciidocfx.com/)
* 使用文档格式转换工具（类此与对程序语言进行编译）
  * 生成 HTML、PDF 等格式的文件
* 将文档内容纳入版本控制系统
  * 记录修改历史并提供回溯
  * 多人协作

>#### 使用文档标记语言的 图书/文档 案例
>* [Front-End Developer Handbook 2017](https://github.com/FrontendMasters/front-end-handbook-2017) -- MarkDown 
>* [readthedocs.org docs](https://github.com/rtfd/readthedocs.org/tree/master/docs) -- reStructuredText 
>* [ProGit 2nd ed](https://github.com/progit/progit2/) -- Asciidoc 

## 版本控制系统

* [Git](http://git-scm.com)
* 代码托管服务（程序员的 SNS 社区）
  * [github](https://github.com)
  * [bitbucket](https://bitbucket.org)
  * [码云@oschina](http://git.oschina.net/)
  * https://code.csdn.net/
* 图书/文档 托管服务
  * [gitbook](https://www.gitbook.com) -- https://help.gitbook.com/
  * [readthedocs](https://readthedocs.org/) -- https://docs.readthedocs.io/
  * [看云](https://www.kancloud.cn/) -- http://help.kancloud.cn/

> SNS: Social Network Service

## git 和 github

* 学习 git 参考
  * [为啥 Git 最棒](http://zh-cn.whygitisbetterthanx.com/)
  * [git 简易指南](http://rogerdudler.github.com/git-guide/index.zh.html)
  * [git-recipes](https://github.com/geeeeeeeeek/git-recipes/wiki)
  * [git 教程](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
  * [git 魔法](http://www-cs-students.stanford.edu/~blynn/gitmagic/intl/zh_cn/) -- [git](https://github.com/blynn/gitmagic)
  * [10篇写给Git初学者的最佳教程](http://www.cnblogs.com/JoannaQ/p/3302544.html) -- [Top 10 Git Tutorials for Beginners](https://www.webpagefx.com/blog/web-design/git-tutorials-beginners/)
  * [Git Book](https://git-scm.com/book/zh/v2)
* 学习 Github 参考
  * [《如何高效利用GitHub》](http://www.yangzhiping.com/tech/github.html)
  * [《Got GitHub》(蒋鑫)](http://www.worldhello.net/gotgithub/)
  * [The GitHub Hep](http://help.github.com/)
  * [《GitHub入门与实践》([日]大塚弘记)](https://item.jd.com/11733256.html)
  * [《完全学会Git GitHub Git Server的24堂课》(孙宏明)](https://item.jd.com/11974446.html)

## 将一组文档构建成网站

* 选择你偏爱的静态网站生成工具
  * [staticgen](http://www.staticgen.com/)
  * [staticsitegenerators](https://staticsitegenerators.net/)
* BLOG
  * [Pelican](http://blog.getpelican.com/)（Python）
  * [Jekyll](http://jekyllrb.com/) / [Octopress](http://octopress.org/) （Ruby）
  * [Hugo](http://gohugo.io/)（Go）
  * [**Hexo**](http://hexo.io/)（Javascript）
* BOOK
  * [**gitbook**](https://toolchain.gitbook.com/)
    * 解析器 -- 基于 Node.js 语言的 gitbook
	* 支持的文档标记语言 -- Markdown（[GFM](https://help.github.com/articles/github-flavored-markdown)）、**AsciiDoc**
	* 支持的版本控制系统 -- Git
  * [Read The Docs](http://docs.readthedocs.io/en/latest/)
    * 解析器 -- 基于 Python 语言的 [Sphinx](http://www.sphinx-doc.org)
	* 支持的文档标记语言 -- Markdown （[CommonMark](http://commonmark.org/)）、**reStructuredText**
	* 支持的版本控制系统 -- Subversion, Bazaar, Git, and Mercurial 

>#### Markdown to Slide
>**Slide** （HTML+CSS+JavaScript）
>  * [md2googleslides](https://github.com/googlesamples/md2googleslides)
>  * [slideshow](https://github.com/slideshow-s9/slideshow)



