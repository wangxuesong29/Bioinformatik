<font face="方正特雅宋_GBK">
# Git之于科学家




在第二章，我们讨论了如何组织一个生物信息学项目目录以及它是如何在项目中帮助我们保证工作的条理性。良好的组织性有利于任务的自动化，从而使生活变得更加轻松，同时完成更多的重复性工作。然而，项目时刻变化，或是同他人合作，因此管理文件的不同版本是一个我们必须面对的额外挑战。
<br>
你有可能已经在你的工作中使用版本控制系统。比如，你或许保存了命名为thesis-versl.docs、thesis-vers3_CD_edits.docx、analysis-vers6.R以及thesis-vers8_CD+GM+SW_edits.docx的文件。保存过往文件版本非常有用，因为它可以让我们在需要的时候恢复某个文件或部分。文件版本同时可以帮助我们区别来自合作人的不同副本。但是，*****************

合作时，项目的组织只会变得更加复杂。我们可以通过诸如Dropbox或者Google Drive去分享整个整个目录，但是我们时刻面临某个文件被删除或被毁的风险。同时，将整个生物信息学项目放在一个共享的目录也是不太可能的，比如几个G（甚至更多）的数据并不适合在网络上分享。云盘只适用于小文件的共享，却不可用于涵盖不断更新的代码和数据的庞大合作项目。

幸载，软件工程师们在蹚水之后也为我们架起了桥，版本控制系统（version contro system, VCS），它用于管理不同版本的共同编辑代码。我们之后使用的VCS叫Git，由Linus Torvalds编写。Linus编写Git的目的是管理Linux核心（亦由他编写），一个同时包含成千上万共同开发者工作的庞大代码库。如你所想，Git适用于项目的版本控制和共同开发。

然，Git的学习曲线在初期十分陡峭。我强烈建议你花时间在这一章去学习Git，但是Git（亦如其他章节）需要大量的时间和练习方可理解。通过本章，我将指出哪个功能更加的强大；此后你可以回顾这些内容，以便顺利地理解后续内容。我还建议读者能够对书中的代码加以联系，进而熟悉Git的命令。通过初期的痛苦，你登入最佳版本控制的殿堂。

##为何Git在生物信息学中如此重要
作为一个Git的长期拥护者，我向我的同事推荐了它并提供基础的教程。多数时候，我发现最难的部分是如何使科学家们相信Git值得融入他们的工作。或许你也在犹豫是否需要学习这一章，我想说的是，Git是绝对值得下功夫的技术。如果你已经百分百地相信了，你就可以醉心于下一节的内容了。

## Git让你保存项目的快照
通过版本控制系统，你在特定的时间点创建项目的快照。如果项目出现了差错，你可以回滚带上一个快照（叫做提交更改，commit）并恢复文件。拥有如此“神器”，对于快节奏的生物信息学工作而言，绝对是一大“福利”。

Git也可以帮助修复令人恼怒的程序错误（bugs）如软件回归（software regression），一段代码离奇地停止工作或给出错误的结果。比如，你在进行SNP的数据分析，发现14%的SNP落在一条染色体的编码区。这关系到你的项目，所以你将此摘录到你的论文中并commit。

两个月后，你已经忘记了此次分析的细节，但是需要回顾14%的分析过程。令你惊奇的是当你回溯到此段代码，数据已经变更为26%！如果你已经使用commit标记你的项目进度（如快照），你讲拥有整个项目的变更历史记载并锁定何处使结果发生了改变。

Git commit使你轻松地再生和回滚先前的分析版本，也可以轻松的查看每一个commit，如果它们被commit的话。甚至可以比较两个commit之间的差别。Git提供多版本的逐行代码对比，而非重复两个月前的工作去发现bug。

此外，Git是合理文档记录的重要部分，从而简化bug的修复过程。当你的代码生成结果，为该版本复现性而作的的全面记录是十分必要的。我的同事兼好友Mike Covington说：“想象你有一个铅笔记录的实验小本本，每次PCR试验后摘录下的最新的结果”。或许这有一点牵强，但是功能性上来讲没有什么本质区别。

## Git记录帮助你记录重要的代码变更
多数软甲在发展过程中会添加特性或修复bug。在科学计算中紧跟软件的发展十分重要，一个bug的修复意味着我们工作中一个正确的或一个错误的结果。Git记录代码的每一个变化，为了直观性，我以我遇到的一个情形加以说明（我觉得全球的实验室中都有发生）。

