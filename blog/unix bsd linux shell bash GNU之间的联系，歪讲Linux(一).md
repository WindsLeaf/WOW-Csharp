[TOC]

# 不客观，非权威

**这是本人的学习笔记，不代表权威。文中相关主观看法不代表主流的客观的看法。不对文章所涉及内容的权威性和正确性做任何保证。**

说实在的，我一直认为了解这些东西其实没什么卵用，**学习使用linux进行开发为什么要知道什么叫GNU？**

但还是需要了解这些，**一是为了方便自己跟别人吹牛逼，二是为了听懂别人吹的牛逼。**毕竟一帮人在那谈一些像freeBSD与mac os之间的关系和华为鸿蒙与安卓与linux与unix的关系的时候，如果咱连听都听不懂就尴尬了，所以，花时间了解一下还是必要的，虽然靠吹牛逼赚不了钱，但咱也不能让别人轻轻松松把逼装到是不是？

# 名词解释+吐槽😜（新手建议跳过本章）

下面的东西，看了就会晕，我也是因为晕，才写了这篇文章🤣

- **unix** ：Unix是20世纪70年代初出现的一个操作系统，闭源，需要付费使用。[^1]
  - **BSD** ：又被称作是伯克利软件发行版，**是unix的一个重要的分支**，它创造性地加入了vi（一个编辑软件）和csh（一款shell）[^2]
  - **POSIX标准**：  一个标准，因为unix的分支越来越多，**POSIX标准的目的是实现UNIX的标准化**[^3]，**这个标准的一个比较大的贡献就是shell脚本在大多数情况下，既可以在linux上运行，也可以在mac os上运行。[^4]**
