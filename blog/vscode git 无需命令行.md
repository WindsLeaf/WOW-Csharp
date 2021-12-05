**扫盲教程，本人能力有限，如有错误，请于评论区指出，不胜感谢，勿喷。**

[TOC]



# 扫盲

## 什么是vscode？

> Visual Studio Code是一个轻量级但功能强大的源代码编辑器，可在您的桌面上运行，并且可用于Windows，macOS和Linux。 它具有对JavaScript，TypeScript和Node.js的内置支持，并具有丰富的其他语言（例如C，C＃，Java，Python，PHP，Go）和运行时（例如.NET和Unity）扩展的生态系统。 。 通过这些入门视频，从VS Code开始您的旅程。
>
> —— 节选自vscode官网

## 什么是git

> Git 和其它版本控制系统（包括 Subversion 和近似工具）的主要差别在于 Git 对待数据的方式。 从概念上来说，其它大部分系统以文件变更列表的方式存储信息，这类系统（CVS、Subversion、Perforce、Bazaar 等等） 将它们存储的信息看作是一组基本文件和每个文件随时间逐步累积的差异 （它们通常称作 **基于差异（delta-based）** 的版本控制）。
>
> ——节选自Git官网

也就是说**vscode是一个编辑器**，即使功能强大，也依然是编辑器。**Git是版本控制软件，这个软件的特色是他储存版本的方式是去储存版本间的差异**

## Git概念简单解释

既然要玩git了，建议了解git的命令行，[Git - 获取 Git 仓库 (git-scm.com)](https://git-scm.com/book/zh/v2/Git-基础-获取-Git-仓库)，这里不对命令行做过多解释。只说一下git的某些概念

git的第一个概念是仓库，仓库里面有很多文件，仓库也记录了所有文件的版本(被提交过的)。

一个文件的生命周期有三个阶段，分别是`work dir`、`HEAD`、`Index`。三者关系是进阶的，一个文件先由`work dir`上传到`index`，再由`index`上传到`HEAD`，再上传到`HEAD`之后，就会自动生成一个版本号，**vscode里面将文件从`work dir`上传到`Index`的过程称之为暂存，将`Index`上传到`HEAD`的过程称之为提交**

![git工作流程](https://suyuesheng-biaozhun-blog-tupian.oss-cn-qingdao.aliyuncs.com/blogimg/20210510222123.png)

### 版本回退

Git里面有`work dir`、`Index`和`Head`的很大一个好处是可以方便的进行版本回退和撤销提交的操作。[git reset 和 checkout 以及HEAD COMMIT ADD详解 - sogeisetsu - 博客园 (cnblogs.com)](https://www.cnblogs.com/sogeisetsu/articles/12503911.html)

![](https://suyuesheng-biaozhun-blog-tupian.oss-cn-qingdao.aliyuncs.com/blogimg/20210510225332.png)

### 远程仓库

比较著名的远程仓库有GitHub，gitee等。远程仓库保证了可以将本地文件储存到云端，保护了文件，并且方便协作。

![](https://suyuesheng-biaozhun-blog-tupian.oss-cn-qingdao.aliyuncs.com/blogimg/20210510222743.png)

# vscode对git的操作

首先需要下载两个软件一个叫vscode、另一个叫GIT（废话）。下载链接如下👇

- [Visual Studio Code - Code Editing. Redefined](https://code.visualstudio.com/)
- [Git - Downloads (git-scm.com)](https://git-scm.com/downloads)

## 初始化一个仓库

用vscode打开一个文件夹，在vscode的命令面板（`CTRL+shift+p`）输入`git init`将会出现选项点击即可。

![](https://suyuesheng-biaozhun-blog-tupian.oss-cn-qingdao.aliyuncs.com/blogimg/20210510222910.png)

## 暂存和提交

左边dock栏，源代码管理，选定文件，右键进行暂存和提交的操作，这个比较简单，按文字提示来就是了

![](https://suyuesheng-biaozhun-blog-tupian.oss-cn-qingdao.aliyuncs.com/blogimg/20210510224051.png)

## 链接远程仓库

按下图操作，随后填git链接或者选择直接从GitHub中创建，全程傻瓜化操作，狂点下一步就完事儿了。

![](https://suyuesheng-biaozhun-blog-tupian.oss-cn-qingdao.aliyuncs.com/blogimg/20210510224454.png)

## 版本回退

两个方法，一个是在命令面板进行撤销操作。

![](https://suyuesheng-biaozhun-blog-tupian.oss-cn-qingdao.aliyuncs.com/blogimg/20210510225027.png)

第二个方法是安装插件，`Git Graph`  [Git Graph - Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=mhutchie.git-graph)，右键点击checkout进行版本回退

![](https://suyuesheng-biaozhun-blog-tupian.oss-cn-qingdao.aliyuncs.com/blogimg/20210510225252.png)