假设一个实验室中有一个聪明的生物信息学家，他写了一个脚本以截取低质量的序列区域。他将此分享给实验室中的同事。一传十，十传百。两个月后，这个生物信息学家发现代码中的一个bug在特定的时候会导致错误，他立刻给同事发出了修正版本并提醒同事防范潜在的错误。不幸的是，消息传达不及时或者同事们“稀里糊涂”地继续使用旧版本。

Git能够轻松解该问题并保证软件的及时更新。通过Git，跟进软件的更新并下载新版本变得相当容易。此外，诸如GitHub和Bitbucket的网络仓库服务使得分析和不同实验室的协同编码变得容易。

## Git保证人员离开后软件的有序、可获得
设想另一场景：一个博士后拥有了一个自己的实验室，她的不同软件工具和脚本散落在不同的路径，更有甚者，她丢失了全部的文档。四处散落的代码令同事抓狂；丢失的代码使之无法复现结果进而阻滞后续研究。

Git能够保证工作的连续性并保存所有的项目历史。在一个仓库中集中一整个项目使之保持条理。Git保持每一个commit的变化，因此全部项目的历史都是可以获得的。即使主要开发人员离开也不是一个问题。借助回滚的能力，项目的变更不在危险，新项目的的建立更加轻松。

## 安装Git
如果你使用的MacOS，通过Homebrew（brew install git）安装git；Linux下，使用apt-get(apt-get install git)。如果你的操作系统没有包管理工具，则可以在Git的官网下载源代码和可执行版本的Git。

## Git基础：创建仓库、追踪文件以及暂存文件和提交更改
至此，我们已经对Git有了基本的认知，并了解如何在生物信息学的工作中布置工作，那么接下来我们就来了解最最基础的Git概念，创建仓库并告知Git那些文件需要保持trace，以及暂存文件和提交更改。

## Git设置：告诉Git你是谁
因为Git旨在帮助你处理协同编辑的文件，你需要告诉它你是谁以及你的邮箱地址是什么。如下操作：
$ git config --global user.name "Sewall Wright"
$ git config --global user.email "swright@adaptivelandscape.org"
确保使用你自己的名字和邮箱。我们通过subcommands与Git互动，格式如下：git <subcommands>。Git拥有众多subcommand，但是你在日常的工作中只需一小部分。

另一个有用的Git设置是终端颜色。许多的subcommand使用终端颜色在视觉上显示变化（如红色为删除、绿色为新的更改）。设置如下：

```sh
$ git config --global color.ui true
```

## git init和git clone：创建仓库
我们首先需要初始化一个目录作为Git仓库，以开始Git之旅。一个仓库是一个接受版本控制的目录。它包含你当前的工作文件和某一时间点的项目快照。快照的Git术语是commit。使用Git的根本是创建和操作这些commit：创建、查看、共享和比较。

Git有两种主要的方式来创建仓库：初始化一个已存在的目录或clone一个存在于其他地方的仓库。无论哪种方式，其结果都是Git视其为一个仓库。Git只管理仓库中的文档及附属目录，对仓库以外的内容无能力力。

让我们以第二章创建的zmays-snps/项目为例，创建一个Git仓库。使用命令进入zmays-snps路径并使用Git subcommand初始化：

```sh
$ git init
Initialized empty Git repository in /Users/vinceb/Projects/zmays-snps/.git/
```
git init在zmays-snps中创建一个叫做.git/的隐藏目录（ls -a显示所有文档）。Git在我们未知的情况下使用.git/完成仓库的管理任务。但是，不要更改或移除该目录下的任何东西，该目录只应由Git进行操作。因而我们使用诸如git init的命令与之交互。

clone已存在的仓库是另一种仓库创建方式。你可以从任意的地方clone：从你的文件系统的某处、从你的局域网或者从互联网的某处。当下，通过仓库托管服务如GitHub和Bitbucket进行clone是非常普及的。

我们练习一下如何从GitHub中clone一个仓库。针对此例，我们将从Li's GitHub页面clone Seqtk代码。Seqtk是SEQuence ToolKit的缩写，其处理FASTQ和FASTA文件的功能非常强大。首先，访问GitHub仓库并四处看看。所有的GitHub仓库都有一个URL语法：user/repository。clone URL在页面的右侧，你可以拷贝该链接以clone该仓库。

现在，终端命令进入zmays-snps/上一级路径。路径的选择无碍；我选择user/repository目录进行clone和编译其他工具。再次路径：