- **GNU** ：全拼是**G**NU is **N**ot **U**nix 是一个[自由软件](https://zh.wikipedia.org/wiki/自由軟體)[集体协作](https://zh.wikipedia.org/wiki/集體協作)计划，1983年9月27日由[理查德·斯托曼](https://zh.wikipedia.org/wiki/理查德·斯托曼)在[麻省理工学院](https://zh.wikipedia.org/wiki/麻省理工學院)公开发起。它的目标是创建一套完全[自由](https://zh.wikipedia.org/wiki/自由软件)的[操作系统](https://zh.wikipedia.org/wiki/操作系统)，称为[GNU](https://zh.wikipedia.org/wiki/GNU)。理查德·斯托曼最早在net.unix-wizards[新闻组](https://zh.wikipedia.org/wiki/新闻组)上公布该消息，并附带一份《[GNU宣言](https://zh.wikipedia.org/wiki/GNU宣言)》等解释为何发起该计划的文章，其中一个理由就是要“重现当年软件界合作互助的团结精神”。[^5]
- **Linux**：有两个说法下面👇
  - **操作系统内核**：Linus发布的遵循GNU旗下“通用公共许可证”的操作系统内核[^6]。但是，**Linux内核并非GNU计划的一部分。**[^7]
  - **操作系统**：[GNU官网]([GNU操作系统和自由软件运动](https://www.gnu.org/))更喜欢称之为GNU/Linux，因为**GNU提供了bash和GCC**等操作系统所必须的东西，[Linux](https://baike.baidu.com/item/Linux)操作系统包涵了[Linux内核](https://baike.baidu.com/item/Linux内核)与其他自由软件项目中的GNU组件和软件，**甚至“linux操作系统”之中GNU计划的代码所占的比重要远远高于Linux内核**，现在所谓的各种Linux发行版其实应该叫做**一个带有Linux的GNU系统**。[^8]现在**越来越多的Linux发行版也认为自己是“GNU/Linux”**。
- **Linux发行版**：有两种说法，**一种是使用了Linux内核就叫Linux发行版，一种是只有GNU/linux才可以叫Linux发行版**[^9]，Linux发行版之间的区别就是预装软件、软件包管理、驱动、内核补丁、桌面环境的不同。
  - Linux发行版有社区版和商业版之分，前者是社区维护，后者嘛，就是公司维护咯。
  - 之所以会有**发行版的区别**，主要还是**侧重点**不一样，**目标用户**不一样，**风格**不一样，**背后的哲学思考**不一样，
    - **Ubuntu**注重的是**功能齐全，桌面华丽，预装驱动全**，基本上安装了就能用👍。
    - **debain**比较**注重开源精神，系统里面就很少有预装闭源的软件或者驱动**为了追求稳定性，软件包也不是很新
    - **Redhat**就是注重服务器系统的稳定性了，各种对kernel的补丁保证了稳定性，付费使用。
    - **centos**就是Redhat的每半年复制版（剔除了些许Redhat专有代码），继承了Redhat稳定性的特点，又由社区维护，免费用（但是**2021年之后centos8就停止维护了**，就挺震惊的🤦‍♀️）。
    - **Fedora**由红帽赞助，红帽各种新功能会先扔到Fedora上测试，算是红帽的先期测试版。
    - **Deepin**就比较牛逼了，基于debain，**桌面环境用起来比较舒服，为国人的使用习惯做了优化，预装的软件很良心，自带软件商店且软件商店丰富度尚可，自带图形化包安装器，最新版甚至可以直接安装安卓软件**，极大限度的照顾了小白用户，但就笔者使用下来的使用体验来看，照windows这种专业的图形界面操作系统还有相当长的差距。
    - **arch**系统就是两个字简洁，三个字，个性化，当然了，滚动更新还更新的特快🛴，**稳定性就差点儿事儿了**😓。[^10]
    - **还有一些很轻量化的系统**，比如安装在树莓派上的树莓派专属debain就可以装在一个8g的内存卡上使用🤷‍♂️，关键是还带桌面。**TinyCore Linux**[^11]就不到20MB，竟然还有图形化桌面环境，且kernel放在内存中运行，惊人不😉？
    - **Android**，这个比较有争议，**争议的核心是Linux发行版的定义问题**[^9]，Android使用了Linux的内核，但是Android并没有使用GNU套件，**至少Android绝对不是GNU/Linux**。[^12]
  - **不同的包管理系统** ：**采用不同的包管理系统，各发行版的维护者对系统的追求不一样**，比如准求稳定的发行版的的包仓库的软件通常是稳定版，追求新技术的发行版的包仓库的软件通常是比较新的版本，不同的包管理系统有不同的使用方法和社区用户者。
    - **什么是包管理系统**：包管理系统的作用是**方便安装、升级和自行解决依赖**，「包仓库」有助于确保代码已经在你使用的系统上进行了审核，并由软件开发者或包维护者进行管理。[^13]
    - **包管理系统的区别**：有的包管理系统是图形化界面（GUI），有的包管理系统是命令行界面（CLI），命令行界面虽然使用方式不同，**但笔者在使用体验上没有感觉到明显的不同🤷‍♂️，apt和yum都能很好的解决依赖问题，也都能方便的去安装、升级和卸载包。**据说不同的包管理系统在处理依赖的能力上是有区别的[^14]。
    - **为什么包管理系统没有统一**：**主要是历史原因。大约在同一时间建立了多个软件包管理系统，特别是.rpm和.deb。每个都有自己的拥护者，每个都足够优秀**👍[^15]，以至于没有任何一个软件包管理者具有明显的优势。发行商肯定不会完全重建他们的系统以实施其他程序包管理器。比如笔者我就比较喜欢yum，因为我单纯觉得yum的命令比较好记和简洁，apt虽然使用起来比较贴合直觉，但早些年的dpkg在安装本地的包的时候竟然不会解决依赖问题，需要用gdebi来解决🤬（当然，新版的debain可以用apt-get来安装本地包并且解决依赖了👌）
    - **主要的包管理系统使用方式的区别**：这个随便一搜就出来了，贴个随便搜的链接[Linux 包管理基础：apt、yum、dnf 和 pkg - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/28562152)
    - **遇到包仓库没有的软件怎么办**：一是自己编译源代码，比如用make命令编译，二是添加源，添加源，添加的源里面就收入了这个软件。贴一个常用的清华源（**注意：这是镜像源，理论上来说，原版源没有的软件，清华的镜像源里面也没有**）[centos | 镜像站使用帮助 | 清华大学开源软件镜像站 | Tsinghua Open Source Mirror](https://mirrors.tuna.tsinghua.edu.cn/help/centos/)
- **Android**：
  - **名词解释（绝大多数人撕逼的地方就在这里）**：安卓有很多含义
    - **AOSP** ：Android Open Source Project Android 开放源代码项目，遵循阿帕奇协议，谷歌是该项目的维护者。
    - **商标**：谷歌公司注册了，属于谷歌公司。[^16]
    - **Android**：这个安卓指的是谷歌公司发布的包含GMS服务和各种谷歌软件和新特性的操作系统，Android=AOSP+GMS+新特性。
  - **开源还是闭源**：
    - Android是运行于[Linux kernel](https://zh.wikipedia.org/wiki/Linux_kernel)之上，但并不是[GNU/Linux](https://zh.wikipedia.org/wiki/GNU/Linux)。
    - Android默认情况下并没有本机[X窗口系统](https://zh.wikipedia.org/wiki/X_Window系統)，也不支持整套标准[GNU](https://zh.wikipedia.org/wiki/GNU)库。Android为了达到商业应用，必须移除被[GNU GPL](https://zh.wikipedia.org/wiki/GNU_GPL)授权证所约束的部分。
    - **只有基础的Android操作系统（包括一些应用程序）才是开源软件**，任何厂商都不须经过Google和开放手持设备联盟的授权随意使用Android操作系统；大多数Android设备都附带着大量的专有软件，例如是[Google移动服务](https://zh.wikipedia.org/wiki/Google流動服務)，当中包括[Google Play](https://zh.wikipedia.org/wiki/Google_Play)商店、Google搜索，以及[Google Play服务](https://zh.wikipedia.org/wiki/Google_Play服務) — 那是一个提供与Google提供的服务[应用程序接口](https://zh.wikipedia.org/wiki/應用程式介面)集成的软件层。这些应用程序必须由设备制造商从Google得到许可
    - Android的硬件抽像层是能以封闭源码形式提供硬件驱动模块。HAL的目的是为了把Android framework与Linux kernel隔开，让Android不至过度依赖Linux kernel，以达成“内核独立”（kernel independent）的概念。这样安卓剥离了Linux内核以外的东西，**只需要对Android修改过的Linux内核采用GPL协议，硬件驱动可以闭源[^17]，Android其余的可以采用阿帕奇协议，保护了硬件厂商的权益和安卓GMS和安卓其他新特性**，这也就是为什么**华为可以使用ASOP却不能使用GMS和Android12。**
- **shell**： 壳程序，通俗的讲是命令解释器[^18]，**他的作用就是将用户的指令告诉操作系统的核心（kernel），然后呢kernel调用电脑的各种软硬件来达到你的指令的要求。**Windows的cmd是shell，Bash是Shell，powershell是shell，甚至windows的文件资源管理器也是shell（图形界面shell）[^19]，sh也是shell（地球上第一个比较流行的shell简称sh，是一个外国人开发出来的，简称Bourne shell😶）[^20]
  - 分为**图形界面shell和文本shell**，当然，**这个区分是我瞎编的**，如有雷同，不胜荣幸哦😁
  - **bash** ：地球上所有能叫出名字来的Linux发行版默认使用的shell，可以说bash是sh的宇宙无敌增强版[^21]，知乎上竟然有一个问题linux初学者是学csh还是tcsh还是sh还是zsh的，**我晕，初学者当然是学bash啊，虽然是大同小异，可实在是没有必要让一个初学者第一个学习的shell竟然不是bash。**其实吧，*问这个问题的同学，你甚至可以学习在linux上用poweshell，powershell是完全有能力向kernel解释你的指令的😂，当然啦，在linux上使用powershell是一件可以但没有必要的事情。*
  - **不同shell的区别？** 首先是功能上的区别，有的shell的自定义程度很高，可以自定义彩色显示，有的shell可以自动建议和自动补全命令，有的shell会匹配历史命令，这是功能上的区别。然后就是标准的区别，也就是**是否支持POSIX标准**，比如说fish的早期版本不支持这个标准，fish无法执行含有`&&`的命令，这对使用者造成了很大的困扰。

# （一）先从UNIX到GNU讲起

这部分很简单，20世纪六十年代，贝尔实验室，开发出了unix。**Unix不是开源软件，Unix源码可以与它的拥有者AT&T通过协议获得许可证**。第一个已知的软件许可证在1975年卖给了伊利诺伊大学。

Unix在学术界发展迅速，随着伯克利成为重要的活动中心，在70年代，Ken Thompson（开发unix的领导者）有一个学术休假。通过在伯克利的Unix的所有活动，一个新的Unix软件支付诞生了：伯克利软件发行版，或者叫**BSD**。[^4]

有好多公司和团体吧，就在unix的基础上二次开发，整出来了好多unix的分支，并且吧，这些个分支所使用的shell还不一样，**shell是啥呢？他的官方名称就是内容解释器或者叫壳程序，他的功能就是把用户输入的命令告诉操作系统的核心，然后这个核心再指挥硬件。**

![](https://suyuesheng-biaozhun-blog-tupian.oss-cn-qingdao.aliyuncs.com/blogimg/20210831003302.png)

**shell不一样，进行相同的操作接收的命令也就不一样**，也就是说，相当于这些shell所能听懂的人话不一样，好比shell是不同国家的人，有的shell只能听懂英文，有的shell只能听懂日文，这可咋办，这地球上unix分支这么多，甚至不同的计算机安装的分支都不一样，总不能让用户换个电脑还得重新学门语言吧，于是乎**POSIX标准**就出来了，不管你是谁，都应该能听懂同一种语言，全世界都得说中国话🤬（当然这只是戏虐）！于是乎，**同样的命令，可以在所有支持POSIX标准的shell上运行**。

然后，[理查德·斯托曼](https://zh.wikipedia.org/wiki/理查·斯托曼)，我们就暂且叫他老李头吧，老李头对unix很不爽，于是乎呢，他有了一个想法，那就是**开发一个完整的开放源代码的类unix操作系统**，来取代unix。他给自己的这个想法起了个名字叫GNU，名字的意思呢是“**GNU's Not Unix!**”，翻译成中文就是“老子不是unix，老子叫GNU！！！🙄”，他这个想法一提出来就得到了广大人民群众自发的支持，毕竟大家早就看unix不爽了，unix，啥都不是！想学习学习你的源代码竟然要花钱，老子不用你了！于是大家怀着这个要将unix干翻的想法开始工作起来了。

老李头在接下来的几年，**成立了自由软件基金会，开始雇佣人来写代码，并且发表了操作系统界的《独立宣言》——GNU宣言。还整了个GPL协议，这个协议挺niubility👍啊，遵循这个协议的软件必须开源，并且使用遵循GPL协议代码的软件也必须开源，哪怕是你商用，也得开源。**

![](https://suyuesheng-biaozhun-blog-tupian.oss-cn-qingdao.aliyuncs.com/blogimg/20210831002803.png)

这个计划吧，一开始还算顺利，向命令解释器（bash）啊，编辑器（Emacs）啊，编译器（GCC）啊啥的都进展的挺顺，可是啊，就是核心开发不出来，核心是啥呢？上面提过一嘴，核心就是能够控制硬件来执行接收到的命令的东西。这个东西可把老李头愁怀了，他是吃也吃不下，睡也睡不着，头发大把掉，胡子蹭蹭长（只是在调侃理查德的大胡子🤦‍♀️）……

# （二）天降正义，Linus！

时间来到了九十年代，一个芬兰赫尔辛基大学的大学生林纳斯，我们管他叫小林吧，这个小林不声不响，开发出来了操作系统内核linux，**并且这个Linux还采用了GPL协议**，小林按当时的话来说，就是比较帅呆了，还特谦虚幽默，你看他当年放出Linux时说的那话

> 我在做个（自由的）操作系统（就是个兴趣爱好，我不会搞得像GNU那么大那么专业），打算让它工作在386 AT平台上。它从四月就开始酝酿了，马上就快好了。我想要那些喜欢或不喜欢minix的人的意见，因为我的系统和它有点类似（同样的文件系统的物理布局——由于实际原因——还有些其他的东西）。
>
> 我现在已经移植了[bash](https://zh.wikipedia.org/wiki/Bash)(1.08)和[gcc](https://zh.wikipedia.org/wiki/GNU_Compiler_Collection)(1.40)， 而且看起来奏效了。这意味着我会在几个月内得到一些实用的东西。“……”是的——它没有任何minix代码，并且它有一个多线程的fs。它**不**可移植（使用386任务切换等），而且它可能永远不会支持除AT硬盘之外的其他东西，因为我只有这些:-(。
>
> “……”它基本上是用C语言写的，但是大多数人可能不会把我写的东西叫做C语言。它使用我能找到的386的每个可以想象的特性，因为它也是一个教我关于386的功能的项目。我前面提到过，它使用内存管理单元来进行分页（还没实现到对硬盘的功能）和分段。这个分段功能使得它真正的依赖于386（每个任务都有64Mb的代码和数据段——4Gb中最多64个任务。如果有人需要超过每个任务64Mb的限制，那将是个麻烦事）。“……”我的一些C语言文件（特别是mm.c）几乎用了和C一样多的汇编。“……”不像minix，我也碰巧喜欢中断，所以中断将在不试图隐藏背后的原因的情形下被处理。[^22]

![](https://suyuesheng-biaozhun-blog-tupian.oss-cn-qingdao.aliyuncs.com/blogimg/20210831011345.png)

老李头看这个小林是越看越喜欢，小林呢觉得GNU也不错，于是呢，GNU+linux kernel（内核）=GNU/Linux！



# （三）越来越受欢迎

从GNU/Linux第一个发行版Boot-root问世以来，GNU/Linux越来越受到欢迎，Marc Ewing成立Red Hat软件公司，成为最著名的Linux经销商之一，也证明了GNU/Linux在商业上被认可（GNU/Linux虽然开源，但不代表不可以商用，Red Hat是开源的，但是并不免费，Red Hat会为Red Hat的用户有偿提供技术服务）。

现在，整个GNU/Linux操作系统家族基于Linux内核部署在传统计算机平台（如个人计算机和服务器，以Linux发行版的形式）和各种嵌入式平台，如[路由器](https://zh.wikipedia.org/wiki/路由器)、[无线接入点](https://zh.wikipedia.org/wiki/無線接入點)、[专用小交换机](https://zh.wikipedia.org/wiki/专用小交换机)、[机顶盒](https://zh.wikipedia.org/wiki/机顶盒)、[FTA接收器](https://zh.wikipedia.org/w/index.php?title=FTA接收器&action=edit&redlink=1)、[智能电视](https://zh.wikipedia.org/wiki/智能电视机)、[数字视频录像机](https://zh.wikipedia.org/wiki/数字视频录像机)、[网络附加存储](https://zh.wikipedia.org/wiki/网络附加存储)（NAS）等。工作于[平板电脑](https://zh.wikipedia.org/wiki/平板電腦)、[智能手机](https://zh.wikipedia.org/wiki/智能手机)及[智能手表](https://zh.wikipedia.org/wiki/智能手表)的[Android](https://zh.wikipedia.org/wiki/Android)操作系统同样通过Linux内核提供的服务完成自身功能。尽管于[桌面电脑](https://zh.wikipedia.org/wiki/桌面電腦)的占用率较低，基于Linux的操作系统统治了几乎从移动设备到主机的其他全部领域。截至2017年11月，世界前500台最强的[超级计算机](https://zh.wikipedia.org/wiki/超级计算机)全部使用Linux。

GNU/Linux被打包成供个人计算机和服务器使用的Linux发行版，一些流行的主流Linux发行版，包括[Debian](https://zh.wikipedia.org/wiki/Debian)（及其派生版本[Ubuntu](https://zh.wikipedia.org/wiki/Ubuntu)、[Linux Mint](https://zh.wikipedia.org/wiki/Linux_Mint)）、[Fedora](https://zh.wikipedia.org/wiki/Fedora_(作業系統))（及其相关版本[Red Hat Enterprise Linux](https://zh.wikipedia.org/wiki/Red_Hat_Enterprise_Linux)、[CentOS](https://zh.wikipedia.org/wiki/CentOS)）和[openSUSE](https://zh.wikipedia.org/wiki/OpenSUSE)等。Linux发行版包含Linux内核和支撑内核的实用[程序](https://zh.wikipedia.org/wiki/计算机程序)和库，通常还带有大量可以满足各类需求的应用程序。[^23]

# （四）命名之争，linux还是GNU/linux？

有越来越多的人管GNU/linux叫linux操作系统，老李头团队的某些人一看不对啊，这怎么行？虽然使用了Linux内核，可也不能抹杀GNU的贡献吧？GNU起初可是要打造GNU系统的啊。

支持GNU的人认为**GNU提供了bash和GCC**等操作系统所必须的东西，[Linux](https://baike.baidu.com/item/Linux)操作系统包涵了[Linux内核](https://baike.baidu.com/item/Linux内核)与其他自由软件项目中的GNU组件和软件，**甚至“linux操作系统”之中GNU计划的代码所占的比重要远远高于Linux内核**，现在所谓的各种Linux发行版其实应该叫做**一个带有Linux的GNU系统**。[^8]

还有些人呢，就发话了，一个操作系统最重要的是啥？不就是内核吗？我们就叫Linux怎么了？（不代表笔者看法🤷‍♂️）

> “GNU/Linux”此名称是[GNU](https://zh.wikipedia.org/wiki/GNU)计划的支持者与开发者，特别是其创立者[理查德·斯托曼](https://zh.wikipedia.org/wiki/理查德·斯托曼)对于Linux操作系统的主张。由于此类操作系统使用了众多GNU程序，包含[Bash](https://zh.wikipedia.org/wiki/Bash)（[Shell程序](https://zh.wikipedia.org/wiki/Unix_shell)）、[库](https://zh.wikipedia.org/wiki/函式庫)、[编译器](https://zh.wikipedia.org/wiki/編譯器)等等作为Linux内核上的系统包，理查德·斯托曼认为应该将该操作系统称为“GNU/Linux”或“GNU+Linux”较为恰当，但现今多数人仍称其为Linux。就1997年之前的Linux来看，一间CD-ROM的供应商所提供的资料显示在他们的“Linux 发行版”中，GNU 软件所占最大的比重，大约占全部源代码的28%，且还包括一些关键的部件，如果没有这些部件，系统就无法工作，而Linux 本身占大约3%。
>
> Linux社群中的一些成员，如[埃里克·雷蒙](https://zh.wikipedia.org/wiki/埃里克·雷蒙)、[林纳斯·托瓦兹](https://zh.wikipedia.org/wiki/林纳斯·托瓦兹)等人，偏好Linux的名称，认为Linux朗朗上口，短而好记，拒绝使用“GNU/Linux”作为操作系统名称。并且认为Linux并不属于[GNU计划](https://zh.wikipedia.org/wiki/GNU計劃)的一部分，斯托曼直到1990年代中期Linux开始流行后才要求更名。有部分[Linux发行版](https://zh.wikipedia.org/wiki/Linux套件)，如[Debian](https://zh.wikipedia.org/wiki/Debian)，采用了“GNU/Linux”的称呼。但大多数商业Linux发行版依然将操作系统称为Linux。而有些人则认为“操作系统”一词指的只是系统的内核(Kernel)，其他程序都只能算是[应用软件](https://zh.wikipedia.org/wiki/应用软件)，因而，该操作系统应叫Linux，但Linux系统包是在Linux内核的基础上加入各种GNU软件包集合而成的。[^24]

反正吧，这事儿现在也没个准确的说法，我觉得吧，人GNU是做了很大贡献的，这个肯定都承认，可是挡不住Linux这个叫法朗朗上口写起来还省墨水啊，总之，现在（2021年8月31日）各种官方还没有个统一的说法，叫啥名字都无伤大雅，不管什么名字，都掩盖不了GNU和linux kernel的成功，也掩盖不了Linux操作系统对这个世界（尤其是开源世界）的贡献。

以上，就是Linux从无到有的历史了，通过这些历史，我们将不再对unix，GNU，Linux，Shell和bash等概念感到一筹莫展了，这就足够了。

现在，可以回到文章开头，去阅读我建议你跳过的名词解释＋吐槽部分了。

ヾ(￣▽￣)Bye~Bye~

# 参考资料

[^1]:[百度百科词条“unix”：AT&T公司意识到了UNIX的商业价值，不再将UNIX源码授权给学术机构，并对之前的UNIX及其变种声明了版权权利](https://baike.baidu.com/item/unix/219943?fr=aladdin)



[^2]:[Linux与Unix区别在哪里 | 《Linux就该这么学》 (linuxprobe.com)](https://www.linuxprobe.com/linux-or-unix.html)



[^3]:[posix是什么都不知道，还好意思说你懂Linux？ - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/392588996)



[^4]:[Linux与Unix区别在哪里 | 《Linux就该这么学》 (linuxprobe.com)](https://www.linuxprobe.com/linux-or-unix.html)



[^5]:[GNU计划 - 维基百科，自由的百科全书 (wikipedia.org)](https://zh.wikipedia.org/wiki/GNU計劃)



[^6]:[Linux内核 - 维基百科，自由的百科全书 (wikipedia.org)](https://zh.wikipedia.org/wiki/Linux内核#塔能鮑姆-林納斯辯論)



[^7]:[GNU计划 - 维基百科，自由的百科全书 (wikipedia.org)](https://zh.wikipedia.org/wiki/GNU計劃)



[^8]:[Linux 和 GNU - GNU 工程 - 自由软件基金会](http://www.gnu.org/gnu/linux-and-gnu.zh-cn.html)



[^9]: 可以把Android说成是Linux发行版吗？ - SegFault的回答 - 知乎 https://www.zhihu.com/question/383947288/answer/1361731747



[^10]: [Linux 各大发行版有什么特色？ - 知乎 (zhihu.com)](https://www.zhihu.com/question/24261540/answer/80418621)



[^11]: [Tiny Core | linux发行版 (linux265.com)](https://linux265.com/distro/58.html)



[^12]: 可以把Android说成是Linux发行版吗？ - AidenLeong的回答 - 知乎 https://www.zhihu.com/question/383947288/answer/1119467476



[^13]: [Linux软件包管理基本操作入门 | 《Linux就该这么学》 (linuxprobe.com)](https://www.linuxprobe.com/linux-basic-manage.html)



[^14]: [包管理器有什么区别？ (qastack.cn)](https://qastack.cn/ubuntu/76/whats-the-difference-between-package-managers)



[^15]: [为什么没有真正的Linux统一软件包管理器？ (qastack.cn)](https://qastack.cn/unix/23675/why-isnt-there-a-truly-unified-package-manager-for-linux)



[^16]: AOSP (Android Open-Source Project) 跟 Android 是何关系？ - yaui的回答 - 知乎 https://www.zhihu.com/question/21448269/answer/1888531716



[^17]: [Android - 维基百科，自由的百科全书 (wikipedia.org)](https://zh.wikipedia.org/wiki/Android)



[^18]:[鸟哥私房菜 - 第十章、认识与学习BASH (vbird.org)](https://linux.vbird.org/linux_basic/centos7/0320bash.php#bash_what)



[^19]:[shell（计算机壳层）_百度百科 (baidu.com)](https://baike.baidu.com/item/shell/99702)



[^20]:[鸟哥私房菜 - 第十章、认识与学习BASH (vbird.org)](https://linux.vbird.org/linux_basic/centos7/0320bash.php#bash_shells)



[^21]:[Linux SHELL中sh和bash的区别 - 御用闲人 - 博客园 (cnblogs.com)](https://www.cnblogs.com/yyxianren/p/10789968.html)



[^22]:[Linux内核 - 维基百科，自由的百科全书 (wikipedia.org)](https://zh.wikipedia.org/wiki/Linux内核#历史)



[^23]:[Linux - 维基百科，自由的百科全书 (wikipedia.org)](https://zh.wikipedia.org/wiki/Linux)