```sh
$ git clone git://github.com/lh3/seqtk.git Cloning into 'seqtk'...
remote: Counting objects: 92, done.
remote: Compressing objects: 100% (47/47), done. 
remote: Total 92 (delta 56), reused 80 (delta 44) 
Receiving objects: 100% (92/92), 32.58 KiB, done. 
Resolving deltas: 100% (56/56), done.
```
seqtk代码由git init克隆岛你的本地目录，同原来GitHub仓库一样。clone能够使你获得Heng Li's发布的GitHub仓库更新内容，而你却无权直接对其仓库中的内容进行修改。

现在，如果你在终端输入cd命令进入seqtk/并输入ls命令，你将看到seqtk的源码：

```sh
$ cd seqtk
$ls
Makefile README.md khash.h kseq.h seqtk.c
```
尽管方式不同，zmays-snps/和seqtk/都是Git仓库。

## Git中跟踪文件：git add和git status第一部分

尽管你已经初始化zmays-snps/作为一个Git仓库，Git却不会自动跟踪每一个目录下文件。相反，你需要通过git add 告诉Git哪些文件需要被跟踪。而这正式Git的神奇之处，生物信息学工作中并不需要追踪所有文件，如大文件和中间结果或者我们可以轻易复现的内容。

跟踪之前，让我们使用git status来查看文件的Git状态（进入zmays-snps/路径）：




```sh
git status
# On branch master (1)
# Initial commit 
# Untracked files: (2)
#
#
#
#
nothing added to commit but untracked files present (use "git add" to track)
```
git status告诉我们：

（1）我们处于*master*分支，该分支是默认分支。分支的设定使我们同事能够在项目的不同版本中工作、切换。简单、功能强大的git分支是其如此流行的一个原因。我们暂时只在*master*分支工作，在以后的章节中会涉及其他分支。

（2）我们有一个“Untracked files”列表，其包含项目根目录下的所有的资料。因为我们还没有告知Git需要跟踪的内容，所以Git没有提交任何东西。

__git status__是最常用的__git__命令之一，我们需要牢记它。__git stauts__描述当前项目仓库的状态：做了什么更改，那些内容在下一次将被提交，和未被跟踪。本章余下的内容将大量使用__git status__命令。

让我们__git add__以告知__git__跟踪*__zmays-snps/ directory__*路径中的__*README*__和*__data/README__*路径下的文件：

```sh
$ git add README data/README
```
现在，__Git__将跟踪__*README*__和*__data/README__*路径下的文件。我们可以再次运行__git status__加以验证：

```sh
$ls
README analysis data scripts $ git status
# On branch master
#
# Initial commit
#
# Changes to be committed:
#	（use "git rm --cached <file>..." to unstage）
#
#			new file:	README 	(1)
#			new file: data/README	
#
# Untracked files:
# (use "git add <file>..." to include in what will be committed) #
# data/seqs/		(2)
```

(1)  在*“changes to be committed.”*中，注意此刻__Git__是如何将__*README*__和*__data/README__*路径下的文件作为新文件列出的。若我们此刻做出提交，__commit__命令会对__git add__命令发出时的文件版本做一个快照。

(2)  __*data/seqs/*__未被跟踪，因为我们没有告知__Git__需要这样做。合宜地,__git status__提醒我们可以使用__git add__跟踪这些文件。

##Git中的暂存文件：git add 和git status第二部分

__Git__中，被跟踪文件和文件被暂存至下次提交清单中是有差异的。这个细微的差异常常使初学者困惑。一个文件被跟踪意味着__Git__知道它的存在。一个文件不仅被跟踪，而且最后一次的更改被暂存在下一次提交的清单中(见图5-1)。

观察一个由__git add__添加跟踪的文件被更改之后的变化能够理清上述差异。更改不会自动地包含在下一次的提交中清单中，我们需使用明确地暂存它们——再次使用__gitadd__。部分疑惑在于，__git add__跟踪新文件并暂存已被跟踪文件的变化。我们通过一个列子来整理思绪。



<p>
<img src="https://cloud.githubusercontent.com/assets/14146871/26757571/74020650-48c0-11e7-949c-98961067d749.png" alt>
<em> 图5-1 分离的Git工作树(文件均在你的仓库中)，暂存区(文件包含在下一次提交的清单中)以及已提交的更改(每一时刻项目某个版本的快照)；对一个未被跟踪的文件执行git add以开始跟踪它和暂存它，而对于已经被跟踪的文件则git add将暂存保存到下次提交的清单中。
</p>







</font>












